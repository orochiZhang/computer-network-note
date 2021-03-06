转载自[百度知道](https://zhidao.baidu.com/question/34178430.html)

RIP协议是距离矢量路由选择协议，它选择路由的度量标准（metric)是跳数，最大跳数是15跳，如果大于15跳，它就会丢弃数据包。 

OSPF协议是链路状态路由选择协议，它选择路由的度量标准是带宽，延迟。 

### RIP的局限性在大型网络中使用所产生的问题

1. RIP的15跳限制，超过15跳的路由被认为不可达
2. RIP不能支持可变长子网掩码(VLSM)，导致IP地址分配的低效率
3. 周期性广播整个路由表，在低速链路及广域网云中应用将产生很大问题
4. 收敛速度慢于OSPF，在大型网络中收敛时间需要几分钟
5. RIP没有网络延迟和链路开销的概念，路由选路基于跳数。拥有较少跳数的路由总是被选为最佳路由即使较长的路径有低的延迟和开销
6. RIP没有区域的概念，不能在任意比特位进行路由汇总
    
一些增强的功能被引入RIP的新版本RIPv2中，RIPv2支持VLSM，认证以及组播更新。但RIPv2的跳数限制以及慢收敛使它仍然不适用于大型网络

### 相比RIP而言，OSPF更适合用于大型网络

1. 没有跳数的限制
2. 支持可变长子网掩码(VLSM)
3. 使用组播发送链路状态更新，在链路状态变化时使用触发更新，提高了带宽的利用率
4. 收敛速度快
5. 具有认证功能

### OSPF协议主要优点

1. OSPF是真正的LOOP-FREE（无路由自环）路由协议。源自其算法本身的优点。（链路状态及最短路径树算法）
2. OSPF收敛速度快：能够在最短的时间内将路由变化传递到整个自治系统。
3. 提出区域（area）划分的概念，将自治系统划分为不同区域后，通过区域之间的对路由信息的摘要，大大减少了需传递的路由信息数量。也使得路由信息不会随网络规模的扩大而急剧膨胀。
4. 将协议自身的开销控制到最小。见下：
    1. 用于发现和维护邻居关系的是定期发送的是不含路由信息的hello报文，非常短小。包含路由信息的报文时是触发更新的机制。（有路由变化时才会发送）。但为了增强协议的健壮性，每1800秒全部重发一次。
    2. 在广播网络中，使用组播地址（而非广播）发送报文，减少对其它不运行ospf 的网络设备的干扰。
    3. 在各类可以多址访问的网络中（广播，NBMA），通过选举DR，使同网段的路由器之间的路由交换（同步）次数由 O（N*N）次减少为 O （N）次。
    4. 提出STUB区域的概念，使得STUB区域内不再传播引入的ASE路由。
    5. 在ABR（区域边界路由器）上支持路由聚合，进一步减少区域间的路由信息传递。
    6. 在点到点接口类型中，通过配置按需播号属性（OSPF over On Demand Circuits），使得ospf不再定时发送hello报文及定期更新路由信息。只在网络拓扑真正变化时才发送更新信息。

5. 通过严格划分路由的级别（共分四极），提供更可信的路由选择。
6. 良好的安全性，ospf支持基于接口的明文及md5 验证。
7. OSPF适应各种规模的网络，最多可达数千台。

### OSPF的缺点

1. 配置相对复杂。由于网络区域划分和网络属性的复杂性，需要网络分析员有较高的网络知识水平才能配置和管理OSPF网络。

2. 路由负载均衡能力较弱。OSPF虽然能根据接口的速率、连接可靠性等信息，自动生成接口路由优先级，但通往同一目的的不同优先级路由，OSPF只选择优先级较高的转发，不同优先级的路由，不能实现负载分担。只有相同优先级的，才能达到负载均衡的目的，不象EIGRP那样可以根据优先级不同，自动匹配流量。


### 发送方式不同
RIP协议是装在UDP报文，而OSPF是直接通过IP数据报发送。    
OSPF比RIP更晚出现，OSPF的设计考虑到了四层UDP的不稳定性。所以就将OSPF报文封装进IP，这么做的好处就是基于三层，不再依靠四层UDP，错误率变低和识别转发能力的加强。
