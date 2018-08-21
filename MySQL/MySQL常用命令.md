# 5.7.23 MySQL Community Server #

**授权指定IP访问MySQL服务器**

```mysql
mysql> GRANT ALL PRIVILEGES ON *.* TO 'root'@'192.168.2.145' IDENTIFIED BY 'Ymf!!2018' WITH GRANT OPTION;
Query OK, 0 rows affected, 1 warning (0.33 sec)
```

**刷新权限使其生效**

```mysql
mysql> flush privileges;
```



