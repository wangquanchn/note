关闭防火墙

```shell
# iptables -F
# iptables -F -t nat
# iptables -X
# iptables -X -t nat
```

#### CentOS 7 开启80端口 ####

```shell
firewall-cmd --zone=public --add-port=80/tcp --permanent
```

| 命令              | 含义                            |
| ----------------- | ------------------------------- |
| --zone            | 作用域                          |
| --add-port=80/tcp | 添加端口，格式为：端口/通讯协议 |
| --permanent       | 永久生效，没有此参数重启后失效  |

**重启防火墙**

```shell
systemctl stop firewalld.service
systemctl start firewalld.service
```

