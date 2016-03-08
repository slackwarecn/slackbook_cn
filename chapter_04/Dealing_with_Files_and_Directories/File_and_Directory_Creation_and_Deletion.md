#### 文件和目录的创建与删除

大多数软件都可以并且会创建它们自己的文件和目录，你也可以办到，并且很简单，用touch(1)和mkdir(1)就行！  

touch实际上只是修改文件的时间戳，如果这个文件不存在的话，它才创建文件。  
```plain
darkstar:~/foo$ ls -l
-rw-r--r-- 1 alan users 0 2012-01-18 15:01 bar1
darkstar:~/foo$ touch bar2
-rw-r--r-- 1 alan users 0 2012-01-18 15:01 bar1
-rw-r--r-- 1 alan users 0 2012-01-18 15:05 bar2
darkstar:~/foo$ touch bar1
-rw-r--r-- 1 alan users 0 2012-01-18 15:05 bar1
-rw-r--r-- 1 alan users 0 2012-01-18 15:05 bar2
```  
可以看到bar2由第二个命令创建，而第三个命令只修改了bar1的时间戳。  

mkdir顾名思义，是用来创建目录的。`mkdir foo`会在当前目录下创建一个名为"foo"的目录。另外，你也可以使用[-p]参数来创建这个目录的父目录。  
```plain
darkstar:~$ mkdir foo
darkstar:~$ mkdir /slack/foo/bar/
mkdir: cannot create directory `/slack/foo/bar/': No such file or directory
darkstar:~$ mkdir -p /slack/foo/bar/
```  
最后一行命令会先创建"/slack"，然后是"/slack/foo"，最后才是"/slack/foo/bar"。如果你没有使用[-p]参数的话，就会出现第二行命令的错误，除非前面的两个目录已经存在了。  

删除一个文件和创建它一样简单，只需要使用rm(1)命令就可以删除文件了（假设你有相应的权限）。rm有几个常用的参数，其中[-f]被用来强制删除一个文件，[-r]则用来递归的删除目录及其内容。  
```plain
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
