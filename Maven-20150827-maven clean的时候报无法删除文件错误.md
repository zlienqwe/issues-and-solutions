###issue
Jenkins上的maven工程执行'mvn clean test'好好的，突然报了了这个错误，查了下可能原因是这个文件刚好被其他进程用到。

```
[ERROR] Failed to execute goal org.apache.maven.plugins:maven-clean-plugin:2.4.1:clean (default-clean) on project tcui: Failed to clean project: Failed to delete F:\jenkins\workspace\tc_ui_test\target\surefire\surefirebooter55827821186128447.jar -> [Help 1]
[ERROR]
[ERROR] To see the full stack trace of the errors, re-run Maven with the -e switch.
[ERROR] Re-run Maven using the -X switch to enable full debug logging.
[ERROR]
[ERROR] For more information about the errors and possible solutions, please read the following articles:
[ERROR] [Help 1] http://cwiki.apache.org/confluence/display/MAVEN/MojoExecutionException
Build step 'Execute Windows batch command' marked build as failure

```

###solution

加一个参数：`-Dmaven.clean.failOnError=false`


```
mvn clean test -Dmaven.clean.failOnError=false
```