###issue
使用`VundleInstall`命令更新完Vim插件之后，保存文件的时候总是报错:
`E382: Cannot write, 'buftype' option is set`
###solution
原因是某些插件修改了`buftype`这个变量的值，改成`nofile`了。有可能是winmanager，bufexplorer，taglist和NERDTree这几个插件。
解决办法是重新打开~/.vimrc，重新设置这个值为空值。
```
vim ~/.vimrc
au VimEnter * set buftype=""
```
