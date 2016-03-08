#### tar

我们已经知道了如何压缩单个文件，但没有一个能像`zip`那样打包文件的。但这到此为止。Tape Archiver, 或`tar(1)`, 就是Slackware最常用的打包工具。像其他打包工具那样，`tar`生成一个包含其他文件和目录的文件。它默认不压缩生成的文件（通常又叫"tarball"），不过Slackware所带的版本支持各种压缩方案，包括上面提到的那几种。

使用`tar`可以简单也可以复杂，随你喜好。一般，生成tarball要使用参数[-cvzf]. 我们来深入地看看：

|参数|意义|
|:----:|----:|
|c|创建tarball|
|x|解压tarball|
|t|显示tarball内容|
|v|输出更多信息|
|z|使用gzip压缩方案|
|j|使用bzip2压缩方案|
|J|使用LZMA压缩方案|
|p|保留权限信息|

`tar`对于参数的顺序要求比别的程序更严格。[-f]参数当读或写入文件时必须出现，并且紧跟其后的必须是文件名。看看这个例子：

```Shell
darkstar:~$ tar -xvzf /tmp/tarball.tar.gz
darkstar:~$ tar -xvfz /tmp/tarball.tar.gz
```

上面，第一个命令能够正常运行，第二个会失败因为tar会尝试打开文件`z`而不是`/tmp/tarball.tar.gz`.

既然我们已经充分了解了参数的意义，来让我们看看如何创建和解压tarball. 前面已经说过，[-c]参数用来创建而[-x]用来解压。如果想创建或解压一个压缩过的tarball, 我们需要指定合适的压缩方案。自然，如果不想压缩文件也可以不填。下面的这个命令使用gzip算法创建并压缩一个tarball. 尽管没有严格要求，但还是加上`.tar`的扩展名以及所使用的压缩算法为最好。

```Shell
darkstar:~$ tar -czf /tmp/tarball.tar.gz /tmp/tarball/
```
