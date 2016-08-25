linux grub2引导项因Windows重装而被覆盖后的解决方法
--

安装win7后，需要通过光盘来修复比较方便，如果不用盘也可以在win7系统中，硬盘启动ubuntu镜像，来进行修复操作，具体步骤如下，
从ubuntu9.10或者10.04或11.04版的安装光盘启动之后，进入终端，先在终端输入命令：
```bash
sudo fdisk -l
```
此步用于确定电脑中安装Ubuntu的所在分区的位置，输入以后会输出类似如下信息，找到ID为`83`的那行，记住`/dev/sdaX`的情况，比如本人的电脑是`/dev/sda3`，具体的自己更改

```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x30c230c1

Device Boot    Start       End    Blocks Id   System

/dev/sda1   *          63   101257694    50628816    7  HPFS/NTFS/exFAT
/dev/sda2       101257695   215046089    56894197+   7  HPFS/NTFS/exFAT
/dev/sda3       215046142   625137344   205045601+   f  W95 Ext'd (LBA)
/dev/sda5       215046144   250628095    17790976   83  Linux
/dev/sda6       250630144   266252287     7811072   82  Linux swap / Solaris
/dev/sda7       266254336   277970943     5858304   83  Linux
/dev/sda8       277972758   570982229   146504736    7  HPFS/NTFS/exFAT
/dev/sda9       570982400   625133567    27075584    7  HPFS/NTFS/exFAT
```

然后再输入
```bash
$ sudo -i
```
此步用于得到root权限，无需输入密码，方便以下操作

接着输入
```bash
#这里用于创建一个文件夹tempdir，用于挂载刚才的sda3，此文件夹名称你可以依个人爱好而定，没有太多要求
$ mkdir /media/tempdir
```


再输入
```bash
mount /dev/sda7 /media/tempdir #将sda3挂载于tempdir文件夹下
```

下面进入了本次恢复最为关键和激动人心的时刻，在终端输入以下命令：

```bash
grub-install --root-directory=/media/tempdir /dev/sda #本步骤用于来重新安装grub2到硬盘的主引导记录【MBR】里面，十分关键！
```

输入以后如果出现
`Installation finished.No Error Reported.`
字符的时候，就表示操作成功了。但是现在只成功的一半，还有以下操作才能够完全成功。

这时重新启动你的电脑，就能看到grub2的引导界面了，但是这时只能用来引导Ubuntu ，还暂时无法引导Windows 7，这时选择进入Ubuntu，再找到并启动终端，在终端输入如下命令：
```bash
sudo update-grub2
```

按照提示输入密码，如果顺利的话，会出现如下类似语句，那就表示成功了。
```
grub.cfg ...
Found Debian background: moreblue-orbit-grub.png
Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done
```

如果没有出现以上类似语句的话，那就在新立得里面搜索grub，可以安装带有Ubuntu标志的那个grub-pc，安装之后，再输入
```bash
sudo update-grub2
```
更新一下grub2就可以了。
