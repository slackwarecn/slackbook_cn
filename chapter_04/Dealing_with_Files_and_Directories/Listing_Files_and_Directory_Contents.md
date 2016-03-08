#### 列出文件和目录内容

`ls(1)`用于列出文件和目录，及其权限、大小、类型、inode、所有者和组，还有很多其他信息。比如，列出Slackware的`/`目录：

```Shell
darkstar:~$ ls /
bin/   dev/  home/  lost+found/  mnt/  proc/  sbin/  sys/  usr/
boot/  etc/  lib/   media/       opt/  root/  srv/   tmp/  var/
```

注意，上面所有列出项都是目录。通过后面附带的`/`我们能够很容易地把它们和文件区分开（标准文件没有这个后缀）。此外，可执行文件会有一个星号的后缀。`ls`还能做到更多。要列出文件和目录的权限，你需要“长列表(long list)”：

```Shell
darkstar:~$ ls -l /home/alan/Desktop
-rw-r--r-- 1 alan users 15624161 2007-09-21 13:02 9780596510480.pdf
-rw-r--r-- 1 alan users  3829534 2007-09-14 12:56 imgscan.zip
drwxr-xr-x 3 alan root       168 2007-09-17 21:01 ipod_hack/
drwxr-xr-x 2 alan users      200 2007-12-03 22:11 libgpod/
drwxr-xr-x 2 alan users      136 2007-09-30 03:16 playground/
```

长列表能列出权限、用户和组所有权、文件大小、上次修改时间，以及文件名。注意，上面前两个列出项是文件，后三个是目录。这可以通过每行的第一个字母辨别出来。正常文件是一个`-`, 目录是一个`d`. 其他文件类型有各自的符号，比如符号链接是`l`.

最后，我要展示如何列出带点的文件，也就是隐藏文件。不像其他操作系统（比如Microsoft Windows）那样，没有专门用来标识“隐藏”和“非隐藏”的文件性质。隐藏文件名开头是一个点。要想把隐藏文件也显示出来，给`ls`传递[-a]参数。

```Shell
darkstar:~$ ls -a
.xine/    .xinitrc-backup  .xscreensaver  .xsession-errors  SBo/
.xinitrc  .xinitrc-xfce    .xsession      .xwmconfig/       Shared/
```

你可能注意到了你的文件和目录显示出来颜色是不一样的。通过给ls传递各种参数，就能打开它的各种功能，比如颜色输出，标注文件类型的后缀字符等等。方便起见，Slackware将`ls`设置为默认开启这些参数。可以通过`LS_OPTIONS`和`LS_COLORS`环境变量控制这些参数。我们将在第五章探讨这些环境变量。
