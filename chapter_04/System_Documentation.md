### 系统文档

你的Slackware系统几乎针对每个应用程序都附带了大量内置文档。最常见的阅读系统文档的方式是`man(1)`. 调用`man`(manual的缩写) 会输出所有现有的程序，系统调用，配置文件，以及库的手册页（man-page）。比如，`man man`输出`man`自己的手册页。

不过，你不可能总是知道哪个任务该用什么程序来完成。还好，man内置搜索功能。使用[-k]参数就能让`man`在所有手册页中搜索给定的关键词。

手册页根据内容的类型被分为几组(group)或部分(section)。比如，section 1是用户程序部分。man会按顺序搜索每个section并输出第一个匹配项。有时你会发现某个条目的手册页出现在不止一个section里。这时，你就要指定搜索的范围。本书中，所有的程序和部分内容会在它右边附带一个括起来的数字，这个数字就是你要给`man`指定的搜索范围。

```Shell
darkstar:~$ man -k printf
printf               (1)  - format and print data
printf               (3)  - formatted output conversion
darkstar:~$ man 3 printf
```

手册页section列表

|Section|内容|
|:-------:|----:|
|1|用户命令|
|2|系统调用|
|3|C语言库调用|
|4|设备|
|5|文件格式/协议|
|6|游戏|
|7|约定/宏包|
|8|系统管理工具|
|9|内核API描述|
|n|"New"——通常用于Tcl/Tk|
