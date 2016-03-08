#### 文件和目录的创建与删除

大多数程序都能自己创建文件和目录，你有时也像自己这么做。幸好，使用`touch(1)`和`mkdir(1)`就能很容易做到。

`touch`实际上只是修改文件的时间戳，如果文件不存在的话就会创建一个。

```Shell
darkstar:~/foo$ ls -l
-rw-r--r-- 1 alan users 0 2012-01-18 15:01 bar1
darkstar:~/foo$ touch bar2
-rw-r--r-- 1 alan users 0 2012-01-18 15:01 bar1
-rw-r--r-- 1 alan users 0 2012-01-18 15:05 bar2
darkstar:~/foo$ touch bar1
-rw-r--r-- 1 alan users 0 2012-01-18 15:05 bar1
-rw-r--r-- 1 alan users 0 2012-01-18 15:05 bar2
```

注意`bar2`是如何被第二条命令创建出来的，以及第三条命令只是修改了`bar1`的时间戳。

`mkdir`用于（这名字很显然）创建目录。`mkdir foo`能在当前文件夹创建一个叫"foo"的目录。此外，你可使用[-p]参数创建传入命令中任一缺失的父级目录。

```Shell
darkstar:~$ mkdir foo
darkstar:~$ mkdir /slack/foo/bar/
mkdir: cannot create directory `/slack/foo/bar/': No such file or directory
darkstar:~$ mkdir -p /slack/foo/bar/
```

在上面的例子中，我们创建了"/slack", 然后是"/slack/foo", 最后是"/slack/foo/bar". 如果没使用[-p]参数的话，那么就不能创建"/slack/foo/bar", 除非前两级目录存在。

删除和创建一样简单。`rm(1)`命令能删除一个文件（假设你有足够的权限）。有一些常用的参数。第一个就是[-f]参数，用来强行删除文件（但也可能因为缺少权限失败）。[-r]参数用来删除目录及其中的内容。

还有另一个命令用来删除目录，就是毫无存在感的`rmdir(1)`. `rmdir`只能删除空目录，如果其中含有文件或子目录的话会报错。

```Shell
darkstar:~$ ls
foo_1/ foo_2/
darkstar:~$ ls foo_1
bar_1
darkstar:~$ rmdir foo_1
rmdir: foo/: Directory not empty
darkstar:~$ rm foo_1/bar
darkstar:~$ rmdir foo_1
darkstar:~$ ls foo_2
bar_2/
darkstar:~$ rm -fr foo_2
darkstar:~$ ls
```
