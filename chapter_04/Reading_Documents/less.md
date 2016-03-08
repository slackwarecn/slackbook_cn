#### less

为了克服`more`的缺点，一个新的pager诞生了，针锋相对地起名为`less(1)`. `less`是一个非常强大的pager，除了支持more的所有功能以外还有一些其他特性。比如，`less`允许使用方向键来控制。

因为它相当受欢迎，许多Linux发行版将`more`排除在外来支持`less`. Slackware两个都有。另外，Slackware有一个`less`的预处理器`lesspipe.sh`. 它能让用户在一些非文本文件上执行`less`. `lesspipe.h`在传入文件后会生成文本输出，并在`less`内显示。

`less`几乎有文本编辑器的所有功能，除了文本编辑以外。支持vi风格的逐行移动（使用**j**和**k**），方向键移动，以及**ENTER**. 如果文件一行太长屏幕装不下，还能横向滚动。**g**可回滚到文件开头，**G**跳转到末尾。

搜索功能和`more`一样，按**/**完成，不过搜索结果会高亮显示。输入**n**会跳转到下一个匹配，**N**到上一个。

与`more`一样，也能通过管道打开文件：

```Shell
darkstar:~$  less
/usr/doc/less-*/README
darkstar:~$  cat
/usr/doc/less*/README
/usr/doc/util-linux*/README | less
```

`less`还有更多功能等待发现，只需输入**h**.
