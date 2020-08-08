---
title: mac安装mysql8.0
tags: mysql
categories: sql
date: 2020-08-08 19:05:27
---
Mac安装mysql8.0版本
<!-- more -->
## 安装

```bash
# Mac安装MySQL
brew install mysql
mysql.server start
mysql_secure_installation
OK
```

## 基本操作

```bash
# 启动 mysql, 并设置为开机启动
brew services start mysql
# 关闭 mysql
brew services stop mysql
# 重启 mysql
brew services restart mysql
```

## 安装过程详情记录

```bash
#### mysql_secure_installation #### 步骤详解
Securing the MySQL server deployment.

Connecting to MySQL using a blank password.

VALIDATE PASSWORD COMPONENT can be used to test passwords
and improve security. It checks the strength of password
and allows the users to set only those passwords which are
secure enough. Would you like to setup VALIDATE PASSWORD component?

Press y|Y for Yes, any other key for No: y   //使用密码验证

There are three levels of password validation policy:   

LOW    Length >= 8
MEDIUM Length >= 8, numeric, mixed case, and special characters
STRONG Length >= 8, numeric, mixed case, special characters and dictionary                  file

Please enter 0 = LOW, 1 = MEDIUM and 2 = STRONG: 0  // 选择密码验证等级
Please set the password for root here.

New password:    // 输入新密码

Re-enter new password: 

Estimated strength of the password: 50 
Do you wish to continue with the password provided?(Press y|Y for Yes, any other key for No) : y  
By default, a MySQL installation has an anonymous user,
allowing anyone to log into MySQL without having to have
a user account created for them. This is intended only for
testing, and to make the installation go a bit smoother.
You should remove them before moving into a production
environment.

Remove anonymous users? (Press y|Y for Yes, any other key for No) : y   //删除匿名用户
Success.


Normally, root should only be allowed to connect from
'localhost'. This ensures that someone cannot guess at
the root password from the network.

Disallow root login remotely? (Press y|Y for Yes, any other key for No) : n // 是否禁止远程登录

 ... skipping.
By default, MySQL comes with a database named 'test' that
anyone can access. This is also intended only for testing,
and should be removed before moving into a production
environment.


Remove test database and access to it? (Press y|Y for Yes, any other key for No) : y  // 是否删除测试库
 - Dropping test database...
Success.

 - Removing privileges on test database...
Success.

Reloading the privilege tables will ensure that all changes
made so far will take effect immediately.

Reload privilege tables now? (Press y|Y for Yes, any other key for No) : y  // 刷新数据库权限
Success.

All done!   // 完成
```

## 修改root密码

```bash
# mysql5.7.9 及更高版本修改root密码方式
# 1.开启mysql跳过密码登录
mysqld_safe --user=mysql --skip-grant-tables --skip-networking &
# 2.命令运行后，重新开启命令行窗口进行下面操作
mysql -u root -p
# NOTE：不用输入密码直接点击enter
# 3.切换数据库，使用mysql库
use mysql;
# 4.查询user用户表，查看用户民和密码
select host, user, authentication_string, plugin from user; # 查询表语句
# 5.如果user表中的root用户的authentication_string字段有值，则清空
update user set authentication_string='' where user='root';
# 6.修改root用户的密码 
ALTER user 'root'@'localhost' IDENTIFIED BY 'admin123456';
#####################################################################################

# 5.7.9以下版本修改root密码方式，只是修改的语句不一样
use mysql;
update user set password=PASSWORD('admin123456') where user='root';

# mac上brew安装mysql更改数据存储位置
# 1、创建数据存储目录
mkdir /data/mysqldb
# 2、移动或复制数据库文件
sudo cp -rp /usr/local/var/mysql /data/mysqldb
# 3、修改配置文件
vim /usr/local/etc/my.cnf
 ## Default Homebrew MySQL server config
 # [mysqld]
## Only allow connections from localhost
# bind-address = 127.0.0.1
## data file path
# datadir=/data/mysqldb

# 4、查看数据文件存储目录
mysqladmin -u root -p variables | grep datadir



# 用Navicat root用户连接时，会报如下错误：
Authentication plugin 'caching_sha2_password' cannot be loaded: dlopen/usr/local/mysql/lib/plugin/caching_sha2_password.so 2: image not found
# ----------原因：
# mysql 8.0 及以后版本的默认加密方式变了，变成了 caching_sha2_password
# mysql 8.0 之前 版本的默认加密方式是 mysql_native_password
# ----------解决办法
# 修改root用户的加密方式为 mysql_native_password
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'rootPASSWORD';
# mysql创建一个新用户，设置密码加密方式为 mysql_native_password，并授予其所有权限
CREATE USER 'newUser'@'localhost' IDENTIFIED WITH mysql_native_password BY 'newPassWord';
GRANT ALL PRIVILEGES ON *.* TO 'newUser'@'localhost';
# 上述用户名后面跟的是localhost，目的是只允许连到本地才能进行访问，不能远程访问，如何才能远程访问？
# 用%替换localhost，如下：
CREATE USER 'newUser'@'%' IDENTIFIED WITH mysql_native_password BY 'newPassWord';
GRANT ALL PRIVILEGES ON *.* TO 'newUser'@'%';
```

<br><br>{% btn large center, 向博主反馈问题, <https://github.com/wongqingbin/blog/issues> , fas fa-paper-plane %}
