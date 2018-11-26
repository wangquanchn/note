# MySQL 5.7版本 CentOS 7.2 安装

## 一、安装Mysql

1. 下载mysql的repo源：
   ```shell
   wget http://repo.mysql.com/mysql57-community-release-el7-8.noarch.rpm
   ```

2. 安装源：
   ```shell
   rpm -ivh mysql57-community-release-el7-8.noarch.rpm
   ```

3.  安装数据库
   ```shell
   yum install mysql-server
   ```

4.  启动数据库
   ```shell
   systemctl start mysqld
   ```




## 二、登录到Mysql 5.7

1. Mysql 5.7版本默认对于root帐号有一个随机密码，可以通过

   ```shell
   grep "password" /var/log/mysqld.log
   ```

   获得，`root@localhost:` 此处为`随机密码`

2. 运行

   ```shell
   mysql -uroot -p
   ```

3. 粘贴`随机密码`，第一次登录mysql



## 三、修改默认密码

现在我们已经登录了mysql，但是默认的随机密码是没办法直接对数据库做操作的，需要修改密码。

同时，5.7版本用了validate_password密码加强插件，因此在修改密码的时候绝对不是 123456 能糊弄过去的，需要严格按照规范去设置密码。

这里我们登录后，使用如下命令修改默认密码：

```mysql
ALTER USER 'root'@'localhost' IDENTIFIED BY 'root!!MYSQL1234';
```



## 四、赋权操作

默认情况下其他服务器的客户端不能直接访问mysql服务端，需要对ip授权：

```mysql
GRANT ALL PRIVILEGES ON . TO 'root'@'%' IDENTIFIED BY 'root' WITH GRANT OPTION;
```



## 五、查看字符集

显示所有变量：

   ```mysql
show variables like 'character%';
   ```

结果显示：

```
+--------------------------+----------------------------+
| Variable_name            | Value                      |
+--------------------------+----------------------------+
| character_set_client     | utf8                       |
| character_set_connection | utf8                       |
| character_set_database   | latin1                     |
| character_set_filesystem | binary                     |
| character_set_results    | utf8                       |
| character_set_server     | latin1                     |
| character_set_system     | utf8                       |
| character_sets_dir       | /usr/share/mysql/charsets/ |
+--------------------------+----------------------------+
```

此时，我们需要修改mysql的/etc/my.cnf 文件中的字符集键值：

```shell
vim /etc/my.cnf
```

在`[mysqld]`字段下加入`character_set_server=utf8`，如下：

```ini
[mysqld]

datadir=/var/lib/mysql
socket=/var/lib/mysql/mysql.sock

symbolic-links=0

log-error=/var/log/mysqld.log
pid-file=/var/run/mysqld/mysqld.pid

character_set_server=utf8
```

修改完成后，使用`systemctl restart mysqld`重启mysql服务

```shell
systemctl restart mysqld
```

 然后再次登录mysql，使用`show variables like 'character%';`查看

```
+--------------------------+----------------------------+
| Variable_name            | Value                      |
+--------------------------+----------------------------+
| character_set_client     | utf8                       |
| character_set_connection | utf8                       |
| character_set_database   | utf8                       |
| character_set_filesystem | binary                     |
| character_set_results    | utf8                       |
| character_set_server     | utf8                       |
| character_set_system     | utf8                       |
| character_sets_dir       | /usr/share/mysql/charsets/ |
+--------------------------+----------------------------+
```

此时，我们的字符集已经都修改完毕。









































