# #CentOS 安装nginx 问题 No package nginx available

出现`No package nginx available`问题的原因，是`nginx`存在于第三方源，在`CentOS-Base.repo`基源中不存在。所以需要安装第三方源`epel`。
`EPEL(Extra Packages for Enterprise Linux)`是`yum`的一个软件源,里面包含了许多基本源里没有的软件了，是为企业级Linux提供的一组高质量的额外软件包，包括但不限于Red Hat Enterprise Linux (RHEL), CentOS and Scientific Linux (SL), Oracle Enterprise Linux (OEL)等。

## #现象如下：

```code
[root@56652fe85231 /]# yum install nginx
Loaded plugins: fastestmirror, ovl
Loading mirror speeds from cached hostfile
 * base: mirrors.cn99.com
 * extras: mirrors.cn99.com
 * updates: mirrors.cn99.com
No package nginx available.
Error: Nothing to do
```

## #解决办法：

***先安装epel:***

```code
# yum install epel-release
# yum install nginx
```
