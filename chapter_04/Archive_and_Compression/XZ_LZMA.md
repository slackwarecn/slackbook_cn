#### XZ、LZMA

最新加入Slackware的压缩工具就是`xz`, 它使用的是LZMA压缩算法。它比`bzip2`更快并且压缩效果更好。实际上，它因为在速度和压缩效果上出色的综合表现，已经成为Slackware的首选压缩方案了。不过，`xz`在我们成书之时还没有手册页，所以要查看所有选项，使用[--help]参数。压缩使用[-z], 解压使用[-d].

```Shell
darkstar:~$ xz -z /tmp/large_file
```
