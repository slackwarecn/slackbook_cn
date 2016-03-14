### 从命令行打印

现在，你已经成功地安装并配置你的打印机。你可以使用`lpr`来从命令行打印。

`lpr`发送文档到打印机以完成打印，不过在此之前，你也许想要先使用root运行`lpadmin`以定义一个默认打印机：
```
# lpadmin -d r1060
```

在这个例子中，`r1060`是配置在`/etc/cups/printers.conf`的名字或在CUPS的配置中的名字。

**注意**

如果你没有root权限，你可以配置PRINTER环境变量：
```
$ PRINTER=r1060
$ export PRINTER
```

一旦打印机被设置完成，你就可以这样打印：
```
$ lpr foo.txt
```
