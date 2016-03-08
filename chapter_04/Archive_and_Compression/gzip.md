#### gzip

Slackware中最古老的压缩程序之一是gzip(1)，gizp是一个一次只操作一个文件的压缩工具。然而，zip包含了打包和压缩两者,gzip只能用来压缩。虽然看起来有些缺陷，但是Unix哲学就是小而美啊。要压缩一个或多个文件，只需将它们作为参数传递给gzip即可。注意，当gzip压缩文件时会为文件添加.gz后缀，然后删除原文件！  
```plain
darkstar:~$ gzip /tmp/large_file
```  
同样的，我们可以使用gunzip来解压.gz文件，gunzip会在解压后删除原来的.gz文件：  
```plain
darkstar:~$ gunzip /tmp/large_file.gz
darkstar:~$ ls /tmp/large_file*
/tmp/large_file
```  

但是假如我们不想删除旧的压缩文件，只是想查看它的内容或者将它作为其它程序的输入怎么办呢？我们可以使用zcat命令来读取gzip文件，在内存中解压然后将其内容输出到标准输出。  
```plain
darkstar:~$ zcat /tmp/large_file.gz
Wed Aug 26 10:00:38 CDT 2009
Slackware 13.0 x86 is released as stable!  Thanks to everyone who helped
make this release possible -- see the RELEASE_NOTES for the credits.
The ISOs are off to the replicator.  This time it will be a 6 CD-ROM
32-bit set and a dual-sided 32-bit/64-bit x86/x86_64 DVD.  We're taking
pre-orders now at store.slackware.com.  Please consider picking up a copy
to help support the project.  Once again, thanks to the entire Slackware
community for all the help testing and fixing things and offering
suggestions during this development cycle.
```  
