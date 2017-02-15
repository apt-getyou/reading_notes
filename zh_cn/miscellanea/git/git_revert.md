# git revert 用一个新提交来消除一个历史提交所做的任何修改

git revert用于反转提交,执行revert命令时要求工作树必须是干净的.

git revert用一个新提交来消除一个历史提交所做的任何修改.

revert 之后你的本地代码会回滚到指定的历史版本,这时你再 git push 既可以把线上的代码更新.(这里不会像reset造成冲突的问题)

revert 使用,需要先找到你想回滚版本唯一的commit标识代码,可以用 git log 或者在adgit搭建的web环境历史提交记录里查看。  
`git revert c011eb3c20ba6fb38cc94fe5a8dda366a3990c61`  
通常,前几位即可  
`git revert c011eb3`  
`git revert`是用一次新的`commit`来回滚之前的`commit`，`git reset`是直接删除指定的`commit`  
看似达到的效果是一样的，其实完全不同。  
第一:   
上面我们说的如果你已经push到线上代码库, reset 删除指定commit以后,你git push可能导致一大堆冲突.但是revert 并不会.  
第二:  
如果在日后现有分支和历史分支需要合并的时候,reset 恢复部分的代码依然会出现在历史分支里.但是`revert` 方向提交的`commit` 并不会出现在历史分支里.  
第三:  
`reset` 是在正常的`commit`历史中,删除了指定的`commit`,这时 `HEAD` 是向后移动了,而 `revert` 是在正常的`commit`历史中再`commit`一次,只不过是反向提交,他的 `HEAD` 是一直向前的.  
