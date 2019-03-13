# Nginx 安装 #

## Centos 7 ##

centos平台编译环境：

安装 `make`

```shell
yum -y install gcc automake autoconf libtool make
```

安装 `g++`

```shell
yum install gcc gcc-c++
```



### 1. 选定源码目录

可以是任何目录，这里选定的是 `/data`

```shell
cd /data
```

### 2. 安装PCRE库

```shell
cd /usr/local/src
wget ftp://ftp.csx.cam.ac.uk/pub/software/programming/pcre/pcre-8.42.tar.gz 
tar -zxvf pcre-8.42.tar.gz
cd pcre-8.42
./configure
make
make install
```

### 3. 安装zlib库 ###

```shell
cd /usr/local/src
wget http://zlib.net/zlib-1.2.11.tar.gz
tar -zxvf zlib-1.2.11.tar.gz
cd zlib-1.2.11
./configure
make
make install
```

### 4. 安装ssl

```shell
cd /usr/local/src
wget https://www.openssl.org/source/openssl-1.0.1t.tar.gz
tar -zxvf openssl-1.0.1t.tar.gz
```

### 5. 安装nginx

```shell
cd /data/files
wget http://nginx.org/download/nginx-1.13.6.tar.gz
tar -zxvf nginx-1.13.6.tar.gz
cd nginx-1.13.6
./configure --prefix=/data/program/nginx/nginx-1.13.6 \
--sbin-path=/data/program/nginx/nginx-1.13.6/nginx \
--conf-path=/data/program/nginx/nginx-1.13.6/nginx.conf \
--pid-path=/data/program/nginx/nginx-1.13.6/nginx.pid \
--with-http_ssl_module \
--with-pcre=/usr/local/src/pcre-8.42 \
--with-zlib=/usr/local/src/zlib-1.2.11 \
--with-openssl=/usr/local/src/openssl-1.0.1t
make
make install
```

### 6. 启动nginx

```shell
cd /data/program/nginx/nginx-1.13.6
./nginx
```



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

