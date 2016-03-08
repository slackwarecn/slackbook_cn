#### 列出文件和目录内容

ls(1)用来列出文件、目录、权限、大小、类型、i节点号，以及用户和组和其它的信息。例如，让我们来列出/目录下的东西：  
```plain
darkstar:~$ ls /
bin/   dev/  home/  lost+found/  mnt/  proc/  sbin/  sys/  usr/
boot/  etc/  lib/   media/       opt/  root/  srv/   tmp/  var/
```  
注意到上面列出的东西都是目录，由于它们都由后缀/结束，所以很容易和普通文件去分开；标准的文件是没有后缀的。此外，可执行文件会有星号后缀。当然我们还可以通过ls获得更多的东西，比如，获取文件和目录的权限：  
```plain
darkstar:~$ ls -l /home/alan/Desktop
-rw-r--r-- 1 alan users 15624161 2007-09-21 13:02 9780596510480.pdf
-rw-r--r-- 1 alan users  3829534 2007-09-14 12:56 imgscan.zip
drwxr-xr-x 3 alan root       168 2007-09-17 21:01 ipod_hack/
drwxr-xr-x 2 alan users      200 2007-12-03 22:11 libgpod/
drwxr-xr-x 2 alan users      136 2007-09-30 03:16 playground/
```  
注意到上面使用了[-l]参数，使用这个参数，我们获得了权限、用户和组、文件大小、最后修改日期以及文件本身。另外，上面结果中的前两行是文件，剩下的三个则是目录。这可以由它们最前面的第一个字符区分，普通文件是'-'目录是'd'；当然还有些其他的字符，例如符号链接的是'l'。   

最后，我们展示怎样列出隐藏文件。和Windows操作系统不同，由于没有特殊的属性来区分“隐藏”和“非隐藏”文件，所以Slackware中以点'.'开头的文件就是隐藏文件。要显示这些隐藏文件，我们可以将[-a]参数传递个ls：  
```plain
darkstar:~$ ls -a
.xine/    .xinitrc-backup  .xscreensaver  .xsession-errors  SBo/
.xinitrc  .xinitrc-xfce    .xsession      .xwmconfig/       Shared/
```  

你很可能注意到了文件个目录拥有不同的颜色。许多ls的增强功能，像这样的颜色或显示文件类型的特性后缀由通过向ls传递各种参数来开启的。为了方便，Slackware默认设置了许多可选的参数。这些东西是由LS_OPTIONS和LS_COLORS环境变量控制的。我们将在第五章谈到更多有关环境变量的东西。  
