### 链接

链接是使用不同名字引用相同文件的方式。使用`ln(1)`程序，用户就能使用不同名字引用相同文件。这两个文件不是把一个复制了一遍，也不是完全相同的两个独立文件，仅仅是不同名字而已。（这就像`rm`或其他工具删除的原理一样，并非抹除了文件内容，只是解除了文件的引用并释放空间以供再次使用。`ln`与之相反，只是创建到文件的第二个引用）要想完整删除一个文件，所有的名字必须删除。

```Shell
darkstar:~$ ln /etc/slackware-version foo
darkstar:~$ cat foo
Slackware 14.0
darkstar:~$ ls -l /etc/slackware-version foo
-rw-r--r-- 1 root root 17 2007-06-10 02:23 /etc/slackware-version
-rw-r--r-- 1 root root 17 2007-06-10 02:23 foo
```

还有另一种类型的链接：符号链接。符号链接不是到文件的引用，而是一种有自己独立权限的特殊文件。符号链接会指向另外的文件或目录。符号链接的优点就是能像文件一样引用目录，并且可跨文件系统。可用[-s]参数来创建符号链接。

```Shell
darkstar:~$ ln -s /etc/slackware-version foo
darkstar:~$ cat foo
Slackware 140
darkstar:~$ ls -l /etc/slackware-version foo
-rw-r--r-- 1 root root 17 2007-06-10 02:23 /etc/slackware-version
lrwxrwxrwx 1 root root 22 2008-01-25 04:16 foo -> /etc/slackware-version
```

使用符号链接时，注意如果源文件被删掉了，符号链接就会失效：此时它指向一个不存在的文件。
