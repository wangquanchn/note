# CentOS 7 #

### 查看IP

```shell
[root@localhost ~]# ip addr
```

### 显示目前所支持的语系 ###

```shell
[root@localhost ~]# locale
LANG=zh_CN.UTF-8
LC_CTYPE="zh_CN.UTF-8"
LC_NUMERIC="zh_CN.UTF-8"
LC_TIME="zh_CN.UTF-8"
LC_COLLATE="zh_CN.UTF-8"
LC_MONETARY="zh_CN.UTF-8"
LC_MESSAGES="zh_CN.UTF-8"
LC_PAPER="zh_CN.UTF-8"
LC_NAME="zh_CN.UTF-8"
LC_ADDRESS="zh_CN.UTF-8"
LC_TELEPHONE="zh_CN.UTF-8"
LC_MEASUREMENT="zh_CN.UTF-8"
LC_IDENTIFICATION="zh_CN.UTF-8"
LC_ALL=
```

### 显示日期与时间

```shell
[root@localhost ~]# date
2018年 08月 20日 星期一 17:54:02 CST
```

### 防火墙 ###

- 停止firewall

  ```shell
  [root@localhost ~]# systemctl stop firewalld.service
  ```

- 禁止firewall开机启动

  ```shell
  [root@localhost ~]# systemctl disable firewalld.service
  ```

- 重启防火墙使配置生效

  ```shell
  [root@localhost ~]# systemctl restart iptables.service
  ```

- 设置防火墙开机启动

  ```shell
  [root@localhost ~]# systemctl enable iptables.service
  ```



yum repolist all
列出所有仓库。
yum list all	列出仓库中所有软件包
yum info软件包名称	查肴软件包信息
yum install软件包名称	安装软件包
yum reinstall软件包名称	重新安装软件包
yum update软件包名称	升级软件包
yum remove软件包	移除软件包
yum clean alia	清除所有仓库缓存
yum check-update	检查可更新的软件包
yum grouplist	查看系统中已经安装的软件包
yum groupinstall 软件包组	安装指定的软件包组
yum groupremove 软件包组	移除指定的软件包鲍
yum groupinfo软件包组	查询指定的软件包组信息