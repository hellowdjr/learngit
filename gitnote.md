1.git自报家门：

```
$ git config --global user.name "Your Name"
$ git config --global user.email "email@example.com"
```



2.建立git仓库：创建一个文件夹并右键   点击Bash  输入:git init



3.将文件添加到暂存区：

```
git add 文件名（有后缀）
```

​                                                        //注意文件名不能有空格



4.提交暂存区的文件到当前分支：

```
$ git commit -m "本次提交的标签"
```

​                                                                                                     //注意commit会把暂存区的所有文件提交



5.查看仓库状态：

```
$ git status
```



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

$ git reset --hard e475af              //e475af是版本号的前几位                                          即commit id
```



9.查看版本提交和回退的命令的历史记录

```
$ git reflog
```

  这个命令可以用于查找回退前的版本号（commit id）  



10.撤销暂存库中的修改(unstage)

```
$ git reset HEAD 文件名（后缀）
```



11.丢弃工作区的修改，使文件回到最近一次git add或 git commit的状态

```
$ git checkout -- 文件名（后缀）
```



12.
