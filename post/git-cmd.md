# git cmd

- `git stash` 把当前的分支的修改存储下来. 
- `git clean` 移除未被追踪的文件
- `git grep -n $key` 搜索
- `git rebase -i HEAD~$n` 将一连串提交压缩成一个单独的提交
- `git reset` 重置
- `git cherry-pick $commit` 选取 commit 号
- `git checkout --ours/theirs $filename` 分支冲突二选一，使用自己/对方的代码
- `git branch | grep -v 'master' | xargs git branch -D` 删除除了master之外的所有分支
- `git log --pretty=format:%H | tail -1` 获取第一个提交
- `git push origin -d $remote-branch` 删除远程分支
- `git merge --squash $other-branch` 合并，且压缩 commit
- `git push --force --set-upstream origin  master`  强制用另一个仓库更新远程服务器
