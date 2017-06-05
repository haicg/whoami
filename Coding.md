# 一个程序员的成长历程

## 网络篇
### 路由表相关知识
1. 什么是路由表？
本质上就是一个存储在路由器或计算机上的网络路径指向表（或者类数据库），主要记录周边网络拓扑信息，同时保存着指向特定网络地址的传输路径。其主要功能就是为了实现路由协议中的静态路由选择。

2. 路由表的基本样式
在Linux系统下使用route命令就可以查看路由表。
```
route -n
```
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.31.1    0.0.0.0         UG    100    0        0 enp5s0
0.0.0.0         192.168.50.1    0.0.0.0         UG    600    0        0 wlp4s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp5s0
192.168.31.0    0.0.0.0         255.255.255.0   U     100    0        0 enp5s0
192.168.50.0    0.0.0.0         255.255.255.0   U     600    0        0 wlp4s0
```
上面是一张路由表， 分别有Destination、Gateway、Genmask、Flags、 Metric、 Ref、Use和Iface。
  1. Destination 表示目的主机地址或者目的网络域。
  1. Gateway 网关地址, 其中 * 表示目标是本主机所属的网络，不需要路由
  1. Genmask 子网掩码
  1. Flags 标志
      - U	Up: 路由处于活动状态。
      - H	Host: 路由目标是单个主机。
      - G	Gateway: 所有发到目的地的网络传到这一远程系统上， 并由它决定最后发到哪里。
      - S	Static: 这个路由是手工配置的，不是由系统自动生成的。
      - C	Clone: 生成一个新的路由， 通过这个路由我们可以连接上这些机子。 这种类型的路由通常用于本地网络。
      - W	WasCloned: 指明一个路由――它是基于本地区域网络 (克隆) 路由自动配置的。
      - L	Link: 路由涉及到了以太网硬件。
  1. Metric 路由距离(路由跳数)，到达指定网络所需的中转数（linux 内核中没有使用)
  1. Ref	路由项引用次数（linux 内核中没有使用）
  1. Use	此路由项被路由软件查找的次数
  1. Iface	该路由表项对应的输出接口


[32.2. 网关和路由](https://www.freebsd.org/doc/zh_CN/books/handbook/network-routing.html)
[linux 路由表 的一些相关资料](http://www.cnblogs.com/gunl/archive/2010/09/14/1826234.html)
