#### 在文件系统中移动

cd是一个用来改变目录的命令。和其他命令不同，cd实际上不是一个程序，而是Shell内建的。这意味着cd没有自己的手册页。你必须查看你使用的Shell的文档来获取更多关于cd的信息。绝大多数时候，它们都一样。  
```plain
darkstar:~$ cd /
darkstar:/$ls
bin/   dev/  home/  lost+found/  mnt/  proc/  sbin/  sys/  usr/
boot/  etc/  lib/   media/       opt/  root/  srv/   tmp/  var/
darkstar:/$cd /usr/local
darkstar:/usr/local$
```  

当我们改变了目录后，注意到提示变了没？Slackware默认的Shell以简单明了的方式让你看到你当前所在的目录，但是这并不是cd做的。如果你的Shell没有以上的提示，你也可以用pwd(1)命令来获取当前所在的目录。  
```plain
darkstar:~$ pwd
/usr/local
```
