#### gzip

Slackware所附带的最古老的压缩工具就是`gzip(1)`了。它一次只能处理一个文件。与`zip`能够压缩和打包不同，`gzip`只能压缩。你第一感觉这是个缺点，但实际上这是它的强大之处。UNIX的哲学之一就是让程序只做一件事并做到最好。这就让程序们能以无限多的组合方式来完成工作。要想压缩一个（或多个）文件，只需将它们作为参数传递给`gzip`.

```Shell
darkstar:~$ gzip /tmp/large_file
```

解压就使用`gunzip`, 它会解压出文件并删除原来的压缩文件。

```Shell
darkstar:~$ gunzip /tmp/large_file.gz
darkstar:~$ ls /tmp/large_file*
/tmp/large_file
```

但如果我们不希望删除压缩文件，只想查看内容的话怎么办？`zcat`程序能读取`gzip`文件，解压到内存并将内容传输到标准输出（也就是终端屏幕，除非使用了重定向。重定向详见“[输入输出重定向](../../chapter_05/Input_and_Output_Redirection.md)”）。

```Shell
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
