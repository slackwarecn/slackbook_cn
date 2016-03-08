#### more

`more`会从第一行开始读取只到屏幕充满，然后停止。看完当前内容后，可以按**ENTER**来接着读取下一行，或是按**SPACE**来另外一屏幕的内容，或是输入想要读取的行数再按**SPACE**。`more`也能在文件中搜索关键词，在`more`中打开文件后，输入**/**再输入关键词，再按下**ENTER**, 文件会滚到第一次发现关键词的地方。

这是对`cat`的一次重大改进，但依然有一些缺点：`more`不能回滚，搜索功能不能高亮搜索到的关键词，不能横向滚动，等等。我们急需一个解决方案。

<div class="note" title="Note" style="margin-left: 0.5in; margin-right: 0.5in;"><h3 class="title">注意</h3><p>
    实际上，现代版本的<code>more</code>, 比如Slackware附带的，确实有一个<i>返回</i>功能（输入<strong>b</strong>键），但只支持<code>more</code>直接打开文件的方式，<code>more</code>通过管道打开的文件是不支持的。
  </p></div>
