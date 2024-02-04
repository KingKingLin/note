# MySQL

启动mysql服务: net start mysql

登录root用户: mysql -u root -p
Enter password: n5>3S;AiqVr(

mysql -h 主机名 -u 用户名 -p
-h 主机名，如果主机名是localhost或者127.0.0.1，则该参数可以省略不写
-u 用户名
-p 密码，如果没有密码，则该参数可以省略不写

出现这个错误：You must reset your password using ALTER USER statement before executing this statement.
可以使用如下命令修改密码：alert user 'root'@'localhost' identified by '123456';

密码已经修改为: 123456

--------------------------------------------------------
username: root
password: 123456



# MySQL 开启远程访问

$ mysql -u root -p

mysql> use mysql;

mysql> update user set host = '%' where user = 'root';

mysql> flush privileges;

Query OK, 0 rows affected(0.01sec) 即表示为成功



# MySQL 关闭远程访问

$ mysql -u root -p

mysql> use mysql;

mysql> update user set host = "localhost" where user = "root" and host= "%";

mysql> flush privileges;

Query OK, 0 rows affected(0.01sec) 即表示为成功



# MySQL 支持其他主机访问

在 ==控制面板\所有控制面板项\Windows Defender 防火墙== 的高级设置里

开启 IPV4 的 ICMP 报文连接 => 前两个

打开 3306 端口

```sql
GRANT ALL PRIVILEGES ON *.* TO 'root'@'%' IDENTIFIED BY 'root' WITH GRANT OPTION;
FLUSH PRIVILEGES;
```



# **Oracle**

电子邮箱: 827543964@qq.com

密码: 123456@Lxy





# Redis

我的redis没有设置密码





# Tomcat乱码

虚拟机参数 VM

加上 -Dfile.encoding=UTF-8