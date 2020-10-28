---
layout: post
title: 校内赛教程二：使用Clion优雅地全程同步和远程调试
categories: [vision, campus-competition]

---

# 校内赛教程二：使用Clion优雅地全程同步和远程调试

> 机械是血肉，电控是大脑，视觉是灵魂。

---

如果你可以在一个系统上用clion写程序，并使用另一个系统的内核来编译完成代码运行，是不是一件非常省事而且高效地事情呢？Clion可以帮助你完成这一点。我们可以在主机上写代码，并把虚拟机作为服务器完成代码的编写和调试，并且代码的同步是完全自动完成的。

## 一、虚拟机配置

首先，你的Ubuntu系统必须支持SSH访问，所以你需要安装opensshserver。当然也有很多其他方法，你可以自己尝试。

在Ubuntu中打开终端，输入如下命令：

```bash
sudo apt install -y openssh-server
```

安装完成后，输入如下命令查看是否安装成功

```bash
ps -ef | grep sshd
```

如何出现类似于下图所示内容表明ssh启动成功：

![]()

安装完成后如果没有启动则输入一下命令（一般不需要）：

```bash
sudo /etc/init.d/ssh resart
sudo /etc/init.d/ssh status
sudo /etc/init.d/ssh start/stop
```

然后查看虚拟机的ip地址，请确保虚拟机连接到网络，并处于桥接模式。记录下inet地址。

```bash
ipconfig -a
```

<img src="https://exp-picture.cdn.bcebos.com/f59dbe39131fceec759b8cc179c4ec9958430b9b.jpg?x-bce-process=image%2Fresize%2Cm_lfit%2Cw_500%2Climit_1" alt="ifconfig" style="zoom:100%;" />

如果没有这个命令，那么先安装对应的软件包：

```
sudo apt install net-tools
```



## 二、配置Clion

打开clion，点击Preference->Build, Execution, Deployment->Toolchains->+->Remote Host，如下图

![]()

然后如图配置，点击Credentials右侧的⚙️打开，输入刚刚得到的虚拟机ip地址，虚拟机用户名和密码，完成后点击OK。

![]()

点击Preference->Build, Execution, Deployment->Cmake->Toolchain，选择刚刚设置过的toolchain即可，如图。

![]()

然后点击项目就可以发现clion完成了自动编译和上传，大功告成。

![]()



----

作者：黄弘骏，github主页：[传送门](https://github.com/Harry-hhj)。