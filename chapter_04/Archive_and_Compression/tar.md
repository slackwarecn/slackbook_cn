#### tar

我们已经看到了几个压缩工具，但是没有一个能像zip那样打包的。然而现在有了。tar(1)是Slackware上用的最多的打包程序。和其他打包程序一样，tar生成一个新的文件来包含其它文件和目录。它默认不会对生成的文件进行压缩，但是Slackware中包含的tar支持多种压缩方式，包括前面提到的。  

你可以通过简单或者负责的参数来使用tar。通常，我们用[-cvzf]来创建一个tar包，下面来深度的了解一下：   

__Table 4.2 tar 参数__  

|参数|解释|
|:---|---:|
|c|创建一个tar包|
|x|从tar包中提取内容|
|t|显示tar包的内容|
|v|显示更详细的信息|
|z|用gzip来压缩|
|j|用bzip2来压缩|
|J|用LZMA来压缩|
|p|保留权限|  

tar相对其他软件来说，对参数的顺序要求更精确。当读和写文件时[-f]参数是必须的，并且后面的参数必须是一个文件名。看看下面的例子：  
```plain
darkstar:~$ tar -xvzf /tmp/tarball.tar.gz
darkstar:~$ tar -xvfz /tmp/tarball.tar.gz
```
上面的第一行命令会如你所愿，但是第二行会失败，因为tar被告知打开z文件而非/tmp/tarball.tar.gz。  

既然我们给出了tar的参数，那么就在看几个例子来了解怎样创建和提取tar包。下面的命令会创建一个tar包，并且使用gzip压缩算法来压缩。虽然不是强制要求，但是添加.tar后缀及压缩算法是个好习惯。  
```plain
darkstar:~$ tar -czf /tmp/tarball.tar.gz /tmp/tarball/
```
