## GitBook 简介

GitBook 是一个通过 Git 和 Markdown 来撰写书籍的工具，最终可以生成 3 种格式：

静态站点：包含了交互功能（例如搜索、书签）的站点  
PDF：PDF 格式的文件  
eBook：ePub 格式的电子书文件  
GitBook 是免费且开源的，项目地址：https://github.com/GitbookIO/gitbook  


## gitbook-cli

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
book.json还有自定义更多的信息，比如网页的title，description等，全部可配置信息请查看这里。

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



## 编辑工具推荐
  * ### [atom](https://atom.io/)
  * ### [gitbook官网编辑器](https://www.gitbook.com/editor)
  * ### [sublime text](https://www.sublimetext.com/)

  *个人推荐使用 atom 编辑器，这款编辑器由github提供，使用 javascript/coffee进行开发，社区支持很好，
  最主要的是atom自带markdown实时预览，左边写右边即时更新，100%兼容github的markdown语法，不需要自己去配置。  
  sublime text 虽然是个很好的编辑器,对markdown的支持也很不错，但需要用户自己花时间去配置，如果只是为了写markdown而去使用sublime，  
  这是一件很不值当的事情。  
  gitbook官网编辑器我没使用过，但其他用户反映良好，所以也可以尝试使用*
