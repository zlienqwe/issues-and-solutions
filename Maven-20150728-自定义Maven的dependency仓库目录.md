###issue
Maven使用mvn命令构建时默认会从中央仓库下载dependency依赖包到~/.m2目录下，一般我们可以通过修改Maven_install_path/conf/settings.xml中的localRepository参数。比如：

```
<localRepository>/Users/Heros/.m2/repository</localRepository>

```
可是如果是服务器上，我们没有权限修改Maven安装目录下的这个settings.xml文件，那这时候怎么修改默认的~/.m2目录为其它目录呢？


###solution

在~/.m2下创建一个settings.xml文件，添加内容如下：

```
<setting>
 <localRepository>/Users/Heros/.m2/repository</localRepository>
</setting>
```