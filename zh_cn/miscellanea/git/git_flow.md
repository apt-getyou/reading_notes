# Git flow 开发流程

[git常用命令](http://www.ruanyifeng.com/blog/2015/12/git-cheat-sheet.html)

大家都知道 Git 开 branch 很方便，非常鼓励 topic branch，但有没有一套模型流程告诉我们应该怎么管理 branch 呢? 有人便整理出一套最佳实践惯例 [A successful Git branching model](http://nvie.com/posts/a-successful-git-branching-model/)，。简单来说，他将 branch 分成两个主要分支，三种支援性分支：

![git flow模式 图解](/resources/image/git_flow.png)

- 主要分支  
  * master: 永远处在 production-ready 状态
  * develop: 最新的下次发布开发状态
- 支援性分支
  * Feature branches: 开发新功能都从 develop 分支出来，完成后 merge 回 develop
  * Release branches: 准备要 release 的版本，只修 bugs。从 develop 分支出来，完成后 merge 回 master 和 develop
  * Hotfix branches: 等不及 release 版本就必须马上修 master 赶上线的情况。会从 master 分支出来，完成后 merge 回 master 和 develop

> 作者还提供了 git-flow 指令工具帮助我们很容易的实践，但其实这只是一个管理模式，最终还是需要人去实现。所以只需要使用这种方式去管理git流就行了。不需要纠结于是否需要使用git flow 插件。如果需要git flow的使用方法，可查看[原文链接](https://ihower.tw/blog/archives/5140)

- 支援性分支命名规范（非官方规范，可由个人自行决定，但最好团队统一）  
  * Feature branches: 新功能开发分支，feature\_{创建人}\_{yyyyMMddHHmm}\_{功能}  
    eg : `feature_lbw_201701151746_change_price`
  * HotFix branches: 修复bug分支，hotfix\_{创建人}\_{yyyyMMddHHmm}  
    eg : `hotfix_lbw_201701151750`
  * Release branches: 预发布分支，release\_{version}。（[version 命名规范](../version.md) ）  
    eg : `release_v0.1Bate`

- 远程分支处理  
  由于团队开发中，经常需要多人合作开发Feature分支，或者develop分支普通开发人员无法更改而需要使用`merge request`功能，这些都需要向git服务器推送远程分支来解决，如此就导致同一个项目上存在过多的分支。  
  在这种情况下就需要开发人员对分支进行管理，可以让开发人员之间选择是否删除远程分支，或者是由管理员统一管理。  
  删除远程分支可以通过命令  `git push --delete origin branch_name` 实现。  
  但执行这个命令后，虽然删除了远程分支，本地使用`git branch -a`也看不到这个分支了。但对于其他开发人员，他们使用`git branch -a`时还是可以看到这些本已经删除的分支(具体原因还不明确，可能是git自己的一个特性，或者就是个bug)。这时候可以通过执行`git remote prune origin`删除这些本已删除的分支。  
  > 删除分支时必须谨慎，确保被删除的分支上的代码已经全部合并完成了

- 关于 feature branch 的合并

    - 如果是开发时间比较久的 feature branch，很可能会因为  
      1. 不定时的 `merge develop` 与新版同步  
      2. 实验性质的修改  
      3. 需求的变更
      等等因素，而让这个 `feature branch` 的 commit 记录变成脏脏的
    - 这时候我们会用以下的方式来做 merge 动作：  
      1. 先对 feature branch 做 `git rebase develop`。会很苦，但是弄完会很有成就感，整个 branch commit history 会变成很乾净。请学 `interactive mode`，可以让你拿掉一些 commit丶合并或修改，你也可以 rebase 多次直到满意为止。
      1. 在从 develop bracnh 做 `git merge feature/some_awesome_feature －no-ff`，－no-ff 的意思是会强制留一个 `merge commit log` 记录，这可以让 `commit tree` 看清楚发生了 merge 动作。(因为我们刚做了 rebase，而 git 预设的合并模式是 fast-forward，所以如果不加 －no-ff 是不会有 merge commit 的) 这个 merge commit 的另一个额外方便之处是，如果想要 reset/revert 整个 branch 只要 reset/revert 这个 commit 就可以了。
      1. 如果此 feature branch 有 remote branch，要先砍掉 `git push origin :feature/some_awesome_feature` 再 `git push origin develop` (这是因为 rebase 一个已经 push 出去的 repository，然后又把修改的 history push 出去，会造成超级大灾难啊~)

    - 先 rebase 再 merge －no-ff 这样做的好处到底是什么? 看图体会一下吧：
    ![commit tree 图](/resources/image/git-branch1.jpg)  
    每一次的 merge 就代表了一个 feature 完成，也可以很清楚看到这个 feature branch 底下包含哪些 commit。
