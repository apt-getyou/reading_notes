#nohup 使用方法

[原文](http://www.cnblogs.com/allenblogs/archive/2011/05/19/2051136.html)  

在应用Unix/Linux时，我们一般想让某个程序在后台运行，于是我们将常会用 `&` 在程序结尾来让程序自动运行。

比如我们要运行mysql在后台

```bash
 /usr/local/mysql/bin/mysqld_safe –user=mysql &
```

可是有很多程序并不想`mysqld`一样，这样我们就需要`nohup`命令，怎样使用`nohup`命令呢？这里讲解`nohup`命令的一些用法。

```bash
[~]# nohup /root/start.sh &
```

在shell中回车后提示：

```bash
[~]# appending output to nohup.out
```

原程序的的标准输出被自动改向到当前目录下的`nohup.out`文件，起到了log的作用，可以使用命令查看。

```bash
tail -f nohup.out
```

但是有时候在这一步会有问题，当把终端关闭后，进程会自动被关闭，察看`nohup.out`可以看到在关闭终端瞬间服务自动关闭。

> 注意：关闭终端时不能直接点击终端窗口上的关闭按钮，需要使用 `exit` 命令退出终端，否则会断掉该命令所对应的session，导致nohup对应的进程被通知需要一起shutdown。



> 附：
>
> nohup命令参考
>
> nohup 命令
>
> 用途：不挂断地运行命令。
>
> 语法：
>
> 描述：`nohup `命令运行由 Command 参数和任何相关的 `Arg` 参数指定的命令，忽略所有挂断（SIGHUP）信号。在注销后使用 nohup 命令运行后台中的程序。要运行后台中的 nohup 命令，添加 & （ 表示”and”的符号）到命令的尾部。
