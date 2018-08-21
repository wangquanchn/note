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

