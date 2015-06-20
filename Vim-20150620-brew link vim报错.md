###issue
```
Shibin@Mac$: brew link vim
Linking /usr/local/Cellar/vim/7.4.488... Error: Permission denied - /usr/local/share/man/fr.ISO8859-1

Shibin@Mac$: brew link vim
Linking /usr/local/Cellar/vim/7.4.488...
Error: Could not symlink share/vim
/usr/local/share is not writable.

Shibin@Mac $  /usr/local/share (master) $ brew link vim
Linking /usr/local/Cellar/vim/7.4.488... 122 symlinks created
```

###solution
```
$ sudo chown -R Shibin:admin /usr/local/share/man/
Shibin@Mac $  /usr/local/share (master) $ sudo chown -R Shibin:admin /usr/local/share
```
