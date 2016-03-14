### 在CUPS中设置打印机

从这里开始，设置一个打印机只需要按照一系列的提示一步一步配置。但了解打印配置的实际工作也许能帮助你了解CUPS都做了什么。

`/etc/cups/printers.conf`文件是由你的计算机能访问的打印设备的详细定义构成，其中标记了一个默认设备。如果你想手动编辑这个文件，你需要先停止`cupsd`守护进程。

在文件中，一个典型的条目看起来就像这样：
```
<Printer r1060>
    Info Ricoh 1060
    Location Downstairs
    MakeModel Ricoh Aficio 1060 - CUPS+Gutenprint v5.2.6
    DeviceURI lpd://192.168.4.8
    State Idle
    StateTime 1316011347
    Type 12308
    Filter application/vnd.cups-raw 0 -
    Filter application/vnd.cups-raster 100 rastertogutenprint.5.2
    # standard-ish stuff below here
    Accepting Yes
    Shared No
    JobSheets none none
    QuotaPeriod 0
    PageLimit 0
    KLimit 0
    OpPolicy default
    ErrorPolicy stop-printer
</Printer>
```

本例中，我们的打印机名称是`r1060`，便于阅读的标记名叫Ricoh 1060。
我们可以使用`lpinfo`获取型号信息，这个命令列出了你系统上所有可用的打印驱动。所以，如果你知道你的系统有一台Ricoh 1060设备并希望输出它，那么你可以以root权限发出命令：

```
darkstar:~# lpinfo -m | grep 1060
```

此命令列出了所有已安装的驱动后，使用grep查找有字符串`1060`的行：

```
gutenprint.5.2://brother-hl-1060/expert Brother HL-1060 - CUPS+Gutenprint v5.2.6
gutenprint.5.2://ricoh-afc_1060/expert Ricoh Aficio 1060 - CUPS+Gutenprint v5.2.6
```

型号信息是结果的后半部分。在这个输出中，型号是Ricoh Aficio 1060 - CUPS+Gutenprint V5.2.6。

访问打印机至关重要的入口是设备URI(统一资源标识符)，或者是网络地址，或物理地址，如USB端口，通过这些东西使设备能被找到。在这个例子中，我们使用设备URI是[lpd://192.168.4.8](lpd://192.168.4.8)，`lpd://`开头是因为我们要使用LPD协议将数据发送到打印机。

到现在，你应该明白了你真正在配置的是什么。你现在可以使用更普遍、更容易的方式从浏览器访问配置工具来做这些事。

在CUPS的界面中，选择管理标签，选择“添加打印机”。在这一步你应该会被要求输入管理员密码以授权。

然后，你将会被要求在列表中为你的打印机选择一个打印机接口和协议。在大多情况下，你的打印机应使用LPD/LPR协议（除非你知道你的打印机需要其他的协议）。

注意，如果你的打印机已经被接入了你的计算机，并且已启动，你应该能看到它被作为本地打印机列出来。

如果你的打印机是联网的，下一个界面将会询问你打印机的地址。请使用`lpd://`协议，输入你打印机的IP地址。如果你不知道打印机的IP地址，你可能需要查看打印机的设置，或者从路由器中确认它的地址。

无论你的打印机通过USB还是网络连接，下一个界面都会询问你关于打印机可读性（human-readable）的细节。这仅仅是作为您的参考。然后，输入您打印机的名称（通常是型号）和描述（如果您不止有一个打印机的话），还有位置（放在在哪里）。

在下一个界面，你需要为CUPS选择打印机驱动。如果你的打印机是PostScript打印机（大多数激光打印机都是），那么你的打印机只需要一个PPD文件。如果你的打印机不是PostScript打印机或者有特殊功能需要额外的驱动，那么你需要选择你打印机的制造商，然后你将会看到可用驱动程序的列表，在这选择合适的驱动程序。

现在，你的打印机已经安装完成并被设置为你所有应用程序的默认打印设备。