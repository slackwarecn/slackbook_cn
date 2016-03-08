#### 引导多个分区

在操作系统安装在各自分区的情况下，我们来配置多启动系统。您必须首先创建分区。如果在安装第一个操作系统之前就很好操作，在这种情况下，就是个简单的规划分区的事，使用`fdisk`或`cfdisk`分区工具，具体参见[“分区”部分](../../chapter_02/Partitioning.md)。

<div class="important" title="Important" style="margin-left: 0.5in; margin-right: 0.5in;"><h3 class="title">注意</h3><p>
    如果你搭建的是两个Linux的双系统，我们不推荐两个系统共用/home. 虽然这在技术上可行，但因为不同的桌面环境和软件版本，会增加你的个人配置文件损坏几率。
  </p><p>
    但共用交换分区是安全的。
  </p></div>

你应该至少给硬盘分三个区：

* Slackware一个分区

* 第二系统一个分区

* 交换分区

首先，按照[第二章，安装](../../chapter_02/README.md)所述，把Slackware安装到第一个分区。

安装好，启动好，一切正常之后，重启进入第二系统。第二系统总会想要占用整个驱动器，你显然*不希望*这样做，所以它限制为仅第二个分区。此外，该操作系统将尝试把引导器安装到硬盘驱动器的开头，覆盖LILO. 

有关引导器，可采取如下做法：

<div class="variablelist" title="Possible Boot Loader Scenarios"><p class="title"><b>
    可能的启动引导器方案
  </b></p><dl><dt><span class="term">
    如果第二系统是Linux, 禁止它安装启动管理器。
  </span></dt><dd><p>
      如果双启动进入另一Linux发行版，该发行版的安装程序通常会询问是否安装启动引导程序。你当然可以不安装引导程序，手动管理LILO来启动Slackware和另一发行版。
    </p><p>
      取决于另一发行版，比起只安装Slackware时你可能会更频繁地修改LILO配置。有些发行版因为频繁更新内核而臭名远扬，这就意味着每次更新你都要修改LILO配置。但如果你不想时时修改配置文件，你就不会选择Slackware了。
    </p></dd><dt><span class="term">
      如果第二系统是Linux，让它用GRUB来替换LILO
  </span></dt><dd><p>
      如果双启动进入另一Linux发行版，你完全可以用GRUB来替换LILO, 或最后安装Slackware并都使用LILO. LILO和GRUB都有自动检测的特性，所以不管最后安装的是谁都要探测其他发行版的存在并为它创建一个启动条目。
    </p><p>
      由于其他的发行版往往会自动更新他们的GRUB菜单，总有可能出点差错然后就无法启动Slackware了。发生这种情况，不要惊慌，进入其它Linux的分区，手动修改GRUB菜单的Slackware条目使之指向正确的分区，内核和initrd（如果适用的话）。
    </p></dd><dt><span class="term">
      让第二系统替换掉LILO并在之后重新安装并配置LILO
  </span></dt><dd><p>
      这个选择也是可行的，尤其是第二系统是Windows的时候。经常Windows更新之后会重写MBR, 这时候就要手动重新安装LILO了。
    </p><p>
      要在其他系统抹除LILO之后修复，启动Slackware安装介质进入配置阶段。*不要*重新分区或重新安装Slackware, 直接跳到<a href="../../chapter_02/The_setup_Program/Configure.md" target="_blank" rel="external">“配置”部分</a>。
    </p><p>
      使用简单模式LILO的时候，它也会自动探测并创建启动菜单。如果失败了，那么就需要手动创建条目了。
    </p></dd></dl></div></div>
