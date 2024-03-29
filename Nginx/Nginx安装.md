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

# wget ftp://ftp.csx.cam.ac.uk/pub/software/programming/pcre/pcre-8.42.tar.gz 
# wget https://ftp.pcre.org/pub/pcre/pcre-8.42.tar.bz2
wget https://ftp.halifax.rwth-aachen.de/osdn/sfnet/p/pc/pcre/pcre/8.42/pcre-8.42.tar.bz2

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
./configure --prefix=/data/program/nginx \
--with-http_ssl_module \
--with-pcre=/usr/local/src/pcre-8.42 \
--with-zlib=/usr/local/src/zlib-1.2.11 \
--with-openssl=/usr/local/src/openssl-1.0.1t
make
make install
```

nginx编译安装之-./configure 参数详解：

```text
https://www.cnblogs.com/flashfish/p/11025961.html
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









### 一、安装编译工具及库文件

```shell
yum -y install make zlib zlib-devel gcc-c++ libtool  openssl openssl-devel
```

### 二、首先要安装 PCRE

PCRE 作用是让 Nginx 支持 Rewrite 功能。

1、下载 PCRE 安装包

```shell
cd /usr/local/src/
wget http://downloads.sourceforge.net/project/pcre/pcre/8.35/pcre-8.35.tar.gz
```

2、解压安装包:

```shell
tar zxvf pcre-8.35.tar.gz
```

3、进入安装包目录

```shell
cd pcre-8.35
```

4、编译安装

```shell
./configure
make && make install
```

5、查看pcre版本

```shell
pcre-config --version
```



### 三、安装SSL

```shell
yum -y install openssl openssl-devel
```



### 四、安装Nginx

```shell
mkdir -p /data/program/nginx
cd /data/program/nginx

yum install -y lrzsz
rz 上传文件

tar -zxvf nginx-1.13.6.tar.gz

cd nginx-1.13.6

./configure --prefix=/data/program/nginx/nginx-1.13.6 \
--sbin-path=/data/program/nginx/nginx-1.13.6/nginx \
--conf-path=/data/program/nginx/nginx-1.13.6/nginx.conf \
--pid-path=/data/program/nginx/nginx-1.13.6/nginx.pid \
--with-http_stub_status_module \
--with-http_ssl_module \
--with-pcre=/usr/local/src/pcre-8.35

make
make install
```







```shell
docker run \
  -u root \
  --rm \
  -d \
  --name docker_nginx \
  -p 80:80 \
  -v /data/program/docker/volume/nginx/nginx.conf:/etc/nginx/nginx.conf \
  -v /data/program/docker/volume/nginx/conf.d:/etc/nginx/conf.d \
  -v /data/program/docker/volume/nginx/html:/usr/share/nginx/html \
  -v /data/program/docker/volume/nginx/log/access.log:/var/log/nginx/access.log \
  -v /data/program/docker/volume/nginx/log/error.log:/var/log/nginx/error.log \
  docker.io/nginx
```



```groovy
user  nginx;
worker_processes  1;

error_log  /var/log/nginx/error.log warn;
pid        /var/run/nginx.pid;

events {
    worker_connections  1024;
}

http {
    include       /etc/nginx/mime.types;
    default_type  application/octet-stream;

    log_format  main  '$remote_addr - $remote_user [$time_local] "$request" '
                      '$status $body_bytes_sent "$http_referer" '
                      '"$http_user_agent" "$http_x_forwarded_for"';

    access_log  /var/log/nginx/access.log  main;

    sendfile        on;
    #tcp_nopush     on;

    keepalive_timeout  65;

    #gzip  on;

    include /etc/nginx/conf.d/*.conf;
}
```



```groovy
server {
    listen       80;
    server_name  localhost;

    #charset koi8-r;
    #access_log  /var/log/nginx/host.access.log  main;

    location / {
        root   /usr/share/nginx/html;
        index  index.html index.htm;
    }

    #error_page  404              /404.html;

    # redirect server error pages to the static page /50x.html
    #
    error_page   500 502 503 504  /50x.html;
    location = /50x.html {
        root   /usr/share/nginx/html;
    }

    # proxy the PHP scripts to Apache listening on 127.0.0.1:80
    #
    #location ~ \.php$ {
    #    proxy_pass   http://127.0.0.1;
    #}

    # pass the PHP scripts to FastCGI server listening on 127.0.0.1:9000
    #
    #location ~ \.php$ {
    #    root           html;
    #    fastcgi_pass   127.0.0.1:9000;
    #    fastcgi_index  index.php;
    #    fastcgi_param  SCRIPT_FILENAME  /scripts$fastcgi_script_name;
    #    include        fastcgi_params;
    #}

    # deny access to .htaccess files, if Apache's document root
    # concurs with nginx's one
    #
    #location ~ /\.ht {
    #    deny  all;
    #}
}
```







查看防火墙状态

```shell
# 查看防火墙状态
firewall-cmd --state
# 查看端口
firewall-cmd --list-ports
# 添加端口
firewall-cmd --zone=public --add-port=443/tcp --permanent
# 重启
firewall-cmd --reload
```



### 五、配置

**当我们访问http://proxy_location/my_path时:**

|                  |                     |                                      |
| ---------------- | ------------------- | ------------------------------------ |
| /proxy_location/ | http://server       | http://server/proxy_location/my_path |
| /proxy_location/ | http://server/      | http://server/my_path                |
| /proxy_location  | http://server       | http://server/proxy_location/my_path |
| /proxy_location  | http://server/      | http://server//my_path               |
| /proxy_location/ | http://server/path  | http://server/pathmy_path            |
| /proxy_location/ | http://server/path/ | http://server/path/my_path           |
| /proxy_location  | http://server/path  | http://server/path/my_path           |
| /proxy_location  | http://server/path/ | http://server//my_path               |



location指令说明，该语法用来匹配url，语法如下：

```conf
location[ = | ~ | ~* | ^~] url{
}
```

1. =: 用于不含正则表达式的url前，要求字符串与url严格匹配，匹配成功就停止向下搜索并处理请求
2. ~: 用于表示url包含正则表达式，并且区分大小写。
3. ~*: 用于表示url包含正则表达式，并且不区分大瞎写
4. ^~: 用于不含正则表达式的url前，要求ngin服务器找到表示url和字符串匹配度最高的location后，立即使用此location处理请求，而不再匹配
5. 如果有url包含正则表达式，不需要有~开头标识



























