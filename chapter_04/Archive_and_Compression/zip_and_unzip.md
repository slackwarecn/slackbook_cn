#### zip、unzip

你可能对.zip文件很熟悉，它包含了许多压缩后的文件和目录。虽然在Linux世界中我们一般不用它，但是zip文件在其他操作系统中仍在普遍的使用，所以我们还是偶尔会遇到它。   

要创建zip文件可以使用zip(1)命令。你可以用zip来压缩文件或者目录甚至两者都行，但是，这时需要用[-r]参数来递归的处理目录。  
```plain
darkstar:~$ zip -r /tmp/home.zip /home
darkstar:~$ zip /tmp/large_file.zip /tmp/large_file
```  
参数的顺序很重要！第一个文件名必须是要创建的zip文件（如果没有提供.zip后缀，程序会为你加上）之后的是要添加到zip文件中的文件或者目录。  

自然的，unzip(1)使用来解压zip压缩文件的：  
```plain
darkstar:~$ unzip /tmp/home.zip
```  
