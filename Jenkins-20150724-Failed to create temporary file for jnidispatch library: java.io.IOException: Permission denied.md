###issue
开发jenkins插件，执行命令：

```
hzchenshibin@qa7:~/popo$ mvn hpi:run -Djetty.port=8282 
```
报错如下：

```
Failed to create temporary file for jnidispatch library: java.io.IOException: Permission denied
```

####solution

原因是因为当前用户对` /tmp/jna`这个临时目录没有写的权限，解决办法是用`java.io.tmpdir`参数指定路径：

```
hzchenshibin@qa7:~/popo$ mvn hpi:run -Djetty.port=8282 -Djava.io.tmpdir=/home/hzchenshibin/tmp
```