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



**查看MySQL版本**

```sql
SELECT VERSION();
```

查看MySQL当前状态

```sql
SHOW GLOBAL STATUS LIKE 'Thread%';
```

非交互式超时时间，如JDBC程序


```sql
SHOW GLOBAL VARIABLES LIKE 'wait_timeout';
```

交互式超时时间，如数据库工具


```sql
SHOW GLOBAL VARIABLES LIKE 'interactive_timeout';
```

查询“查询缓存”开关


```sql
SHOW VARIABLES LIKE 'query_cache%';
```

查看存储引擎状态


```sql
SHOW ENGINE innodb status;
```



在哪些列上建立索引

1.列的离散度

2.联合索引左匹配







优化

1. 重启
2. 连接优化
   - 服务器最大连结数
   - 客户端连接超时时间wait_timeout
   - 连接池