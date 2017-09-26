### 撤销

[link](http://blog.csdn.net/u013485584/article/details/53319044)
### git bash for window

[git bash](https://git-for-windows.github.io/)

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
7. `git push origin :refs/tags/标签名``git push origin :refs/tags/protobuf-2.5.0rc1` 删除远程标签
```
#首先查看以前的commit
git log --oneline
#假如有这样一个commit：8a5cbc2 updated readme
#这样为他添加tag
git tag -a v1.1 8a5cbc2
```
7. `git tag -d v1.0` 删除tag
8. `git tag -v v1.0` 如果有GPG私钥的话就可以验证tag
9. `git push origin --tags`--tags参数 提交tags到github

### git log
* `git log -- filename （git log filename）` 查看该文件每次提交记录
* `git log -p filename` 查看一个文件所有的修改,查看每次详细修改内容的diff
* `git log -p -2` 查看最近两次详细修改内容的diff
* `git log --stat` 查看提交统计信息

|选项|说明|
|:---:|:---:|
|-p|按补丁格式显示每个更新之间的差异。|
|--stat|显示每次更新的文件修改统计信息。|
|--shortstat|只显示 --stat 中最后的行数修改添加移除统计。|
|--name-only|仅在提交信息后显示已修改的文件清单。|
|--name-status|显示新增、修改、删除的文件清单。|
|--abbrev-commit|仅显示 SHA-1 的前几个字符，而非所有的 40 个字符。|
|--relative-date|使用较短的相对时间显示（比如，“2 weeks ago”）。|
|--graph|显示 ASCII 图形表示的分支合并历史。|
|--pretty|使用其他格式显示历史提交信息。可用的选项包括 oneline，short，full，fuller 和 format（后跟指定格式）。|
|-----|-----|
|-(n)|仅显示最近的 n 条提交|
|--since, --after|仅显示指定时间之后的提交。|
|--until, --before|仅显示指定时间之前的提交。|
|--author|仅显示指定作者相关的提交。|
|--committer|仅显示指定提交者相关的提交。|
|--grep|仅显示含指定关键字的提交|
|-S|仅显示添加或移除了某个关键字的提交|

### git diff
* `git diff id id ./src/main.js` 比较commit之间文件的不同
* `git diff <file>` 比较当前文件和暂存区文件的差异
### git show
* `git show commit-id filename` 查看某次提交中的某个文件变化
* `git show commit-id` 根据commit-id查看某个提交
### git reset 
* `git reset --hard` 取消下载，就是恢复到工作区
* `git reset` 取消git add
* `git reset --hard commit_id` 取消那次commit
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
4. git push origin :dev 删除远程的dev分支
### 使用步骤

* 本地已经有.git没有关联远程
* github新建respository,
* `git add .`移动到暂存区
* `git commit -m 'first commit'`
* `git remote add origin https://github.com/mypanda/git-tag.git`关联远程仓库
* `git push -u origin master`提交master分支
* `git puch -u origin`提交所有的分支
* `git push origin --tags`--tags参数 提交tags

### 冲突怎么解决
* 远程commit提交了，然后本地也做了修改，冲突
* `git pull origin master`下载到本地
*  然后手动修改冲突
* `git add .`
* `git commit -m 'repair'`
* `git push origin master` 提交到远程

### git merge

* `git merge --no-ff dev` --no-ff参数是在master新建节点，然后把dev合并上来，不带--no-ff是，master的head指针指向dev并非是正常理解的合并过来

### git add和取消add

* `git reset HEAD .` 或者 `git reset HEAD a.txt`取消放置到暂存区的内容， 

### git reset --hard commit->id

* `git reset --hard 1111111` 把Hard指向上一个111111111这个commit
* `git reset --hard 2222222` 只要窗口不关，找到222222这个id，在执行一次reset --hard + id就可以前进到222222版本

### git checkout

* 撤销工作区修改`git checkout .`
