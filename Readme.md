# git简介

## 分布式版本控制
git是一个免费的、开源的分布式版本控制系统，可以快速高效地处理从小型到大型的项目。

客户端并不知道提取最新版本的文件快照，而是把代码仓库完整的镜像下来

在管理项目时，存放的不是版本与版本之间的差异，而是索引，可以通过索引找到不同的版本


## 集中式控制系统的分类
集中化版本控制系统诸如CVS，SVN和Perforce。每个人都可以在一定程度上看到其他人在做的事情。

缺点：中央服务器的**单点故障**

存储的是不同版本之间的差异

## git 小历史
Linus 林纳斯·本纳迪克特·托瓦兹  Linux作者github作者

## 本地结构

    
工作区 ——git add———>  暂存区（临时存储） ———git commit———> 本地库（每个历史版本内容）


## 本地库和远程库
### 团队内协作

(经理)本地库 ————————> 远程库 <—————push,clone————— 个人

fork: 复制一个远程库

## 初始化本地库

【1】创建文件夹  即本地仓库  
【2】设置用户名       git config --global user.name "zhonggengjun"   
【3】设置邮箱         git config --global user.email "gjzhongdf@163.com"  
【4】本地仓库的初始化  git init  # return Initialized empty Git repository in D:/GitResp/.git/


## 常用命令
添加文件 add  提交文件 commit  
【1】创建文件  
【2】提交到暂存区  git add <filename>  
【3】提交到本地库  git commit -m "注释说明"  
文件需要放置在本地仓库，否则git不管理，本地仓库需要提交才能管理


## 查看工作区与暂存区的状态
git status

## 查看提交日志
 git log  
 当历史记录过多的时候，查看日志会有分屏效果：下一页：空格键，上一页：b  
 
 使用 git log --pretty=oneline 优化日志输出  
 git log --oneline  再次简化输出  
 使用  git reflog 查看当前版本与之前版本的距离 HEAD@{数字} 其中数字就是距离（步数）  
 

 ## 前进版本后退版本
 git reset --hard [跳到某一步的索引] 工作区的代码会跟着调回指向索引的版本内容  
 git reset --hard [索引]            本地库的指针移动的同时，重置暂存区，重置工作区  
 git reset --mixed [索引]           本地库指针移动的同时，重置暂存区，但是工作区不动  
 git reset --soft [索引]            本地库指针移动的时候，暂存区和工作区都不动  


 ## 找回本地删除的库
 rm  [fname]  
 同步删除操作到暂存区  
 将删除操作同步到暂存区  
 git add [fname]  
 将删除操作同步到本地库  
 git commit [fname]  
 查看日志会发现 这不是物理删除，只需要返回到 对应版本的索引就可以了

## 恢复缓存区被删的库
rm [fname]  
git add [fname]  
git restore [fname]   
或者 通过  git reset --hard HEAD  
git reset --hard [索引]  


## 对比文件的差异
fname 提交后做了修改，比对前后两者的差异  
git diff fname      比较工作区与暂存区的差异  git diff 比对所有文件的差异  
git diff [历史版本]  fname 比对具体暂存区与工作区的文件差异 

## 分支
在版本控制中，使用多条线同时推进多个任务，多条线就是说多个分支  
不同的分支开发独立的新功能  

查看分支 git branch -V  
创建分支 git branch branch_name  
切换分支 git checkout branche_name

## 合并分支到主分支
【1】进入主分支  
【2】将子分支合并  git merge branch_name, 如果同一文件的同一行都有内容，会报错与冲突  
终端界面显示： (master|MERGING)  表示处于合并状态  
解决:  
根据需求人为决定删减内容 

git add 冲突文件名  
git commit -m "必要的备注"  
提交本地库时候，不要加文件名


## 与远程库交互
【1】 出事换文地库 git init  
【2】 上传文件 git add git commit   
【3】 登录github 创建新的仓库

远程库的地址： https://github.com/coallar/GItResp2.git  
通过Git本地将地址保存，即命名别名  
查看别名 git remote -v  
新增别名 git remote add [别名] [远程库地址]  

## 推动操作
git push [远程库地址or别名]  分支
