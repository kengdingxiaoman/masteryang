# git命令积累

## 常用命令

### 查看本地仓库状态
git status

该命令可以让我们时刻掌握仓库当前的状态
- Changes not staged for commit： 文件被修改过了，但还没有准备提交的修改(原有文件修改过，还未add)
- Changes to be committed： 文件可以提交 (add了还未commit)
- nothing to commit, working tree clean：当前没有需要提交的修改，工作目录是干净的 (commit后)
- Untracked files：文件还未被添加 (新建的文件，还没add)

### 查看文件具体修改了什么内容
git diff <font color="red">${filename}</font>

### 提交文件到本地仓库
git add <font color="red">${filename}</font>

然后执行命令：<br/>
git commit -m "${commit_message}"

### 查看历史记录
git log

也可以后面跟具体的文件名：<br/>
git log <font color="red">${filename}</font>

可以加上 参数 \-\-pretty=oneline，这样显示会比较清晰一些<br/>
git log \-\-pretty=oneline <font color="red">${filename}</font>

### 撤销工作区修改
git checkout \-\- <font color="red">${filename}</font>

命令 git checkout \-\- ${filename}意思就是，把文件在工作区的修改全部撤销，这里有两种情况：

一种是文件自修改后还没有被放到暂存区，现在，撤销修改就回到和版本库一模一样的状态<br/>
一种是文件已经添加到暂存区后，又作了修改，现在，撤销修改就回到添加到暂存区后的状态

总之，就是让文件回到最近一次git commit或git add时的状态。

**特别注意**：<font color="red">git checkout \-\- ${filename} 命令中的\-\-很重要，没有\-\-，就变成了"切换到另一个分支"的命令</font>

### 撤销暂存区修改
git reset HEAD <font color="red">${filename}</font>

<font color="red">git reset命令既可以回退版本，也可以把暂存区的修改回退到工作区。</font>当我们用HEAD时，表示最新的版本。

### 版本回退
回退时，Git必须知道当前版本是哪个版本，在Git中，用HEAD表示当前版本，上一个版本就是HEAD^，上上一个版本就是HEAD^^，当然往上100个版本写100个^比较容易数不过来，所以写成HEAD~100。

具体回退命令：
git reset \-\-hard HEAD^

也可以在得知了 commit id 后，直接使用如下命令：<br/>
git reset \-\-hard <font color="red">${commit_id}</font>

- git 版本的回退只是指向版本指针的重新指向，所以你也可以再重新指回最新的版本，只要知道版本的commit_it
- commit_id不用写全，一般写个7位就可以了，如果找不到 commit_id了，可以使用 git reflog命令

### 从仓库中删除文件
git rm <font color="red">${filename}</font>

别忘了还要执行 git commit

### 查看命令历史
git reflog <br/>
可以通过该命令获取commit_id

### 查看git版本
git --version

## 远程仓库

### 推送到远程仓库
git push -u origin master

把本地库的内容推送到远程，用git push命令，实际上是把当前分支master推送到远程。

由于远程库是空的，我们第一次推送master分支时，加上了-u 参数，Git不但会把本地的master分支内容推送的远程新的master分支，还会把本地的master分支和远程的master分支关联起来，在以后的推送或者拉取时就可以简化命令，只需使用

git push origin master

### 克隆远程仓库
克隆远程仓库就相等于是获取远程仓库的代码

git clone https://github.com/kengdingxiaoman/learngit.git

### 创建仓库
git init

### 新建一个本地仓库添加到远程仓库
git init <br/>
git add README.md <br/>
git commit -m "first commit" <br/>
git remote add origin https://github.com/kengdingxiaoman/learngit.git <br/>
git push -u origin master

### 添加一个本地仓库到远程仓库
git remote add origin https://github.com/kengdingxiaoman/learngit.git
git push -u origin master

## 分支管理
因为创建、合并和删除分支是非常快的，所以Git鼓励你使用分支完成某个任务，合并后再删掉分支，这和直接在master分支上工作效果是一样的，但过程更安全。

### 创建分支
git checkout -b <font color="red">${branchname}</font> <br/>
\-b 创建并切换

也可以执行如下2条命令来完成：<br/>
git branch <font color="red">${branchname}</font> <br/>
git checkout <font color="red">${branchname}</font>

### 查看当前分支
git branch <br/>
git branch 命令会列出所有分支，当前分支前面会标一个<font color="red">\*</font>号

### 合并分支
git merge <font color="red">${branchname}</font> <br/>
git merge命令用于合并指定分支到当前分支

### 删除分支
git branch -d <font color="red">${branchname}</font> <br/>


## 名词解释

### origin 和 master
在 clone 完成之后，Git 会自动为你将远程仓库命名为 origin，origin 只相当于一个别名，运行 git remote –v 或者查看 .git/config 可以看到 origin 的含义，并下载其中所有的数据，建立一个指向它的 master 分支的指针，我们用 (远程仓库名)/(分支名) 这样的形式表示远程分支，所以 origin/master 指向的是一个remote branch (从那个branch我们clone数据到本地)，但你无法在本地更改其数据。

远程库的名字就是origin，这是Git默认的叫法，也可以改成别的，但是origin这个名字一看就知道是远程库

Git自动会为我们创建了唯一一个master分支，所以，git commit就是往master分支上提交更改。

### 暂存区和工作区
- 工作区：就是在你电脑里能看到的目录

- 版本库：工作区有一个隐藏目录 .git，这个不算工作区，而是Git的版本库。Git的版本库里存了很多东西，其中最重要的就是称为stage(或者叫index)的暂存区，还有Git为我们自动创建的第一个分支master，以及指向master的一个指针叫HEAD。

文件往Git版本库里添加的时候，是分两步执行的：
- 第一步是用 git add 把文件添加进去，实际上就是把文件修改添加到暂存区

- 第二步是用 git commit 提交更改，实际上就是把暂存区的所有内容提交到当前分支

需要提交的文件修改通通放到暂存区，然后，一次性提交暂存区的所有修改。
