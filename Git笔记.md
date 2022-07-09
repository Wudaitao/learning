git 使用笔记
------------

## 常用命令

### 用户配置

**git config --global uer.name "NONWORD"**

**git config --global user.email 814302486@qq.com**

- --local(默认，高优先级)：只影响本地仓库
- --global(中优先级)：只影响所有当前用户的git仓库
- --system(低优先级)：影响到全系统的git仓库

### 管理仓库相关命令

**git init**： 初始化仓库

**git status**：对仓库状态的跟踪
	
	git status介绍：
	git中有两个状态：内容状态和文件状态，
	内容状态标示内容文件的改变，有三个区域：工作目录，暂存区和提交区
	文件状态有两个状态：已跟踪和未跟踪

![](https://img-blog.csdnimg.cn/cbfe8e2a30ea4f138c0f6f837de9cc7a.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAQmV0dHlhbmVy,size_20,color_FFFFFF,t_70,g_se,x_16)

**git add <filelist>**： 添加文件内容到暂存区（同时文件被跟踪）

**git add .**：添加所有文件到暂存区

**git commit -m "my first commit."**:从暂存区提交到提交区，-m：提交的注释

**git commit -a -m "full commit."**:从工作区提交到提交区

**git commit --amend**：通过vim直接修改上次提交的注释信息

**git log**:查看提交历史记录

**git diff**：工作区与暂存区的差异

**git diff --cached [<reference>]**：暂存区与某次提交的差异，默认为HEAD

**git diff [<reference>]**：工作区与某次提交的差异，默认为HEAD

**git checkout -- <file>**：将文件内容从暂存区复制到工作区

**git reset HEAD <file>**：将文件内容从上次提交区复制到暂存区

**git checkout HEAD -- <file>**：将文件从上次提交区复制到工作区

![](https://img-blog.csdnimg.cn/d479dc58dfc04d488f6188a2973686e8.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAQmV0dHlhbmVy,size_20,color_FFFFFF,t_70,g_se,x_16)

### 分支操作

**git branch**

* git branch <branchName> //创建一个分支
* git branch -d <branchName> //删除一个分支
* git branch -v //显示所有分支信息

**git checkout**

* git checkout <branchName> //通过移动HEAD检出版本，可用于切换分支
* git checkout -b <branchName> //创件一个分支并切换
* git checkout <reference> //将其移动到一个引用
* git checkout - //恢复到上一个分支

**git reset**:回退当前分支到历史某个版本

* git reset --mixed <commit>  //默认
* git reset --soft <comit>
* git rest --hard <commit>

![](https://img-blog.csdnimg.cn/f90d6a4c25a542ac82bc3372c14d699e.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAQmV0dHlhbmVy,size_20,color_FFFFFF,t_70,g_se,x_16)

**git stash**：git stash 用来保存目前的工作目录和暂存区状态，并返回到干净的工作空间。有时候我们要切换分支会有以下提示，是因为当前分支还有内容未提交，现在切换内容会丢失。这时候要用到git stash 命令

* git stash save "push to stash area" // 通过save 后面传入信息标识 放到stash区
* git stash llist //查看收藏的记录
* git stash apply stash@{0} //将保存的内容重新恢复到工作目录
* git stash drop stash@{0} //将对应的stash记录删除
* git stash pop //= git stash apply + git stash drop

![](https://img-blog.csdnimg.cn/1442d0f069494e3498499ce8fe260731.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAQmV0dHlhbmVy,size_20,color_FFFFFF,t_70,g_se,x_16)

**git merge**:合并分支操作

### 远程操作

**git init ~/git-server --bare**:初始化一个本地的远程服务器

**git push**：将本地历史推送到远程

**git remote add origin ~/git-server**：添加一个远程仓库的别名

**git remote -v**:查看远程仓库信息

**git fetch**:获取远程仓库的提交记录

**git pull**:git fetch + git merge，拉取远程记录并合并提交记录

**git clone**:克隆一个远程仓库作为本地仓库
