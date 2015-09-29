###issue
本地准备弄下Rails的单元测试，在执行命令

```
rake db:migrate RAILS_ENV=test
```
的时候报错:

```
rake aborted!
ActiveRecord::StatementInvalid: Mysql2::Error: Can't read dir of './qm_test/' (errno: 13 - Permission denied): SHOW TABLES LIKE 'schema_migrations'
/Users/Heros/.rvm/gems/ruby-2.0.0-p643@rails4.2/gems/activerecord-4.1.12/lib/active_record/connection_adapters/abstract_mysql_adapter.rb:303:in `query'
/Users/Heros/.rvm/gems/ruby-2.0.0-p643@rails4.2/gems/activerecord-4.1.12/lib/active_record/connection_adapters/abstract_mysql_adapter.rb:303:in `block in execute'
/Users/Heros/.rvm/gems/ruby-2.0.0-p643@rails4.2/gems/activerecord-4.1.12/lib/active_record/connection_adapters/abstract_adapter.rb:378:in `block in log'
/Users/Heros/.rvm/gems/ruby-2.0.0-p643@rails4.2/gems/activesupport-4.1.12/lib/active_support/notifications/instrumenter.rb:20:in `instrument'
/Users/Heros/.rvm/gems/ruby-2.0.0-p643@rails4.2/gems/activerecord-4.1.12/lib/active_record/connection_adapters/abstract_adapter.rb:372:in `log'
```
###solution

查了下，是因为数据库data文件(这里是qm_test)的权限不对。

```
ps aux | grep mysql  #在结果中得到-datadir=/usr/local/var/mysql
cd /usr/local/var/mysql
ls -alt
sudo chown _mysql:admin qm_test #修改qm_test的owner为_mysql，组为admin
```