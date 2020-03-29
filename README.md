# computer-network-note
计算机网络基础笔记
## 应用层
- HTTP2
- HTTP
  1. [HTTP协议基础解析](https://github.com/orochiZhang/computer-network-note/blob/master/Applicationlayer/HTTP_data_structure.md)
  2. [HTTP的请求方法和幂等性](https://github.com/orochiZhang/computer-network-note/blob/master/Applicationlayer/HTTP_Method_Idempotent.md)

- DHCP
- RIP
- DNS
- SNMP
- FTP
- TFTP

应用 | 应用层协议 | 运输层协议
---|---|---
Web应用     | HTTP| TCP
IP地址配置  | DHCP| UDP
路由选择协议| RIP | UDP
名字转换    | DNS | UDP
网络管理    | SNMP| UDP
文件传输    | FTP | TCP
文件传输    | TFTP| UDP
电子邮件    | SMTP| TCP

## Socket
- Socket的五种IO模型

## 传输层
- [TCP与UDP](https://github.com/orochiZhang/computer-network-note/blob/master/Transportlayer/TCP_and_UDP.md)
- [TCP](https://github.com/orochiZhang/computer-network-note/blob/master/Transportlayer/TCP.md)
- UDP

## 网络层
- IP
- [IP地址分类，子网划分，CIDR构造超网](https://github.com/orochiZhang/computer-network-note/blob/master/Networklayer/IP_address.md)
- ARP
- [ICMP/IGMP](https://github.com/orochiZhang/computer-network-note/blob/master/Networklayer/ICMP_and_IGMP.md)

### IGP
IGP（Interior Gateway Protocol,内部网关协议）是在一个自治网络内网关（主机和路由器）间交换路由信息的协议。路由信息能用于网间协议（IP）或者其它网络协议来说明路由传送是如何进行的。Internet网被分成多个域或多个自治系统。一个域（domain）是一组主机和使用相同路由选择协议的路由器集合，并由单一机构管理。IGP协议包括RIP、OSPF、IS-IS、IGRP、EIGRP。
### EGP
外部网关协议（英语：Exterior Gateway Protocol，缩写EGP）是一个现已过时的互联网路由协议，最初于1982年由BBN科技公司的Eric C. Rosen及David L. Mills提出。其最早在RFC 827中描述，并于1984年在RFC 904中被正式规范。EGP是一种简单的（网络）可达性协议，其与现代的距离向量路由协议和路径-矢量协议不同，它仅限适用于树状拓扑的网络。   
在互联网发展的早期，自治系统之间的互连使用的是一种称为“EGP版本3”的外部网关协议。EGP3不应与一般所说的各种EGP协议相混淆。现今，边界网关协议（BGP）是互联网路由的目前公认标准，其基本已取代了局限较大的EGP3协议。
- [外部网关协议BGP](https://github.com/orochiZhang/computer-network-note/blob/master/Networklayer/BGP.md)
- [内部网关协议RIP/OSPF](https://github.com/orochiZhang/computer-network-note/blob/master/Networklayer/RIP_and_OSPF.md)

## 数据链路层/计算机网络硬件
- [路由器与交换机](https://github.com/orochiZhang/computer-network-note/blob/master/DataLinkLayer/Router_and_Switch.md)

