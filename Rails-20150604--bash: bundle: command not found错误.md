###issue
执行`bundle install`报错 `-bash: bundle: command not found`。这是很多Rails初学者遇到过的错误。

###solution
原因很多时候是因为你用rvm切换到了新的ruby版本，换了新的gemset时，bundler这个gem没有被安装，安装它即可：
`gem install bundler``
