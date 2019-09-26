### Git&Github

#### 0、Git与SVN的区别
- **1、Git 是分布式的，SVN 不是**
- **2、Git 把内容按元数据方式存储，而 SVN 是按文件**
- **3、Git 分支和 SVN 的分支不同**
- **4、Git 没有一个全局的版本号，而 SVN 有**
- **5、Git 的内容完整性要优于 SVN**  
#### 1、基础  
- ##### Git配置

```
## 用户信息
$ git config --global user.name "Tooi6"
$ git config --global user.email test@Tooi.com
## 文本编辑器
$ git config --global core.editor emacs
## 差异分析工具
$ git config --global merge.tool vimdiff
## 查看配置信息
$ git config --list
$ git config user.name
```
> [Git 工作区、暂存区和版本库的基本概念](https://www.runoob.com/git/git-workspace-index-repo.html)

```
## 初始化仓库
$ git init
$ git init newrepo # 使用newrepo目录作为仓库

## 提交到仓库
$ git add *.c  # 加入到暂存区
$ git add README
$ git commit -m '初始化项目版本'

## 克隆远程仓库
$ git clone <repo> <directory>

## 查看项目的当前状态
$ git status

## 显示已写入缓存与已修改但尚未写入缓存的改动的区别
$ git diff # 尚未缓存的改动
$ git diff --cached # 查看已缓存的改动
$ git diff HEAD # 查看已缓存的与未缓存的所有改动
$ git diff # 显示摘要而非整个

## 取消已缓存文件内容
$ git reset HEAD <file>

## 移除缓冲区文件
$ git rm [-f] <file>
$ git rm -r <dir> # 删除文件夹

## 移动或重命名
$ git mv <filefrom> <fileto>
```
- 分支管理 
> 分支意味着你可以从开发主线上分离开来，然后在不影响主线的同时继续工作。  

```
## 创建分支
$ git branch <branchname>
$ git branch # 列出所有分支
$ git checkout -b <branchname> # 创建分支，并切换到该分支

## 切换分支
$ git checkout <branchname>

## 合并分支
$ git merge <branchname>

```
- ##### 查看提交历史

```
$ git log
$ git log --oneline # 简洁的版本
$ git log --reverse --oneline # 倒序显示（从第一次提交开始）
$ git log --author=tooi6 --oneline -5 # 查看tooi6作者提交的5条记录
## 三周前且在四月十八日之后的所有提交
$ git log --oneline --before={3.weeks.age} --after={2010-04-18} --no-merges #
```
[git log命令](https://git-scm.com/docs/git-log)
- ##### Git标签  
> 如果你达到一个重要的阶段，并希望永远记住那个特别的提交快照，你可以使用 git tag 给它打上标签。

```
## 给最新的一次提交打一个标签
$ git tag -a v1.0 
$ git tag -a v0.9 85fc7e7  # 给85fc7e7提交打标签
```
#### 2、Git 远程仓库(Github)
- ##### 添加远程库

```
## 添加一个新的远程仓库
git remote add [shortname] [url]

## 配置ssh
$ ssh-keygen -t rsa -C "youremail@example.com" # 先在本地电脑生成ssh key 再到GitHub中设置  
$ ssh -T git@github.com  # 验证是否配置成功

## 提交到 Github
$ git remote add origin git@github.com:Tooi6/FirstRepository.git 
$ git push -u origin master

## 提取远程仓库的更新
$ git fetch origin  # 获取远程仓库最新分支
$ git merge origin/master # 合并分支  
$ git push origin master    # 推送到 Github

## 删除远程仓库
$ git remote -v  # 查看远程仓库
$ git remote rm [别名]
```
#### 3、IDEA使用git