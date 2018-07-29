# #CentOS yum源修改

## #CentOS7 yum源修改

`CentOS yum`源所在目录`/etc/yum.repos.d`。进入到`yum`目录下，备份当前`yum`源：

```cmd
$ cd /etc/yum.repos.d/
$ mv CentOS-Base.repo CentOS-Base.repo.bak  #备份yum源
```

### #1.修改为阿里云源

下载阿里源`yum`的文件：

```cmd
$ wget -O CentOS-Base.repo http://mirrors.aliyun.com/repo/Centos-7.repo 
#清理缓存 
$ yum clean all 
#重新生成缓存 
$ yum makecache
# 更新
$ yum -y update
```

### #2.修改为163源

下载163的`yum`源文件：

```cmd
$ wget -O CentOS-Base.repo http://mirrors.163.com/.help/CentOS6-Base-163.repo
#清理缓存 
$ yum clean all 
#重新生成缓存 
$ yum makecache
# 更新
$ yum -y update
```
