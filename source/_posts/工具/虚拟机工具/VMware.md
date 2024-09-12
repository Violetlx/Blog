---
title: VMware
tags:
  - 工具
  - SpringCloud
categories:
  - 工具
  - 虚拟机工具
description: VMware下载安装
top_img: 'https://img.onlinedown.net/download/202011/130602-5faa1fba690d4.jpg'
cover: 'https://img.onlinedown.net/download/202011/130602-5faa1fba690d4.jpg'
date: '2024-09-12 11:20:2'
abbrlink: 545a6120
---

![VMware虚拟机](https://www.abackup.com/easybackup-tutorials/images/backup-vmware/vmware-workstation.png)

# 什么是虚拟机

虚拟机是指软件模拟的具有完整硬件系统功能的，运行在一个完全隔离环境中的完整计算系统，在实体计算机中能够完成的工作，在虚拟机中都能够实现。



------

# VMware 简介

> 简而言之，[**VMware**](https://www.vmware.com/)（链接位于 **ibm.com** 外部）主要用于开发虚拟化软件。
>
> 虚拟化软件会在计算机硬件上创建一个抽象层，从而能够将单台计算机的硬件要素（处理器、内存、存储等）分成多个虚拟计算机（通常称为虚拟机 ( **VM** )）。 每个虚拟机都运行自己的操作系统 ( **OS** )，其行为就像一台独立的计算机，而实际上它只是在一部分底层计算机硬件上运行。



## Ⅰ大概介绍

**VMware** 虚拟机软件是一个虚拟 **PC** 软件，它可以让你在一台电脑上运行一个或多个操作系统。

## Ⅱ 详细介绍

**VMware**  是一款功能强大的桌面虚拟计算机软件，提供用户可在单一的桌面上同时运行不同的操作系统，和进行开发、测试 、部署新的应用程序的最佳解决方案。**VMware** 可在一部实体机器上模拟完整的网络环境，以及可便于携带的虚拟机器，其更好的灵活性与先进的技术胜过了市面上其他的虚拟计算机软件。

------

# VMware 下载



## Ⅰ 官网地址

[下载 VMware Workstation Pro | CN](https://www.vmware.com/cn/products/workstation-pro/workstation-pro-evaluation.html)

## Ⅱ 网盘下载

打开浏览器搜索 **VMware** 下载，然后打开帖子，复制网盘下载。

或者打开 [`B 站`](https://www.bilibili.com/) ，进行搜索。



------



# VMware 安装

![VM安装](/images/tools/vm/a/v1.png)

**VMware** 安装，点击下一步

![VM安装](/images/tools/vm/a/v2.png)

接受协议，下一步

![VM安装](/images/tools/vm/a/v3.png)

自定义 **VMware** 安装位置，下一步

![VM安装](/images/tools/vm/a/v4.png)

勾选快捷方式，下一步

![VM安装](/images/tools/vm/a/v5.png)

安装 **VMware** 虚拟机，点击完成即可。



------

# VMware 新建虚拟机



**① 创建新的虚拟机**

![VM安装](/images/tools/vm/a/v6.png)

**② 选择典型或自定义**

![VM安装](/images/tools/vm/a/v7.png)

**③ 安装系统驱动**

![VM安装](/images/tools/vm/a/v8.png)

**④ 下载 Linux 镜像**

网易开源镜像站:http://mirrors.163.com/
阿里云官方镜像站:[http://mirrors.aliyun.com](http://mirrors.aliyun.com/)

可选 **Centos** 或 **Unbtor**

<div style="display: flex; 
            justify-content: center; 
            gap: 10px; 
            padding: 10px; 
            background-color: #fff; 
            border-radius: 10px; 
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2); 
            text-align: center;">
    <img src="https://imcn.me/wp-content/uploads/2014/07/centos-logo.jpg" alt="Image 1" style="width: 60%; border-radius: 10px;">
    <img src="https://p1.ssl.qhimg.com/t01244e5eda16b4451f.png" alt="Image 2" style="width: 45%; border-radius: 10px;">
</div>
**⑤ 配置信息**

![VM安装](/images/tools/vm/a/v9.png)

**⑥ 自定义名称和路径**

![VM安装](/images/tools/vm/a/v10.png)

**⑦ 设置磁盘**

![VM安装](/images/tools/vm/a/v11.png)

**⑧ 配置硬件**

![VM安装](/images/tools/vm/a/v12.png)

**⑨ 点击完成**

![VM安装](/images/tools/vm/a/v13.png)

即可完成创建：

![VM安装](/images/tools/vm/a/v14.png)



------

# 安装 Centos7

接下来，我们启动刚刚创建的虚拟机，开始安装 `Centos7` 系统：

![VM安装](/images/tools/vm/a/v14.png)

启动后需要选择安装菜单，将鼠标移入黑窗口中后，将无法再使用鼠标，需要按上下键选择菜单。选中 **Install Centos 7** 后按下回车：

![VM安装](/images/tools/vm/a/v17.png)

然后会提示我们按下 **enter** 键继续：

![VM安装](/images/tools/vm/a/v18.png)

过一会儿后，会进入语言选择菜单，这里可以使用鼠标选择。选择中文-简体中文，然后继续：

![VM安装](/images/tools/vm/a/v19.png)

接下来，会进入安装配置页面：

![VM安装](/images/tools/vm/a/v20.png)

鼠标向下滚动后，找到系统安装位置配置，点击：

![VM安装](/images/tools/vm/a/v21.png)

选择刚刚添加的磁盘，并点击完成：

![VM安装](/images/tools/vm/a/v22.png)

然后回到配置页面，这次点击《网络和主机名》：

![VM安装](/images/tools/vm/a/v23.png)

在网络页面做下面的几件事情：

1. 修改主机名为自己喜欢的主机名，不要出现中文和特殊字符，建议用localhost
2. 点击应用
3. 将网络连接打开
4. 点击配置，设置详细网络信息

![VM安装](/images/tools/vm/a/v24.png)

本机网络详细信息：

![VM安装](/images/tools/vm/a/v25.png)

点击配置按钮后，我们需要把网卡地址改为静态IP，这样可以避免每次启动虚拟机IP都变化。所有配置照搬你自己截图的网络信息填写：

![VM安装](/images/tools/vm/a/v26.png)

最后，点击完成按钮：

![VM安装](/images/tools/vm/a/v27.png)

回到配置界面后，点击`开始安装`：

![VM安装](/images/tools/vm/a/v28.png)

接下来需要设置root密码：

![VM安装](/images/tools/vm/a/v29.png)

填写你要使用的root密码，然后点击完成：

![VM安装](/images/tools/vm/a/v30.png)

接下来，耐心等待安装即可。

![VM安装](/images/tools/vm/a/v31.png)

等待安装完成后，点击**重启**：

![VM安装](/images/tools/vm/a/v32.png)

输入密码即可登录：

![VM技巧](/images/tools/vm/a/v15.png)

![VM技巧](/images/tools/vm/a/v16.png)

打开中端输入密码切换 root 用户：

![VM安装](/images/tools/vm/a/v33.png)

此时你要输入密码，不过需要注意的是密码是**隐藏**的，输入了也看不见。所以放心输入，完成后回车即可：

![VM安装](/images/tools/vm/a/v34.png)

测试网络是否通畅：

```Bash
ping www.baidu.com
```

如果看到这样的结果代表网络畅通：

![VM安装](/images/tools/vm/a/v35.png)

默认ping命令会持续执行，按下`CTRL `+ `C`后命令即可停止。



------

# 设置虚拟机快照

在虚拟机安装完成后，最好立刻设置一个快照，这样一旦将来虚拟机出现问题，可以快速恢复。

我们先停止虚拟机，点击 **VMware** 顶部菜单中的`暂停`**`下拉选框`**，选择`关闭客户机`：

![VM快照](/images/tools/vm/a/v36.png)

接着，点击VMware菜单中的🔧按钮:

![VM快照](/images/tools/vm/a/v37.png)

然后在弹出的快照管理窗口中，点击 **拍摄快照**，填写新的快照信息：

![VM快照](/images/tools/vm/a/v38.png)

快照拍摄完成了！而且我们可以在不同阶段拍摄多个不同快照作为备份，方便后期恢复数据。

假如以后虚拟机文件受损，需要恢复到初始状态的话，可以选中要恢复的快照，点击转到即可：

![VM快照](/images/tools/vm/a/v39.png)





