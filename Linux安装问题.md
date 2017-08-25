## lsb_release安装

标签： lsb_release 	分类： linux<br>
想查看一下系统内核信息，<br>
用lsb_release -a,提示不存在，安装一下：<br>
> yum install redhat-lsb

然后再lsb_release -a<br>
LSB Version:    :core-4.0-ia32:core-4.0-noarch:graphics-4.0-ia32:graphics-4.0-noarch:printing-4.0-ia32:printing-4.0-noarch<br>
Distributor ID: CentOS<br>
Description:    CentOS Linux release 6.0 (Final)<br>
Release:        6.0<br>
Codename:       Final

## Linux（centos7） 安装VmwareTools问题

**安装步骤**

解压vmware tools，得到vmware-tools-distrib文件夹，用root权限运行其下的vmware-install.pl文件

* tar -xzvf VMwareTolls-9.2.3-1031360.tar.gz 
* cd vmware-tools-distrib 
* sudo ./vmware-install.pl

**出现问题**

1、gcc错误
Searching for GCC...
The path "" is not valid path to the gcc binary.

2、内核头文件问题
Searching for a valid kernel header path...
The path "" is not a valid path to the 3.10.0-229.el7.x86_64 kernel headers.

**解决方式**

- yum -y update <br>
- yum -y install kernel-headers kernel-devel gcc
- sudo apt-get install linux-headers-`uname -r`

然后进行`reboot`，重行执行安装操作

