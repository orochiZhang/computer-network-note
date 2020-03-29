转载自[百度知道-真正的BGP是什么——电信员工解释BGP含义](https://zhidao.baidu.com/question/743946845824519732.html)

中国网通与 中国电信都具有AS号（自治系统号），全国各大网络运营商多数都是通过BGP协议与自身的AS号来互联的。使用此方案来实现双线路需要在CNNIC（中国 互联网信息中心）申请IDC自己的IP地址段和AS号，然后通过BGP协议将此段IP地址广播到网通、电信等其它的网络运营商，使用BGP协议互联后网通 与电信的所有骨干路由设备将会判断到IDC机房IP段的最佳路由，以保证网通、电信用户的高速访问。

BGP(Border GatewayProtocol)是一种在自治系统之间动态交换路由信息的路由协议。一个自治系统的经典定义是在一个管理机构控制之下的一组路由器，它使用IGP和普通度量值向其他自治系统转发报文。

在BGP中使用自治系统这个术语是为了强调这样一个事实：一个自治系统的管理对于其他自治系统而言是提供一个统一的内部选路计划，它为那些通过它可以到达的网络提供了一个一致的描述。

边界网关协议是不同自治系统路由器之间进行通信的外部网关协议，作为EGP替代品。BGP系统之间交换网络的可达到信息。这些信息包括数 据到达这些网络所必须经过的自治系统AS中的所有路径，通过这些信息构造自治系统链接图，然后根据连接图删除选路环，制定选路策略。

### 使用BGP双线方案有以下优点
1. 服务器只需要设置一个IP地址，最佳访问路由是由网络上的骨干路由器根据路由跳数与其它技术指标来确定的，不会对占用服务器的任何系统资源。服务器的上行路由与下行路由都能选择最优的路径，所以能真正实现高速的单IP双线访问。
2. 由于BGP协议本身具有冗余备份、消除环路的特点，所以当IDC服务商有多条BGP互联线路时可以实现路由的相互备份，在一条线路出现故障时路由会自动切换到其它线路。
3. 使用BGP协议还可以使网络具有很强的扩展性可以将IDC网络与其他运营商互联，轻松实现单IP多线路，做到所有互联运营商的用户访问都很快。这个是双IP双线无法比拟的。

虽然BGP方案是最好的解决方案但由于此方案需要IDC提供商的设备投入与带宽投入方面较大并且技术上较为复杂，所以目前国内采用此方案仅限于实力较强的专业IDC服务商。

综上所述，以上各种双线实现的方式各有优缺点，双IP双线成本较低，但网络不够稳定并且占用大量的服务器资源，普通单IP双线路只是实现了部 分双线路的效果所以访问速度不佳，CDN方式对静态网页效果很好但对交互性很强的网页效果不太理想，BGP单IP双线路解决了以上所有的问题是最好的实现方式但国内采用此种方案的IDC服务商较少，如果能将BGP单IP双线与CDN加速结合起来将会是最优的解决方案。目前全国已有不少合用BGP技术方案的数据中心，但大多为特殊客户提供服务，很少有针对普通用户和IDC商的机房。

### BGP双线的实现方式
BGP双线的实现方式跟早期的双网卡双线相比最大的特色就是服务器只需要一个网卡，因此在客户的服务器上不存在任何需要改动的地方，不过 运营商就需要购置一台较为昂贵的BGP路由器，因此这种双线技术也称为“全路由双线”。

同理，BGP多线也可以通过这样的结构来实现，也就是接入的ISP线路再多一条或再多几条。

### BGP双线的真真假假

另外，BGP双线要有自己的IP段、自治域。这个怎么弄？   
跟CNNIC申请。但是，要有自己线路的运营商才能申请，这个绝对不是随便一个IDC公司就能办到的，能够做到这一点的公司，其实力已经非常雄厚，国内达得到这个级别的也基本可以数出来，要是一个公司你连名字都没听过，看看他们的公司规模也就一个普通中小企业，你相信这样的公司能够具有申请资格？

**结论**：所以，一句话说穿，国内号称BGP双线的公司大部分都是不符合上述条件的，当然，有些如果是代理商，那还得看他代理的是谁的 BGP双线。由于各方面条件的限制，我们在这里无法为大家列举国内所有的真正BGP双线运营商，但是有一点可以告诉广大读者，真正的BGP双线多线在国内是比较有限的；当然，从大局上说，我们期待更多的运营商采用这种技术，给大家带来更多实际的好处，而不是纯粹为了宣传造势。

除了机房的路由器交换机都要使用带BGP协议的以外，各运营商也必须使用带BGP的路由器和交换机，所以真正的BGP机房成本可想而知，而且BGP运维技术也需要相当好的人才，所以“BGP”并非随口就来，门槛也不低，北京地区内真正的BGP机房也只限于寥寥7家。

有朋友要问了，BGP那么高的成本究竟能不能实现与对它投入相等的价值呢？答案当然是肯定的，要不然BGP机房早就在市场经济中流产了，总结起来优势主要有两点：

**1、消除南北访问障碍**

由于BGP可以将网通、电信两大电信运营商的线路“合并”就使得中国南北无障碍通讯成为可能，落实到接入层就使得“网通、电信”这种名词消失，更有实际意义的是一个网站资源无限制的全国无障碍使用，不像以前要想实现异地无障碍访问还要在异地做VPN或者异地加速站，北京以外的机房一般价格都低但是也是要成本的，如果一个企业有10台服务器10M独享带宽那原来的成本就是每年6.5万+3.2万=9.7万，现在实现了BGP成本为7.5万，每年下来光托管服务器方面就省了2万，还有人力、外派、办事处等等费用更是省了又省。

**2、高速互联互通**

由上提要也不难推理出高速互联的意义，原来的线路访问另一线路往往要绕很多层路由，但是实现BGP以后就像进入了高速公路，随之而来的就是速 度的提高，说是提高不如说是“还原”，还原了原来应有的互联速度。原来的带宽利用率一般都在40%左右，实现BGP后能达到80%以上所以从这点上原来做10M独享的现在用5M就可以满足要求了。这样又节省了一部分成本。