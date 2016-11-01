#awk 和 xargs 的联合使用

- 目标

  实现批量操作

- 命令简单说明
  - __awk__:  
    就是把文件逐行的读入，以空格为默认分隔符将每行切片，切开的部分再进行各种分析处理  
  - __xargs__:  
    将参数列表转换成小块分段传递给其他命令，以避免参数列表过长的问题  

* 具体场景
  在使用docker构建或者拉取镜像时，经常容易生成镜像名称和TAG名称为`<none>`的镜像，我们可以用命令
  ```bash
   ➜  ~ docker images
  ```
  查看到类型与下面这种情况
  ```bash  
   REPOSITORY              TAG                 IMAGE ID            CREATED             SIZE
   rediscluster_sentinel   latest              a72dce3e251f        2 weeks ago         182.9 MB
   <none>                  <none>              00251933c20d        2 weeks ago         182.9 MB
   <none>                  <none>              6339f3627bb4        3 weeks ago         182.9 MB
   <none>                  <none>              a7597de53808        3 weeks ago         182.9 MB
   <none>                  <none>              3359ef556427        3 weeks ago         182.9 MB
   <none>                  <none>              53d04000f367        3 weeks ago         182.9 MB
   redis                   3                   1aa84b1b434e        5 weeks ago         182.9 MB
   rabbitmq                3-management        ed992ccc4335        5 weeks ago         178.7 MB
   rancher/server          latest              0a18f1c0ead2        10 weeks ago        843 MB
   rancher/agent           v1.0.2              860ed2b2e8e3        4 months ago        454.3 MB
  ```
   对于这种情况我们可以选择使用`docker rmi <IMAGE ID>`删除对应的镜像，但这无疑是效率不高的操作，对此我们可以选择使用 `awk` 和 `xargs` 命令进行批量删除。
   首先我们先使用`grep`选出需要删除的镜像

  ```bash
  docker images | grep '<none>'
  ```

  效果如下

  ```bash
  <none>                  <none>              00251933c20d        2 weeks ago         182.9 MB
  <none>                  <none>              6339f3627bb4        3 weeks ago         182.9 MB
  <none>                  <none>              a7597de53808        3 weeks ago         182.9 MB
  <none>                  <none>              3359ef556427        3 weeks ago         182.9 MB
  <none>                  <none>              53d04000f367        3 weeks ago         182.9 MB
  ```

  但我们只需要images id 作为删除镜像的参数，我们需要使用`awk `  和 `$`  继续选择

  ```bash
  docker images | grep '<none>' | awk '{print $3}'
  ```

  得到 images id 列表

  ```bash
  00251933c20d
  6339f3627bb4
  a7597de53808
  3359ef556427
  53d04000f367
  ```

  其中 `$` +　number 表示取第几列数据。

  得到images id 列表后我们就可以使用`xargs` 命令将这些id作为参数传入`docker rmi`

  所以最终命令为

  ```bash
  docker images | grep '<none>' | awk '{print $3}' | xargs docker rmi
  ```

  同样，也可以按这套思路写一个批量删除已退出的docker容器

  ```bash
  docker ps -a | grep 'Exited' | awk '{print $1}' | xargs docker rm
  ```

  ​
