#### zip、unzip

你应该对`.zip`文件非常熟悉了。这是含有其他文件或目录的压缩文件。虽然在Linux世界中我们通常不使用zip文件，但它们在其他系统里广为使用，所有我们时不时会有处理它的需要。

要创建一个zip文件，你需要（废话）使用`zip(1)`命令。你能用`zip`压缩文件、目录、或文件和目录。你需要使用[-r]参数来递归处理目录。

```Shell
darkstar:~$ zip -r /tmp/home.zip /home
darkstar:~$ zip /tmp/large_file.zip /tmp/large_file
```

参数的顺序非常重要。第一个文件名必须是要创建的zip文件（如果没有`.zip`扩展名，zip会自动加上），另外的是待压缩的文件。

自然，`unzip(1)`是解压zip文件的工具。

```Shell
darkstar:~$ unzip /tmp/home.zip
```
