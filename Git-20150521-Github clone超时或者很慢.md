###issue
Github经常被墙，Git clone要么龟速要么超时异常。

###solution
因为我本地长期使用SSH端口转发的方式翻墙，转发端口是7070，所以只需要在.gitconfig文件里面为git添加ss代理即可,也可用命令方式:

添加SS代理:
```
git config --global http.proxy "127.0.0.1:7070"
```

移除SS代理：
```
git config --global --remove-section http
```

