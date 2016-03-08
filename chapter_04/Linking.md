### 链接

链接是一种使用多个不同名字引用一个文件的方法。使用ln(1)命令，用户可以使用多个名字来引用同一个文件。这两个文件之间比不是副本，可以说是一样的文件，只是名字不同而已。要完整的删掉文件，它所有的链接都必须被删掉。（事实上这也是rm和同类工具做的事情，不是删掉文件的内容，而是简单的删除这个文件的引用，释放空间来重用。ln会创建文件的一个引用或是符号链接。）  
```plain
darkstar:~$ ln /etc/slackware-version foo
darkstar:~$ cat foo
Slackware 14.0
darkstar:~$ ls -l /etc/slackware-version foo
-rw-r--r-- 1 root root 17 2007-06-10 02:23 /etc/slackware-version
-rw-r--r-- 1 root root 17 2007-06-10 02:23 foo
```  

另一种链接是符号链接，符号链接不是原文件的引用，而是一种特殊的文件。这些符号链接指向其它文件或者目录。它的主要优势是既可以指向文件又可以指向目录，并且可以跨文件系统。它们通过传递[-s]参数给ln来创建。  

```plain
darkstar:~$ ln -s /etc/slackware-version foo
darkstar:~$ cat foo
Slackware 140
darkstar:~$ ls -l /etc/slackware-version foo
-rw-r--r-- 1 root root 17 2007-06-10 02:23 /etc/slackware-version
lrwxrwxrwx 1 root root 22 2008-01-25 04:16 foo -> /etc/slackware-version
```  

对于符号链接，如果原文件被删除了，那么这链接就没用了，仅仅表示指向了一个不存在的文件。
