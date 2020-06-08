下载

```shell
wget http://download.redis.io/releases/redis-5.0.5.tar.gz

scp /data/program/redis/redis-5.0.5.tar.gz root@47.103.223.69:/data/program/redis/redis-5.0.5.tar.gz

tar xzf redis-5.0.5.tar.gz
cd redis-5.0.5
make
```

配置文件

```
redis-5.0.5/redis.conf
```

编辑配置文件

```
vim redis-5.0.5/redis.conf

daemonize yes
```


启动redis服务

```
redis-5.0.5/src/redis-server redis-5.0.5/redis.conf
```

