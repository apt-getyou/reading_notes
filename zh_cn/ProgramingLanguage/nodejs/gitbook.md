# GitBook 简介

GitBook 是一个通过 Git 和 Markdown 来撰写书籍的工具，最终可以生成 3 种格式：

静态站点：包含了交互功能（例如搜索、书签）的站点  
PDF：PDF 格式的文件  
eBook：ePub 格式的电子书文件  
GitBook 是免费且开源的，[项目地址](https://github.com/GitbookIO/gitbook)  
此文档只是对gitbook的简介,具体信息可查看官方文档 [官方文档地址](http://gitbook.chenxiayu.cn/zh/index.html)


## gitbook-cli
宿舍
需要先安装gitbook-cli，这个工具是用来管理gitbook工具的，这有点类似容器的意思，通过gitbook-cli可以在本地安装多个gitbook工具的不同版本。

使用如下命令安装GitBook。
```bash
 $ npm install gitbook-cli -g
```

安装完之后，你可以检验下是否安装成功。

```bash
$ gitbook -V
```

安装gitbook
安装完gitbook-cli后，要使用gitbook还需要安装gitbook工具，可以通过如下命令安装。

```bash
$ gitbook versions:install
```
安装好后可以通过如下命令查看是否安装成功。

```bash
$ gitbook versions
```
都安装好后接下来我们就可以做点有意思的事情了。

## 常用命令
再开始做有意思的事情之前，先来熟悉下常用命令。

- gitbook-cli常用命令  

  ```bash
  $ gitbook -h # 查看帮助信息  
  $ gitbook versions # 查看本地安装的gitbook版本  

  $ gitbook versions:install # 安装最新版gitbook  
  $ gitbook versions:install 2.3.3 # 安装指定版本  

  $ gitbook versions:uninstall # 卸载当前选中版本  
  $ gitbook versions:uninstall 2.3.3 # 卸载指定版本  

  $ gitbook versions:link # 指定当前文件夹使用当前选中版本  
  $ gitbook versions:link 2.3.3 # 指定当前文件夹使用指定版本  
  $ gitbook versions:link path # 指定path使用指定版本  
  $ gitbook -v 2.3.3 # 指定当前使用哪个版本的gitbook  
  $ gitbook --gitbook 2.3.3 # 同上  
  ```

- gitbook常用命令

  ```bash
  $ gitbook init # 初始化一个仓库

  $ gitbook install # 安装插件

  $ gitbook serve [book] # 本地预览
  $ gitbook serve --port 8001 # 指定端口

  $ gitbook build repository PATH # 输出一个静态网站

  $ gitbook pdf book pdf # 生成pdf文件

  $ gitbook help # 查看帮助
  ```

>顺便吐槽一下gitbook命令设计是有问题，两个不同的命令耦合在了一起。

## 图书项目结构

README.md和SUMMARY.md是Gitbook项目必备的两个文件，也就是一本最简单的GitBook也必须含有这两个文件，它们在一本Gitbook中具有不同的用处。

- README.md  
这个文件相当于一本Gitbook的简介。

- SUMMARY.md  
这个文件是一本书的目录结构，使用Markdown语法，一个简单的例子如下所示。

  ```Markdown
  # Summary

  * [Part I](part1/README.md)
      * [Writing is nice](part1/writing.md)
      * [GitBook is nice](part1/gitbook.md)
  * [Part II](part2/README.md)
      * [We love feedback](part2/feedback_please.md)
      * [Better tools for authors](part2/better_tools.md)
  ```

- book.json  
自从GitBook 2.0.0开始支持自定义简介文件，在book.json中定义，这样README.md就可以用作项目的简介。
```json
{
    "structure": {
        "readme": "myIntro.md"
    }
}  
```
book.json还有自定义更多的信息，比如网页的title，description等，全部可配置信息请查看[这里](book.json.md)。

- GLOSSARY.md  
你可以定义一些条目并且这些条目将显示在术语表中. 基于这些条目, GitBook 讲自动创建一个索引并在页面中高亮显示这些条目.  
`GLOSSARY.md` 文件的格式很简单 :  
  ```markdown
  # 条目
  条目的定义

  # 另一个条目
  条目的定义可以包含加粗文本以及其它所有种类的内联标签 ...
  ```

## 发布  

使用gitbook可以很方便的发布到很多平台下面举几个常用的例子。

- 发布到GitHub  
源代码保存到master分支，build出来的上传到gh-pages分支，就这么简单的搞定了。

- 发布PDF
这里以windows平台为例子，需要先安装calibre@2.38.0（其实只是需要ebook-convert这个工具），安装好后将其安装目录配置到PATH。  
然后就可以使用下面的命令生成pdf了。  
```bash
$ gitbook pdf . ../temp.pdf # 将当前目录，生成到父目录下的temp.pdf
```

## 个性化

> gitbook 在编译书籍的时候会读取书籍源码顶层目录中的 book.json  

具体可查看 [book.json](book.json.md)


## *注意*

目前gitbook最新版为3.x.x , 在`Windows`下存在无法正常livereload的bug,如果需要正常使用livereload,可选择使用2.x.x版本的gitbook。
修改办法:
修改`book.json`,添加行
```
"gitbook" : "2.x.x",
```
*book.json必须是合法的json文件，否则修改不能生效*


## 编辑工具推荐
  * ### [atom](https://atom.io/)  
  * ### [gitbook官网编辑器](https://www.gitbook.com/editor)  
  * ### [sublime text](https://www.sublimetext.com/)  

**个人推荐使用 atom 编辑器，这款编辑器由github提供，使用 javascript/coffee进行开发，社区支持很好，
最主要的是atom自带markdown实时预览，左边写右边即时更新，100%兼容github的markdown语法，不需要自己去配置。  
sublime text 虽然是个很好的编辑器,对markdown的支持也很不错，但需要用户自己花时间去配置，如果只是为了写markdown而去使用sublime，  
这是一件很不值当的事情。  
`atom`还是一款新生的编辑器，是否能够取代`sublime text`还未可知，但就目前来看还有许多需要完善的地方，最明显的就是其运行速度，还有就是由于国内防火墙的关系，导致国内要下载atom的插件十分困难，我到现在还只是在用原生的atom，而不像sublime text拥有一套自己的配置（毕竟sublime的精髓就在插件啊）。  
还有一点，atom自带的markdown-preview插件默认是实时更新，也就是说只要你改变代码，预览就会实时更新。这在编写的时候会导致整个atom带点卡顿的效果，十分影响编写速度，所以建议关闭，只在保存后更新预览。
最后，其实配合`chrome`也可以实现实时预览功能啊,就是慢点（笑）
gitbook官网编辑器我没使用过，但其他用户反映良好，所以也可以尝试使用**
