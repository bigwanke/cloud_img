---
title: 虚拟机没有ip
date: 2020-10-01 19:30:04
tags: [CentOS7,虚拟机]
categories: 错误记录
---

由于直接使用Vmware操作虚拟机不是很方便，想通过Xshell连接虚拟机,但使用ip addr查询虚拟机ip，发现ens33没有inet属性

<!--more-->

![image-20220112123754724](C:/Users/wanke/AppData/Roaming/Typora/typora-user-images/image-20220112123754724.png)

使用命令查看网卡配置

```shell
vi /etc/sysconfig/network-scripts/ifcfg-ens33
```

从配置清单中可以发现 CentOS 7 默认是不启动网卡的（ONBOOT=no），把这一项改为YES，保存后退出。

![image-20220112124220293](C:/Users/wanke/AppData/Roaming/Typora/typora-user-images/image-20220112124220293.png)

然后重启网络服务

```shell
sudo service network restart
```

![image-20220112124550852](C:/Users/wanke/AppData/Roaming/Typora/typora-user-images/image-20220112124550852.png)

再次查询ip地址，可已发现虚拟机的inte属性显示ip

![image-20220112124619164](C:/Users/wanke/AppData/Roaming/Typora/typora-user-images/image-20220112124619164.png)

