###issue
开发jenkins插件，执行命令：

```
hzchenshibin@qa7:~/popo$ mvn hpi:run -Djetty.port=8282 
```
报错如下：

```
Jul 25, 2015 10:35:02 AM hudson.model.AbstractBuild$AbstractRunner performAllBuildSteps
WARNING: Publisher com.netease.ci.plugins.popo.PopoNotifier aborted due to exception
java.lang.IllegalStateException: Root URL isn't configured yet. Cannot compute absolute URL.
	at hudson.model.AbstractItem.getAbsoluteUrl(AbstractItem.java:382)
	at hudson.model.Run.getAbsoluteUrl(Run.java:797)
	at com.netease.ci.plugins.popo.PopoNotifier.perform(PopoNotifier.java:40)
	at hudson.tasks.BuildStepMonitor$1.perform(BuildStepMonitor.java:19)
	at hudson.model.AbstractBuild$AbstractRunner.perform(AbstractBuild.java:682)
	at hudson.model.AbstractBuild$AbstractRunner.performAllBuildSteps(AbstractBuild.java:657)
	at hudson.model.AbstractBuild$AbstractRunner.performAllBuildSteps(AbstractBuild.java:635)
	at hudson.model.Build$RunnerImpl.post2(Build.java:161)
	at hudson.model.AbstractBuild$AbstractRunner.post(AbstractBuild.java:604)
	at hudson.model.Run.run(Run.java:1400)
	at hudson.model.FreeStyleBuild.run(FreeStyleBuild.java:46)
	at hudson.model.ResourceController.execute(ResourceController.java:88)
	at hudson.model.Executor.run(Executor.java:175)
```

####solution

解决办法：

###### Manage Jenkins -->Configure System -->Jenkins URL
Jenkins URL: http://localhost:8282/