---
# Gitlab
## 安装
### 拉取社区版镜像
+ docker pull gitlab/gitlab-ce

### 创建挂载目录
+ /Users/lvweiwei/docker/gitlab/etc
+ /Users/lvweiwei/docker/gitlab/log
+ /Users/lvweiwei/docker/gitlab/data

### 启动容器
+ docker run -d -p 8443:443 -p 8090:80 -p 22:22 --name gitlab -v /Users/lvweiwei/docker/gitlab/etc:/etc/gitlab -v  /Users/lvweiwei/docker/gitlab/log:/var/log/gitlab -v /Users/lvweiwei/docker/gitlab/data:/var/opt/gitlab gitlab/gitlab-ce

### 登录
+ localhost:8090
+ 管理员用户：root
+ 密码：Passw0rd

> 默认帐户的用户名是root，第一次访问时，将被重定向到密码重置界面

## 启动、关闭脚本
+ 启动脚本：/Users/lvweiwei/docker/startgitlab
+ 关闭脚本：/Users/lvweiwei/docker/stopgitlab

## 配置SSH
+  运行ssh-keygen来创建(*不要只使用ssh-keygen，不然git clone等会告警*)

> ssh-keygen -f ~/.ssh/id_rsa -y > ~/.ssh/id_rsa.pub

+  SSH公钥默认储存在账户的主目录下的 ~/.ssh 目录
+  查看公钥id_rsa.pub
+  在gitlab中添加公钥

> 登陆GitLab账号
>
> 点击用户图像 -> Settings -> SSH keys
>
> 复制公钥内容，粘贴进“Key”文本区域内，取名字
> 
> 点击Add Key

## 测试
+ 创建测试目录/Users/lvweiwei/gitlabtest
+ 在/Users/lvweiwei/gitlabtest执行：git clone git@localhost:root/test.git
+ 

## Gitlab网上资料
+ [gitlab-ce in docker hub](https://hub.docker.com/r/gitlab/gitlab-ce/)
+ [docker安装配置gitlab详细过程](https://www.cnblogs.com/zuxing/articles/9329152.html)
+ [docker 安装 gitlab](https://www.cnblogs.com/panjunbai/p/11477197.html)
+ [GitLab使用教程，看这一篇就够了](https://www.jianshu.com/p/bf7b09e234c8)

---
# Git
## 修改全局参数
+ git config -e --global 进入全局配置文件，修改用户名和邮箱

## 基本操作
+ 把当前目录变成Git可以管理的仓库: git init 
+ 提交: git commit -m “message”
+ 查看仓库状态: git status
+ 查看文件变更: git diff <filename>
+ 显示从最近到最远的提交日志: git log 或者 git log --pretty=oneline

## 添加文件
+ 添加文件: git add <file1> <file2> 
+ git add . 

> 把工作时的所有变化提交到暂存区，包括文件内容修改(modified)以及新文件(new)，但不包括被删除的文件

+ git add -u

> 仅监控已经被add的文件（即tracked file），会将被修改的文件提交到暂存区，不会提交新文件（untracked file）

+ git add -A 

> 上面两个功能的合集（git add --all的缩写）

## 撤销(文件)修改
+ git checkout -- file

> 让文件回到最近一次git commit或git add时的状态

+ git reset HEAD <file>

> 把暂存区的修改撤销掉（unstage），重新放回工作区

## 删除文件
+ 手工删除文件
+ git rm <file> 或 git add<file> : 从工作区删除
+ git commit提交或git checkout -- <file>恢复

## 版本回退
+ 在版本的历史之间穿梭: git reset --hard commit_id
+ 查看提交历史，以便确定要回退到哪个版本: git log
+ 查看命令历史，以便确定要回到未来的哪个版本: git reflog
+ 回退到上一个版本: git reset --hard HEAD^
+ 回退到上上一个版本: git reset --hard HEAD^^

## 远程库操作
### 将已有本地库关联远程空白库

> 适用于在远程库创建一个空白库，把一个已有的本地库关联到这个远程库上

+ 将当前库关联一个远程库: git remote add origin git@server-name:path/repo-name.git
+ 第一次推送master分支的所有内容: git push -u origin master
+ 推送最新修改: git push origin master

### 从远程库克隆

> 最好的方式是先创建远程库，然后，从远程库克隆

+ git clone git@server-name:path/repo-name.git

> 上述命令将在当前目录创建子目录“repo-name”
> 

### 查看远程库的信息

> 当你从远程仓库克隆时，实际上Git自动把本地的master分支和远程的master分支对应起来了
> 
> 远程仓库的默认名称是origin

+ 查看远程库的信息: git remote -v

### 向远程库推送分支
+ 推送master分支到远程库: git push origin master
+ 推送其他分支，比如dev到远程库: git push origin dev

> master分支是主分支，因此要时刻与远程同步
> 
> dev分支是开发分支，团队所有成员都需要在上面工作，所以也需要与远程同步
>
> bug分支只用于在本地修复bug，就没必要推到远程了，除非老板要看看你每周到底修复了几个bug
> 
> feature分支是否推到远程，取决于你是否和你的小伙伴合作在上面开发
> 
> 总之，就是在Git中，分支完全可以在本地自己藏着玩，是否推送，视你的心情而定

## 分支操作
+ 查看分支：git branch
+ 创建分支：git branch <name>
+ 切换分支：git checkout <name>或者git switch <name>
+ 创建+切换分支：git checkout -b <name>或者git switch -c <name>
+ 合并某分支到当前分支：git merge <name>
+ 删除分支：git branch -d <name>

## Bug分支
> 修复bug时，我们会通过创建新的bug分支进行修复，然后合并，最后删除
> 
> 当手头工作没有完成时，先把工作现场git stash一下，然后去修复bug，修复后，再git stash pop，回到工作现场
> 
> 在master分支上修复的bug，想要合并到当前dev分支，可以用git cherry-pick <commit>命令，把bug提交的修改“复制”到当前分支，避免重复劳动

## Git网上资料
+ [Git教程-廖雪峰](https://www.liaoxuefeng.com/wiki/896043488029600)

> **非常好的教程**