# Git flow 開發流程

大家都知道 Git 開 branch 很方便，非常鼓勵 topic branch，但有沒有一套模型流程告訴我們應該怎麼管理 branch 呢? 有人便整理出一套最佳實踐慣例 [A successful Git branching model](http://nvie.com/posts/a-successful-git-branching-model/)，。簡單來說，他將 branch 分成兩個主要分支，三種支援性分支：

![git flow模式 图解](../../resources/image/git_flow.png)

- 主要分支  
  * master: 永遠處在 production-ready 狀態
  * develop: 最新的下次發佈開發狀態
- 支援性分支
  * Feature branches: 開發新功能都從 develop 分支出來，完成後 merge 回 develop
  * Release branches: 準備要 release 的版本，只修 bugs。從 develop 分支出來，完成後 merge 回 master 和 develop
  * Hotfix branches: 等不及 release 版本就必須馬上修 master 趕上線的情況。會從 master 分支出來，完成後 merge 回 master 和 develop

> 作者還提供了 git-flow 指令工具幫助我們很容易的實踐，但其实这只是一个管理模式，最终还是需要人去实现。所以只需要使用这种方式去管理git流就行了。不需要纠结于是否需要使用git flow 插件。如果需要git flow的使用方法，可查看[原文链接](https://ihower.tw/blog/archives/5140)
