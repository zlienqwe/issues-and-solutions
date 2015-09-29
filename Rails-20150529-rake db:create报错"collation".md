###issue
本地配置好`config/database.xml`后执行`rake db:create`报错：

```
Couldn't create database for {"adapter"=>"mysql2", "encoding"=>"utf8", "reconnect"=>false, "database"=>"dev", "host"=>"localhost", "pool"=>5, "username"=>"root", "password"=>"root", "socket"=>"/var/run/mysqld/mysqld.sock"}, {:charset=>"utf8", :collation=>"utf8_unicode_ci"}
(If you set the charset manually, make sure you have a matching collation)
Couldn't create database for {"adapter"=>"mysql2", "encoding"=>"utf8", "reconnect"=>false, "database"=>"test", "host"=>"localhost", "pool"=>5, "username"=>"root", "password"=>"root", "socket"=>"/var/run/mysqld/mysqld.sock"}, {:charset=>"utf8", :collation=>"utf8_unicode_ci"}
(If you set the charset manually, make sure you have a matching collation)
```
###solution

在`config/database.xml`里面将`localhost`改成`127.0.0.1`就好了，原因不是很清楚。

###补充(2015-09-29)
今天执行`rake db:create RAILS_ENV=test`命令创建数据库的时候再次报这个错误，解决方法还是改`localhost`为`127.0.0.1`