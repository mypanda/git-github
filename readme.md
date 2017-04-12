### git tag

0. [http://caibaojian.com/github-create-tag](http://caibaojian.com/github-create-tag.html)
1. tags作用 - 可以作为版本的更新情况
2. `git tag` 列表所有的tag
3. `git tag -| v1.*` 列表显示选定的符合条件
4. `git tag v1.0` 新建tag
5. `git tag -a v1.0 -m 'first version'` 带注释的tag
6. `git tag -s v1.0 -m 'first version'`
	* 前提是你有GPG私钥，把上面的a换成s就行了。
	* 除了可以为当前的进度添加tag，我们还可以为以前的commit添加tag
```
#首先查看以前的commit
git log --oneline
#假如有这样一个commit：8a5cbc2 updated readme
#这样为他添加tag
git tag -a v1.18a5cbc2
```
7. `git tag -d v1.0` 删除tag
8. `git tag -v v1.0` 如果有GPG私钥的话就可以验证tag
9. `git push origin --tags`--tags参数 提交tags到github

### git branch

0. [http://www.cnblogs.com/sk-net/archive/2011/07/11/2103282.html](http://www.cnblogs.com/sk-net/archive/2011/07/11/2103282.html)
0. [http://www.tuicool.com/articles/A3Mn6f](http://www.tuicool.com/articles/A3Mn6f)
1. 分支作为开发的工作目录
2. 开发分支合并到master发布
3. `git branch dev` 新建分支
4. `git checkout dev` 切换分支
5. `git checkout -b dev` 新建并切换到dev分支
6. 合并分支，要先切换到master分支 `git checkout master`
7. `git merge dev` 合并分支,要在master分支上,保留合并的日志
	* 调用 `git status` 查看冲突文件
	* 有冲突`git add` `git rm`解决冲突
	* 解决后`git commit`提交
8. `git rebase dev` 分支衍合(合并的另一种),不会保留合并日志
	* 调用 `git status` 查看冲突文件
	* 有冲突`git add` `git rm`解决冲突
	* 解决后`git rebase --continue`提交更改
9. 删除分支 `git branch -d dev`
	* 没有合并分支删除报错,`git branch -D dev` 强制删除
### git push 
0. [www.yiibai.com/git/git_push.html](http://www.yiibai.com/git/git_push.html)
1. git push origin master 推送master分支
2. git push origin 推送当前分支
3. git push --all origin 推送所有分支
### 使用步骤

* 本地已经有.git没有关联远程
* github新建respository,
* `git add .`移动到暂存区
* `git commit -m 'first commit'`
* `git remote add origin https://github.com/mypanda/git-tag.git`关联远程仓库
* `git push -u origin master`提交master分支
* `git puch -u origin`提交所有的分支
* `git push origin --tags`--tags参数 提交tags
