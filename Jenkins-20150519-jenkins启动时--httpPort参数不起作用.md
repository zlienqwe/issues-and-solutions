###issue
本地执行命令：`java -DJENKINS_HOME=/Users/Heros/jenkins -jar jenkins.war  --httpPort=8484`发现不起作用，jenkins启动还是在默认的8080端口。

####solution
执行：`java -DJENKINS_HOME=/Users/Heros/jenkins -jar jenkins.war -–httpPort=-1 --httpPort=8484`
下次只需：`java -DJENKINS_HOME=/Users/Heros/jenkins -jar jenkins.war  --httpPort=8484`
