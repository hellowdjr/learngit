# gitnote

## 一、创建版本库

1.git自报家门：

```
$ git config --global user.name "Your Name"
$ git config --global user.email "email@example.com"
```

2.建立git仓库：创建一个文件夹并右键   点击Bash  输入:

```
$ git init
```

3.将文件添加到暂存区：

```
$ git add 文件名（有后缀）
```

​      //注意文件名中不能有空格                                                 

## 二、

4.提交暂存区的文件到当前分支：

```
$ git commit -m "本次提交的标签"
```

​   //注意commit会把暂存区的所有文件提交

5.查看仓库状态：

```
$ git status
```

## 三、版本回退

6.查看版本历史记录：

```
$ git log
```

7.查看版本库与当前区别：

```
$ git diff HEAD -- 文件名（加后缀）
```

8.版本回退：

```
$ git reset --hard HEAD^               //HEAD^表示上一个版本

$ git reset --hard e475af              //e475af是版本号的前几位     
                                     即commit id
```

9.查看版本提交和回退的命令的历史记录

```
$ git reflog
```

  这个命令可以用于查找回退前的版本号（commit id）  

## 四、管理修改（包括删除）

10.撤销暂存库中的修改(unstage)

```
$ git reset HEAD 文件名（后缀）
```

11.丢弃工作区的修改，使文件回到最近一次git add或 git commit的状态

```
$ git checkout -- 文件名（后缀）
```

12.删除工作区文件（相当于在工作区手动删除）

```
$ rm 文件名（后缀）
```

13.将“删除”这一修改加到暂存区

```
$ git rm 文件名（后缀）
```

## 五、github

### 添加远程库

#### 操作

1.远程库关联（在关联时需要给远程库指定一个名字，origin是一般的默认远程库名字）

```
$ git remote add origin https://github.com/hellowdjr/learngit.git
```

15.把本地库的（master）分支内容推送到远程库（注意如果本地库内容为空会无法推送）

```
$ git push -u origin 分支名（master）
```

-u参数还会把本地的`master`分支和远程的`master`分支关联起来，在以后的推送或者拉取时就可以简化命令。

16.解除本地库和远程库的绑定（比如删除origin）

```
$ git remote rm origin
```

一个本地库可以与很多个远程库关联，但是要分别取上不同的远程库名字，

#### 学习体会

我在进行推送操作（15）时遇到两个情况：

1.如果使用http地址关联远程库，那么第一次进行push操作时，github网站上会出现来自本地库的关联请求，请求通过后本地库的内容才会在远程库中显示。

2.本地库内容为空时，push操作会报错

### 从远程库克隆

#### 操作

```
$ git clone 远程库地址（http或ssh都可）
```

## 六、分支管理

### 操作

```
$ git branch 分支名
//创建新分支

$ git switch 分支名
//切换分支到指定分支（令head指针指向指定分支）

$ git branch
//查看当前分支

$ git switch -c 分支名
//创建并切换到新分支

$ git merge 分支名
//将指定分支合并到当前分支

$ git branch -d 分支名
//删除分支
```

<img title="" src="file:///D:/Djr/GitNOTE/note_photo/微信图片_20220117112651.png" alt="" width="276" data-align="inline">   Fast forward模式<img title="" src="file:///D:/Djr/GitNOTE/note_photo/微信图片_20220117112241.png" alt="" data-align="inline" width="279">  普通模式合并，合并后有分支历史

```
$ git stash
//保存未提交的工作区现场

$ git stash list
//查看保存的工作现场

$ git stash pop
//恢复工作区现场，并删除stash内容

$ git stash apply   $ git stash drop
//恢复工作区现场       //删除stash内容

可以多次stash，恢复的时候，先用git stash list查看，然后恢复指定的stash，用命令：
$ git stash apply stash@{0}

$ git branch -D 分支名
//强制删除未合并的分支

$ git remote -v
//查看远程库的详细信息

$ git push origin 本地分支名
//将本地分支推送到远程库的对应分支上

$ git checkout -b branch-name origin/branch-name
//在本地创建与远程分支对应的分支

$ git branch --set-upstream branch-name origin/branch-name
//设置本地分支与远程分支的链接

$ git pull
//拉取远程库中已经与当前分支链接的分支的内容，并且自动合并
```

- `master`分支是主分支，因此要时刻与远程同步；

- `dev`分支是开发分支，团队所有成员都需要在上面工作，所以也需要与远程同步；

- bug分支只用于在本地修复bug，就没必要推到远程了，除非老板要看看你每周到底修复了几个bug；

- feature分支是否推到远程，取决于你是否和你的小伙伴合作在上面开发。

疑问

假如dev分支是main的前一个版本，为什么此时在main分支中操作$ git merge dev会显示Already up to date

## 七、标签

### 创建标签

```
$ git tag 标签名
//给当前分支的最近一次commit打标签

$ git tag
//查看所有标签

$ git tag 标签名 commit id
//对某次提交打标签

$ git show 标签名
//查看标签信息

$ git tag -a 标签名 -m "说明文字" commit id
//给某次commit打上标签并附说明文字
```

### 操作标签

```
$ git push origin 标签名
//推送某个标签名到远程某个提交

$ git push origin --tags
//推送所有未推送的标签

$ git tag -d 标签名
//删除本地标签

$ git push origin :refs/tags/标签名
//删除远程标签
```
