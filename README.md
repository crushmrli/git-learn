# git-learn
# git-learn



## git常用操作命令

```javascript
git init    //初始化，把目录变成仓库
git add fileName    //把文件添加到暂存区预备上传
git commit -m 'infor'   //把暂存区的文件提交到当前分支 并且添加上传说明比如'add 2 files'  
git status  //查看仓库当前状态会告诉我什么文件被修改了  
git diff    //顾名思义就是查看每次修改的difference只是提交前修改的    
git log     //查看历史记录  

git reset --hard HEAD~版本号 //回退版本 HEAD指向当前版本
//如果不写 HEAD就可以在版本里历史中穿梭（可能会出现退出不了的情况这个时候按q）  
git reflog  //可以查看每一次命令记录(可以查看版本号)

git reset --hard 版本号     //退回到一个版本（利用版本号）  

git checkout -- fileName    //可以把暂存区的内容会退到上一次add操作的内容或者上一次commit之后的内容


```

### 分支管理

```javascript
git branch      //查看分支

git checkout -b name //创建分支并切换 -b表示创建并切换相当于下面两条命令

git branch name      //创建分支

git checkout name    //切换到分支(常用)

git merge name       //合并dev分支到master上

git branch -d name   //删除dev分支(-D为强制删除分支，有时候分支没有合并就要被删除 这个时候用)

git merge --no-ff -m "info" name
//合并分支时，加上--no-ff参数就可以用普通模式合并，合并后的历史有分支，能看出来曾经做过合并，而fast forward合并就看不出来曾经做过合并。

```

### bug分支

```javascript
git stash       //存储当前工作区 

git stash list  //查看当前工作区的暂存区列表

git status      //查看状态  
```

```
git checkout master     //转移到问题区解决问题  

git checkout dev        //返回工作区继续完成工作
```

```
git stash apply stash@{num}    //回复工作区(但是不删除存储的临时内容) 
 
git stash drop stash@{num}  //删除暂存区

git stash pop   //回复工作区同时把stash内容删除
```

### 多人协作

```
git remote  //查看远程库的信息

git remote -v   //查看更详细的信息  

git push origin master  //把master主线推送到origin远程库中当然也可以推送其他分支  

git clone 仓库地址      //可以将远程库克隆到本地  

//克隆到本地的内容默认情况下只能看到masetr分支

git checkout -b dev origin/dev
//就可以创建远端origin的dev分支到本地

//当git的push操作出现问题，就是出现冲突的时候

git pull  //先把最新的提交从origin/dev 抓取下来，然后本地合并，解决冲突,再推送

git branch --set-upstream 本地分支名 远端库名/远端分支名
//上面的操作时将远端库的分支与本地建立联系
```

### 创建标签

```
git remote  //查看远程库的信息

git remote -v   //查看更详细的信息  

git push origin master  //把master主线推送到origin远程库中当然也可以推送其他分支  

git clone 仓库地址      //可以将远程库克隆到本地  

//克隆到本地的内容默认情况下只能看到masetr分支

git checkout -b dev origin/dev
//就可以创建远端origin的dev分支到本地

//当git的push操作出现问题，就是出现冲突的时候

git pull  //先把最新的提交从origin/dev 抓取下来，然后本地合并，解决冲突,再推送

git branch --set-upstream 本地分支名 远端库名/远端分支名
//上面的操作时将远端库的分支与本地建立联系
```

### 配置别名（为了方便快捷的操作）

```
git config --global alias.st status //将status缩写为st

git config --global alias.unstage 'reset HEAD'

//将展示log信息缩写为lg
git config --global alias.lg "log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit"

```

参考自：https://www.jianshu.com/p/2dac87817d51
