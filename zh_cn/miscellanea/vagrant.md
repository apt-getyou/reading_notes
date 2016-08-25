vagrant 部分问题解决方法
--


1. Vagrant 启动失败,停留在 Waiting for VM to boot 的解决方法

  用 VirtualBox面板运行该系统，在GRUB界面回车登录系统，用户名：vagrant，密码：vagrant，编辑 `/etc/grub.d/00_header`，找到：
  ```bash
   if [ "${recordfail}" = 1 ]; then  
    set timeout=-1
  ```

  将 -1 改成 10 即可：

  ```bash
  if [ "${recordfail}" = 1 ]; then  
    set timeout=10
  ```

  再运行  `update-grub` 更新 GRUB，关机后再用 `vagrant up` 启动就能正常启动了。

1. 开启 NFS 文件系统提升 Vagrant 共享目录的性能  

  Vagrant 默认的 VirtualBox 共享目录方式读写性能表现并不好，好在 Vagrant 支持 NFS 文件系统方式的共享，我们可以启用 NFS 提升性能。

  开启方法

  首先要把虚拟机的网络设置成 :private_network 模式。

  然后确认宿主机系统是否安装了 nfsd，Mac OS X 默认是集成了的，部分 Linux 需要安装对应 package 才能支持（以 Ubuntu 为例）：
  ```bash
  $ sudo apt-get install nfs-kernel-server nfs-common
  ```
  同时，虚拟机里的系统也要安装对应的 package：

  ```bash
  $ sudo apt-get install nfs-common
  ```
  接下来编辑配置文件 Vagrantfile，将共享的目录 nfs 设置为 true，如下：

  ```ruby
  Vagrant.configure("2") do |config|
    # ...
    config.vm.synced_folder ".", "/vagrant", :nfs => true
  end
  ```
  保存后，使用命令 vagrant reload 重启虚拟机后才会生效，期间会修改宿主计算机的 /etc/exports 文件，因此可能要你输入密码，而且每次启动都要会求输入，稍微有点麻烦。
