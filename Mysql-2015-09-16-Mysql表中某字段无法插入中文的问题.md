###issue
数据库的character set 是utf-8，其他列都能插入中文，惟独job_name这一列报错：

```
Incorrect string value: '\xE8\x80\x83\xE6\x8B\x89...' for column 'job_name' at row 1
```
####Analysis
[http://stackoverflow.com/questions/10957238/incorrect-string-value-when-trying-to-insert-utf-8-into-mysql-via-jdbc](http://stackoverflow.com/questions/10957238/incorrect-string-value-when-trying-to-insert-utf-8-into-mysql-via-jdbc)

```
The strings that contain \xF0 are simply characters encoded as multiple bytes using UTF-8.

Although your collation is set to utf8_general_ci, I suspect that the character encoding of the database, table or even column may be different. They are independent settings. Try:

ALTER TABLE database.table MODIFY COLUMN col VARCHAR(255)
    CHARACTER SET utf8 COLLATE utf8_general_ci NOT NULL;
Substitute whatever your actual data type is for VARCHAR(255)
```

###solution

```
ALTER TABLE ci_monitor.jobs MODIFY COLUMN job_name VARCHAR(45)
CHARACTER SET utf8 COLLATE utf8_general_ci NOT NULL;
```

