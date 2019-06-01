# Git 命令
## 1. 基本命令
1. 初始化Git仓库：git init
2. 添加文件：git add FileName
3. 删除文件：git rm FileName
4. 提交文件：git commit -m 'mark' Name
5. 查看仓库当天状态：git status
6. 工作区和上次提交的差异：git diff
7. 查看历史命令：git reflog
8. 查看从最近到最远的提交日志：git log
	+ --pretty=oneline  一行显示
	+ --graph 分支合并图
	+ --graph --pretty=oneline --abbrev-commit 简洁的合并情况
9. 查看远程库信息：git remote


## 2. 版本管理
1. 回退到上一个版本：git reset –hard HEAD^
2. 丢弃工作区的修改：git checkout - FileName
	1. 修改了工作区文件的内容，想直接丢弃工作区的修改时，用git checkout – file
	2. 不但修改了工作区的内容，还添加到了暂存区(git add)时，想丢弃修改，第一步git reset HEAD <file> ，第二步 git checkout – file
	3. 提交了不合适的到版本库时，想撤销的本次提交，参考版本回退方法

## 3. 分支管理
1. 查看分支：git branch
2. 创建名为dev分支：git branch dev
3. 删除分支：git branch -d dev
	+ 强制删除 -D
4. 切换分支：git checkout dev
5. 创建+切换分支：git checkout -b dev
6. 合并dev分支到当前分支：git merge dev
	+ --no-ff 强制禁用Fast forward模式(git merge --no-ff -m 'mark' dev)
7. 暂存工作区：git stash
	+ 恢复：git stash apply &lt; stash@{0} &gt;
	+ 删除：git stash drop &lt; stash@{0} &gt;
	+ 恢复并删除：git stash pop
	+ 查看：git stash list

## 4.标签管理
1. 创建标签：git tag Tagname
2. 指定标签信息：git tag -a Tagname -m 'mark...'
3. 查看所有标签：git tag
	+ 删除标签：git tag -d Tagname
	+ 删除远程标签：git push origin :refs/tags/Tagname
4. 一次性推送全部尚未推送到远程的本地标签：git push origin --tags