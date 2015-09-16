###issue
Mac下安装了mysql，在Rails开发过程中遇到插入中文就报错，报错信息如下：

```
ActiveRecord::StatementInvalid in CommentsController#create
Mysql2::Error: Incorrect string value: '\xE9\x99\x88\xE4\xBB\x95...' for column 'author' at row 1: INSERT INTO `online_issue_comments` (`author`, `content`, `created_at`, `online_issue_id`, `updated_at`) VALUES ('我是中文', 'agagagaaga gaga', '2015-06-15 13:25:29', 1, '2015-06-15 13:25:29')
```

###solution

1. 进入myql, 执行`show variables like 'character_set_%';` 查看编码:  

```
| character_set_client | utf8
| character_set_connection | utf8
| character_set_database | utf8
| character_set_filesystem | binary
| character_set_results | utf8
| character_set_server | utf8
| character_set_system | utf8
```

Mac下有一些默认是Latin，不是utf8，如果有不是 utf8 的，执行下面的操作:
先停止 mysql 服务,拷贝 /usr/local/mysql/support-files 下的任意一个 *.cnf 到 /etc/my.cnf 下，并加入下面的配置:

```
default-storage-engine=INNODB
character-set-server=utf8
collation-server=utf8_general_ci
[mysqld]
character-set-server=utf8
[client]
default-character-set=utf8
```
重启mysql，重新创建数据库和表，插入中文，成功。

