###issue
Jenins上有一个Job配的是Maven + Sonar，今天突然在执行到Sonar代码分析这一步的时候报错：

![](http://i4.tietuku.com/c8923de8eaa48cd2.png)

```
[ERROR] Failed to execute goal org.codehaus.mojo:sonar-maven-plugin:2.5:sonar (default-cli) on project nefs-fsi: PermGen space -> [Help 1]
org.apache.maven.lifecycle.LifecycleExecutionException: Failed to execute goal org.codehaus.mojo:sonar-maven-plugin:2.5:sonar (default-cli) on project nefs-fsi: PermGen space
    at org.apache.maven.lifecycle.internal.MojoExecutor.execute(MojoExecutor.java:216)
    at org.apache.maven.lifecycle.internal.MojoExecutor.execute(MojoExecutor.java:153)
    at org.apache.maven.lifecycle.internal.MojoExecutor.execute(MojoExecutor.java:145)
    at org.apache.maven.lifecycle.internal.LifecycleModuleBuilder.buildProject(LifecycleModuleBuilder.java:116)
    at org.apache.maven.lifecycle.internal.LifecycleModuleBuilder.buildProject(LifecycleModuleBuilder.java:80)
    at
    ...
Caused by: java.lang.OutOfMemoryError: PermGen space
[ERROR]
[ERROR] Re-run Maven using the -X switch to enable full debug logging.
[ERROR]
[ERROR] For more information about the errors and possible solutions, please read the following articles:
[ERROR] [Help 1] http://cwiki.apache.org/confluence/display/MAVEN/MojoExecutionException
Sonar analysis completed: FAILURE
Build step 'Sonar' changed build result to FAILURE
Build step 'Sonar' marked build as failure
######Start Netease Builder Parser
######Get project ID = 163
######Save job successful, job id=49
######buildStartTime=2015-06-23 09:44:53
######Save job successful, job build id=18084
######Start to parse execute result
######The job type is: TestNG/JUnit Parser
######Build failure. No parsing.
######Parse testNG/JUnit success.
Email was triggered for: Failure - Any
Sending email for trigger: Failure - Any
An attempt to send an e-mail to empty list of recipients, ignored.
Notifying upstream projects of job completion
Finished: FAILURE
```

####solution
在Job中配置MAVEN_OPTS参数：

```
MAVEN_OPTS: -Xms2048m -Xmx2048m -XX:PermSize=1024m  -XX:MaxPermSize=2048m
```
![](http://i4.tietuku.com/539e9da26c3bdd31.png)
