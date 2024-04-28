> 下载好git后：

1.git config --global user.email "2357956088@qq.com"

2.git config --global user.name "lds"

3.git init （初始化，会生成一个.git 隐藏文件夹）



git  add 文件名  文件名  文件名(将对应文件添加到暂存区)  /  git add . (将所有文件添加到暂存区) 

 git commit -m "提示信息"  将文件添加到本地仓库



git status 查看有没有更改了但是未提交的文件

git diff 文件名  查看当前位置的文件与仓库中存储的文件有没有区别

git log 查看版本信息

git log --pretty=oneline  查看版本信息(简略版)

HEAD->master 指针，指向的是最新的版本

git  reset -- hard HEAD^  回退到上一个版本

git  reset -- hard HEAD~n   回退到上n个版本   

git  reset -- hard HEAD^~n 回退到上n+1个版本   

git reflog 可以看到所有的历史信息，git log --pretty=oneline只能看到当前指针所指位置及之前的历史信息

git  reset -- hard 版本ID  回退到指定ID号的版本

注：reset针对的是已经commit提交的







> 当修改了一个文件以后发现出错，但是这时还没add，可以使用如下命令回退：

git checkout   --   文件名

> 当已经add了但还没有commit时，适用如下命令回退：

1.git reset HEAD  文件名      去除暂存区中的更改文件

2.git checkout   --   文件名







> 删除工作区的文件，同时也要删除本地仓库中的文件

git rm 文件名

git  commit  -m  "提示信息"

> 删除了工作区的文件，但是是误删，运行如下命令后恢复删除的工作区文件：

git checkout   --   文件名







> 将本地项目与GitHub关联起来

登录github->设置->SSH and GPG keys->点New SSH key->将id_rsa.pub中的秘钥复制到key中，title是描述信息

在电脑C盘的用户中找.ssh文件夹，看里面有没有一个名为id_rsa.pub的文件，

如果没有，在Git Bash 窗口中运行命令 ： ssh-keygen   -t   rsa  -C   "邮箱地址"

> 创建一个仓库

repository->New

在git命令行工具中运行如下命令：

1.git remote add origin https://github.com/Coisinids/-.git

2.git push -u origin master

之后每次写完项目

1.git  add  .

2.git commit -m "提示信息"  

3.git push -u origin master

> 将GitHub上的项目拉取到本地

1.在Code中的SSH中复制地址

2.在git命令行中输入 git   clone    地址

> GitHub配置静态资源服务器(纯前端的展示)

Settings->Pages->将None改为master->点Save





master ：主分支(放已经测试好的，成熟的代码)

git   branch   查看当前项目的所有分支

git   branch   分支名   创建一个分支

git   branch  -d  分支名   删除对应分支(不能删除当前正处在的分支，要先切换到其他分支才能删除)

git   switch    分支名   切换到对应分支

git   switch   -c   分支名   创建一个分支并且切换到这个分支

git   merge    分支名    将对应分支的内容合并到主分支(需要先切换到主分支)，合并的时候默认是以Fast-forward

还有一种合并方式：git   merge   --no-ff   -m  "提示信息"   分支名 (这种方式会在主分支上commit一下，而且会记录已经删除的其他分支的版本信息)

git  log  --graph  --oneline   看到整个时间线





当创建了分支之后，还在主分支master中做修改，之后再将其他分支内容合并到主分支时会出现问题

解决方式：在代码中手动更改，然后再git    add   .      git    commit    -m   "提示信息"







git stash (暂存)

git stash   list( 看到暂存的内容)

git stash   pop (恢复暂存的内容)

这种方法适用于当前分支a的内容不太适合commit，但是需要先到主分支，然后再创建一个新的分支b去修改其他内容的情况，在b分支修改完后，还需要在a分支执行git   cherry-pick   b分支的版本ID（目的是将在b分支修改的内容同步到a分支）





git   pull   (拉取最新的内容到本地文件夹中)