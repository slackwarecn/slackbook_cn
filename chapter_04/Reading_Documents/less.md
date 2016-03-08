#### less

为了克服more的缺点，一个新的分页程序被开发出来，并且是具有讽刺意味的less(1)。less是一个更高端的分页程序，它提供了所有more的功能，以及其它的特性。less允许你在文档中使用方向键来移动。  

Slackware为less提供了一个便利的预处理器lesspipe.sh。它允许用户对一些非文本文件使用less。lesspipe.sh会运行文件将产生的文本输出在less中显示。  

less提供了接近文本编辑器的功能。可以使用vi风格的j和k或者用方向键或是ENTER来一行一行的移动。如果文本太宽的话，你还可以用方向键来水平滚动。g键回到第一行，G键回到最后一行。  

可以使用more的方式进行搜索，但是结果会高亮显示，n键带到下一个结果，N返回上一个搜索结果。  

和more一个，文件可以直接有它打开或者由管道传递给它：  
```plain
darkstar:~$  less
/usr/doc/less-*/README
darkstar:~$  cat
/usr/doc/less*/README
/usr/doc/util-linux*/README | less
```

less还有更多的东西，在程序中按h会得到完整的命令列表。
