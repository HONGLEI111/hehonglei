---
title: 防火墙
date: 2024-09-12 16:15:46
cover: https://img.hehonglei.cn/img/0001.avif
tags:
  - Linux
categories: 
  - 文档
---
一、防火墙相关命令

　　1、d查看防火墙状态 ：
```systemctl status firewalld.service```

　　　　注：active是绿的running表示防火墙开启

　　2、关闭防火墙 ：
```systemctl stop firewalld.service```

　　3、开机禁用防火墙自启命令 ：```systemctl disable firewalld.service```

　　4、启动防火墙 ：```systemctl start firewalld.service```

　　5、防火墙随系统开启启动 ： ```systemctl enable firewalld.service```

　　6、重启防火墙 ： ```firewall-cmd --reload```

二、端口开放相关命令

　　1、查询已经开放的端口 ：```firewall-cmd --list-port```

　　2、查询某个端口是否开放 ：```firewall-cmd --query-port=80/tcp```

　　3、开启端口 ：```firewall-cmd --zone=public --add-port=80/tcp --permanent```

　　　　注：可以是一个端口范围，如1000-2000/tcp

　　4、移除端口 ：```firewall-cmd --zone=public --remove-port=80/tcp --permanent```

　　5、命令含义：

　　　　--zone #作用域

　　　　--add-port=80/tcp #添加端口，格式为：端口/通讯协议

　　　　--remove-port=80/tcp #移除端口，格式为：端口/通讯协议

　　　　--permanent #永久生效，没有此参数重启后失效

原文链接：https://blog.csdn.net/qq_26347283/article/details/104759414

