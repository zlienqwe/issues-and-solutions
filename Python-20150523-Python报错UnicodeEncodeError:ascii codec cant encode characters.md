###issue
执行一个Python文件遇到报错：
```
UnicodeEncodeError: 'ascii' codec can't encode characters in position 4-7: ordinal not in range(128)
```
###solution
Python2.7安装的时候默认使用ascii编码，当程序中出现非ascii编码时，python的处理常常会报这样的错，(python3没有这样的问题)  
代码中加入如下三行:

```
import sys
reload(sys)
sys.setdefaultencoding('utf8')
```

