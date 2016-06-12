## GitBook 简介

GitBook 是一个通过 Git 和 Markdown 来撰写书籍的工具，最终可以生成 3 种格式：

静态站点：包含了交互功能（例如搜索、书签）的站点  
PDF：PDF 格式的文件  
eBook：ePub 格式的电子书文件  
GitBook 是免费且开源的，项目地址：https://github.com/GitbookIO/gitbook  

## GitBook 安装  

* 全局安装
```bash
npm install -g gitbook
```
* 项目内安装
```bash
npm install gitbook
```

* 如果需要在命令行执行gitbook命令，可选择安装 `gitbook-cli`   
安装方式   
```bash
 npm install -g gitbook-cli
 ```

 ## 章节和子章节

 使用SUMMARY.md定义章节结构.

 SUMMARY.md的格式是一个简单的链接列表, 链接名作为章节名, 目标是章节文件路径.

 添加嵌入列表定义子章节.

 简例

  ```markdown
   # 概要

   * [第一章](chapter1.md)
   * [第二章](chapter2.md)
   * [第三张](chapter3.md)
 ```

 子章节例子

  ```markdown
   # 概要

   * [第一部分](part1/README.md)
       * [Writing is nice](part1/writing.md)
       * [GitBook is nice](part1/gitbook.md)
   * [第二部分](part2/README.md)
       * [We love feedback](part2/feedback_please.md)
       * [Better tools for authors](part2/better_tools.md)
  ```



## 编辑工具推荐
  * ### [atom](https://atom.io/)
  * ### [gitbook官网编辑器](https://www.gitbook.com/editor)
  * ### [sublime text](https://www.sublimetext.com/)

  > 个人推荐使用 atom 编辑器，这款编辑器由github提供，使用 javascript/coffee进行开发，社区支持很好，
  最主要的是atom自带markdown实时预览，左边写右边即时更新，100%兼容github的markdown语法，不需要自己去配置。  
  sublime text 虽然是个很好的编辑器,对markdown的支持也很不错，但需要用户自己花时间去配置，如果只是为了写markdown而去使用sublime，  
  这是一件很不值当的事情。  
  gitbook官网编辑器我没使用过，但其他用户反映良好，所以也可以尝试使用
