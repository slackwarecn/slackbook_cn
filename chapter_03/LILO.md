### LILO

LILO是一种Linux引导器，并且目前是Slackware的默认引导器。如果你之前用过其他Linux发行版，你应该听说过GRUB. 如果你更喜欢GRUB的话。前往Slackware CD的`/extra`就能找到它。由于LILO是Slackware的默认引导器，在此我们还是得重点研讨它。

对新手来说配置LILO可能有点难，所以Slackware附带了个配置工具叫`liloconfig`. 正常来说`liloconfig`的第一次运行是安装程序自动完成的，不过你也随时可以在终端里调用它。

![ ](http://slackbook.org/beta/png/setup-lilo.png)

`liloconfig`有两种操作模式：简单模式和专家模式。简单模式会自动为您配置好LILO. 如果Slackware是你电脑上的唯一系统，简单模式就能快速、正确地完成配置。当然它也能探测Windows系统并将其添加到`/etc/lilo.conf`, 这样你开机的时候就能选择启动哪个系统。

要想使用专家模式的话，你需要知道Slackware的根分区位置。你也可以设置为其他Linux发行版的根分区，但我们不保证能正确运行：liloconfig会尝试使用Slackware的内核来启动该Linux系统，这应该不是你希望的结果。不过，在专家模式下配置Windows分区倒是简单。我们给出一条专家模式下的建议：把LILO装在主引导记录（MBR）上。以前，我们会建议把LILO装在根分区上并将该分区设为可引导分区；现在，LILO已经足够成熟，能安全地安装在MBR上了。实际上，这么做的话你碰到的问题会更少。

`liloconfig`是能快速地配置好引导器，但如果你想知道究竟发生了什么的话，你需要看看LILO的配置文件：`/etc`下的`lilo.conf(5)`. `/etc/lilo.conf`分为了几个部分。最上面你能找到全局部分，这部分描述LILO应安装在何处（一般是MBR），启动时显示的图像或信息，启动默认操作系统的等待时长。以下是我的`lilo.conf`的全局部分，长这样：

```fundamental
# LILO configuration file

boot = /dev/sda
  bitmap = /boot/slack.bmp
  bmp-colors = 255,0,255,0,255,0
  bmp-table = 60,6,1,16
  bmp-timer = 65,27,0,255

append=" vt.default_utf8=0"
prompt
timeout = 50

# VESA framebuffer console @ 1024x768x256
vga = 773
.... many more lines ommitted ....
```

完整的LILO参数详见`lilo.conf`的手册页。在此文档中我们将简要地讨论一些常用选项。

首先应该注意的就是"boot"一行。它决定引导器安装位置。要安装到MBR上的话，填上对应硬盘设备条目就好。在上面的例子中，我所用的SATA硬盘显示为SCSI设备`/dev/sda`. 要安装到分区的引导区块中，还得附加上分区设备条目。比如，要安装到电脑唯一的SATA硬盘的第一个分区上，就该写`/dev/sda1`.

"prompt"选项让LILO询问你该引导哪一个系统。每个操作系统都在LILO配置文件的后半部分列出（这一内容将在后文中探讨）。timeout选项告诉LILO启动默认操作系统前的等待时长（单位：0.1秒）。在上面的例子中是5秒。有些系统显示启动屏幕需要很长时间，这时候就需要设置个大点的timeout. 这就是为什么简单的LILO安装方法设置了很长的timeout（有时甚至长达2分钟）。上面的例子中，append那一行由liloconfig自动配置。你能（并且应该）在自己的`/etc/lilo.conf`看到类似的内容。在此不会深入探讨为什么需要这一行，你只需要记住有这一行比没有好就行了。:^)

接下来看看操作系统部分。每个Linux操作系统的配置以"image"配置行开头。Microsoft Windows操作系统以"other"配置行开头。现在让我们来看看Slackware和Windows各自的配置样例。

```fundamental
# LILO configuration file
... global section ommitted ....
# Linux bootable partition config begins
image = /boot/vmlinuz-generic-2.6.29.4
  root = /dev/sda1
  initrd = /boot/initrd.gz
  label = Slackware64
  read-only
# Linux bootable partition config ends
# Windows bootable partition config begins
other = /dev/sda3
  label = Windows
  table = /dev/sda
# Windows bootable partition config ends
```

对于像Slackware这样的Linux操作系统，image配置项规定了要启动的内核。在这个例子中，要启动的内核是`/boot/vmlinuz-generic-2.6.29.4`. 其余的几个配置项看名字就可知道作用：它们告诉LILO根分区的位置，使用哪个`initrd`文件，把根文件系统挂载为只读。`initrd`配置项对于那些使用通用内核，或使用LVM和软件RAID的人十分重要。它告诉LILO(以及内核)在哪找到使用`mkinitrd`创建的`initrd`.

配置好`/etc/lilo.conf`后，运行`lilo(8)`来安装。不像GRUB和其他引导器那样，在更改配置文件之后需要重新运行lilo, 不然新修改的引导器镜像不会被安装，所做出的修改不会生效。

```Shell
darkstar:~# lilo
Warning: LBA32 addressing assumed
Added Slackware *
Added Backup
6 warnings were issued.
```

看见这些警告不必太惊慌，这些并不代表lilo出了问题，除非发现了致命错误。另外，LBA32 addressing 的警告是常有的事。
