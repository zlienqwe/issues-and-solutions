###issue
开发jenkins插件，执行命令：

```
mvn hpi:run
```  

报错`java.net.BindException: Address already in use`

####solution
原因是默认的端口8080已经被占用，查了下Maven的官方说明[https://jenkins-ci.org/maven-hpi-plugin/run-mojo.html](https://jenkins-ci.org/maven-hpi-plugin/run-mojo.html),发现有一个`-Djetty.port=PORT`参数。于是解决办法就来了：

```
mvn hpi:run -Djetty.port=8282 
```