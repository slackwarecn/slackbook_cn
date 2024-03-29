### 多重引导

引导程序（比如 LILO）是一个非常灵活的东西，因为它的存在只是为了确定要启动分区中的哪一个硬盘，分区，甚至内核。我们很自然就能推出，安装了多系统的用户一定是一个 LILO 或 GRUB 用户。

出于各种原因，人们需要“多启动”：一些人希望在在某个分区或驱动器有一个稳定的 Slackware 系统，并在另一位置有个开发用沙盒，其他人可能想同时体验 Slackware 和其他 Linux 或 BSD 发行版，还有一些人一个分区装 Slackware，另一分区装闭源系统（为了工作或某些 Linux 没有的程序）。

多启动不应该掉以轻心，但它通常意味着你将有两个不同的试图管理引导程序的操作系统。如果你多启动，很可能一个操作系统会覆盖或更新引导程序条目。如果这种情况发生，你必须手动修改 GRUB 或 LILO 来引导这些操作系统。

有两种方法来双（多）启动：你可以把每个操作系统安装在不同的硬盘上（台式机常见，因为台式机有很多硬盘位）或安装在不同分区上（笔记本电脑常见，因为只有一个物理驱动器）。
