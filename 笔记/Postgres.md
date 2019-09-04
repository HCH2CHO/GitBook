## postgrelSQL

select site,count(*) from photo3 group by site;

update site set start_query=false;

update photo2 set start_detect=false;

select count (*) from photo1 where lat IS NOT NULL;

select count(*) from photo3 where start_info='true';

select count(*) from photo3 where start_detect='true';

select count(*) from photo3 where facenum !=0;



copy (select * from photo3 where start_info='true') to '/mnt/volume-nyc1-01/postgresql/emotion3.csv' with csv;

copy (select * from photo where start_info='true') to '/mnt/volume-nyc1-01/postgresql/emotion.sql' DELIMITER |;

copy (select * from photo3 where site='Changdeokgung Palace Complex, South Korea ' ) to '/mnt/volume-nyc1-01/postgresql/Changdeokgung Palace Complex, South Korea.csv' with csv;

## postgres

`select * from your_table where .... limit 5;`

`select  count(*)  from  table;`

`DROP TABLE table_name;  `

delete from table;

`select site,count(*) from photo group by site;`

`vacuum full`  数据库释放空间

==jqy没有读写权限，容易异常停止，应使用root用户==

```
1.登录postgresql用户：sudo -i -u postgres。
```

```
2.登陆用户之后，可以操纵该用户下的各种数据库。此时这种状态，在本文中称为用户模式：postgres@xxx:~$
```

```
3.在用户模式下可以进行数据库的操作。创建数据库：createdb database_name，删除数据库：dropdb database_name。
```

```
4.要进行操纵，需要进入命令模式。使用psql进行命令的输入：psql database_name，其中database_name指的是数据库的名字，例如psql EmotionMap。此时可以看到命令行变为database_name = #.
```

```
5.在命令模式下可以对该数据库中表进行操纵，包括SQL语句等。
```

```
6.注意，每一条命令需要以分号作为结尾，否则命令行变为database_name. 
代表的是命令仍未结束。
```

```
7.退出命令模式，返回用户模式，可以直接输入：\q or quit  su -
```



* 查看所有数据库

  ```
  (psql) \list or \l    
  ```

* 切换数据库

```
​~~~
psql:\c dbname
​~~~
```

* 列出指定表的所有字段

  ```
  psql:\d tablename
  ```

* 查看指定表的基本情况

  ```
  psql:\d+ tablename
  ```


* 查看某数据占用存储大小

  ```
  (psql) select pg_size_pretty(pg_database_size('dbname'));
  ```


* 查看当前数据库所有table    

  ```
  (psql) \dt
  ```

* 查看当前数据库所有relation

  ```
  (psql) \d
  ```

* 导出数据库（命名随意选择，选这个后缀便于标识）

  ```
  $ pg_dump EmotionMap3 > /mnt/volume-nyc1-01/postgresql/emotion.postgresql
  ```

* Windows下手动使用psql，找到psql.exe所在目录，在此目录打开cmd

  ```
  $ psql -U postgres dbname
  ```

* Windwos下从文本恢复数据库，通常需要先创建一个空数据库dbname，然后

  ```
  $ psql -U postgres dbname < the\path\to\your\backupfile
  ```

* 创建NoSQL扩展：

  ```
  (psql) create extension hstore
  ```

* 在psql中执行bash的命令：

  ```
  (psql) \! dir
  ```

* 导出table

  ```
  (psql) copy TABLENAME [query] to 'FILEPATH' with delimiter '|'
  ```

  copy photo to '/home/jqy/a.csv' with delimiter ',';

* 查看postgres用户的目录 

  ```
  $ echo ~postgres
  ```

* 将指定表到处至压缩文件

  ```
  $ psql -c "copy public.TABLENAME to stdout with delimiter '	' csv header"  DATABASE | zip > TABLENAME.zip
  ```

* 显示配置文件

  ```
  (psql) SHOW config_file;
  ```


* 显示软件版本

  ```
  (psql) SHOW version();
  ```