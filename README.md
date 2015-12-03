# Learn_Git
这是 Git权威指南(蒋鑫 著) 的笔记

## 配置 ##
级别|说明
:-:|:-:
本地级(默认)|直接在项目的.git/config里面进行配置
用户级(--global)|在当前计算机用户的配置文件里进行配置: C:\Users\Administrator\.gitconfig
系统级(--system)|D:\Program Files (x86)\Git\etc\.gitconfig


### 获取属性 ###
	git config --global user.name, 这是获取全局级别的user.name
	当然你也可以直接打开相应的文件去查看了...
	
### 设置属性 ###
	git config key value, 当然也可以直接打开文件进行修改
对于 git config a.b.c.d hehe(这默认是本地修改)的结果是
```ini
[a "b.c"]
	d = hehe
```

#### 注意 ####
user.name和user.email用于记录提交者的信息

### 杂 ###
使用 git config -e --global 会打开git自带的vi对用户级的文件进行配置修改
### git别名 ###
git config --system alias.st status
git config --system alias.ci commit


### 例子 ###
>git config --global user.name "xzchaoo",设置全局级别的user.name


## 状态 ##
列出当前工作区的状态
git status

参数|说明
:-:|:-:
s|简短模式
b|显示当前工作分支的名称

### 简短模式 ###
git status -s
第一列的M表示当前的缓冲区与当前的HEAD有差别
第二列的M表示当前工作区与缓冲区的文件有差别


## 搜索 ##
git grep 关键字

## 克隆 ##

git clone

git fetch
	如果在当前工作区已经克隆过一次了,可以使用fetch 再次获取新版本(如果该仓库进行了更新的话)

### 例子 ###
git clone https://github.com/takahirom/PreLollipopTransition, 将该仓库复制到当前目录下的PreLollipopTransition


## TAG 里程碑 ##

## 日志 ##

log

参数|作用
:-:|:-:
pretty|fuller,oneline,raw
stat|打印出前后两次的不同之处
graph|图形
online|一行


## 杂 ##
> git也可以对svn仓库进行操作

## 比较 ##
diff:查看两者之间的不同
至于这"两者"可以是很多
默认是查看工作区和缓冲区的差别

git diff 查看当前工作区和缓冲区的区别
git diff HEAD 查看当前工作区和HEAD的差别
git diff --cached 查看当前缓冲区和HEAD的差别

参数|说明
:-:|:-:
cached/staged|比较缓冲区与HEAD的区别

## HEAD的理解 ##
当前版本库的头指针
HEAD通常指向refs/heads/master
而master通常指示了一次提交

## reset ##
修改当前的HEAD,到指定的状态
git reset HEAD <file>: 修改缓冲区的<file>文件为HEAD的<file>文件,即将缓冲区里的<file>文件撤出去

git reset [--soft | --mixed | hard] [<commit>]
--soft将HEAD指向<commit>
--mixed,将HEAD指向<commit>,缓冲区更新为<commit>的内容,这是默认行为
--hard, 将HEAD指向<commit>,缓冲区和工作区更新为<commit>的内容
所以git reset,会用HEAD覆盖缓冲区的内容,相当于取消缓冲区里的修改


	
## checkout ##
git checkout -- 2.txt: 将缓冲区里的2.txt放到工作区
git checkout HEAD -- 1.txt 用HEAD的1.txt替换工作区和缓冲区

git checkout 某个版本号
可能进入分离头模式
,也就是说当前的HEAD指向了某个具体的版本号而不是master

git checkout
	显示三个区域的差别
git checkout 某分支名称
HEAD的指向会发生变化
切换到某个分支,三个区域的内容都会更新

git checkout 新的分支名 分支的起点
用于简单的创建一个新的分支 并且切换到它
当处于分离头模式的时候,行为不再拘束于master

git checkout master
	切换到master这个点上



## rm ##
git rm --cached 1.txt: 删除缓冲区中的1.txt, 对工作区不会产生影响


## clean ##
git clean -n 干跑
git clean -fd 删除当前路径下的所有没有被追踪的文件

## branch ##
git branch 查看当前的分支名称
-v
## reflog ##
.git/logs/refs/heads/master里面记录了master分支的修改记录,每一次你的master指向发生改变的时候,这里都会有记录
可以直接打开它查看
或者使用git reflog show master 进行查看

## merge ##
将当前分支与制定分支合并

## 杂 ##
git rev-parse master
	查看master分支对应的提交
git cat-file commit HEAD
	查看HEAD对应的提交的内容
使用master代表分支master中的最新提交
使用HEAD代表版本库中最近的一次提交
^可以表示父提交
HEAD^ HEAD^^ a573106^2 相当于HEAD^^

git reset --hard HEAD^
将master指向HEAD^,并且由于指定了--hard,所以工作区和缓冲区的内容页被替换成HEAD^

git show acc2f69 显示这个提交的信息

## stash ##
**stash只会跟踪那些被管理的文件**
git stash 保存当前工作区和缓冲区,然后将工作区和缓冲区都恢复到HEAD
list
pop 弹出最近一次保存,恢复工作区和缓冲区
	--index 除了恢复工作区还尝试恢复缓冲区 否则只有工作区被恢复
apply 用最近一次保存恢复工作区和缓冲区,但不进行弹出
clear 弹出最近一次保存,但不进行恢复,相当于删除最近一次保存
git stash [save [-k] [-q] [message]]
	-k stash执行之后不清空缓冲区 -q安静

tag
describe 用tag和sha1描述当前的版本
git ls-files
	列出位于缓冲区的文件

git ls-files --with-tree=HEAD^
git cat-file -p HEAD^:1.txt
恢复文件
git cat-file -p HEAD^:1.txt > 1.txt 从HEAD^1恢复1.txt到工作区
git checkout HEAD^1 -- 1.txt
mv

git log --onlne --decorate -3
git add -i 进入交互模式


"ls" 和 "git ls"的区别
git add -u
	将本地所有的改动和删除添加到缓冲区里
	设计到的文件只有被git管理到的文件

git cat-file -p HEAD~1:1.txt
git show HEAD~1:1.txt
	显示文件的内容

git checkout HEAD~1 -- 1.txt
	将HEAD~1里的1.txt复制到缓冲区和工作区


文件忽略 通过.gitignore文件
!lib.a 代表不忽略
/TODO 当前目录下的!文件!
/TODO/ 当前目录下的!文件夹!
1.txt 所有叫做1.txt的 不管目录多深
/1.txt 当前目录下的1.txt
# 忽略自己
.gitignore

# 忽略当前目录下的1.txt
/1.txt


# 忽略所有叫做222.txt的
222.txt

# 忽略所有temp目录下的全部
temp/**

ceshi/*.bak

ceshi/**/3.txt


# 10.9 文件归档 #
主题数据库的建立过程

#  #
## cherry-pick ##
可以将某次提交在当前的版本上进行重放
git cherry-picker <commit>
只是重新执行了这个动作而已, 因此相当于是一次新的提交

## rebase ##
	--continue
	--abort
	--skip
git rebase [--onto <newbase>] <from> <to>
	将<from>到<to>的修改重放到<newbase>(默认是<from>)
	然后将HEAD指向最终结果
	如果from并不是to的祖先, 那么会设法找到他们的公共祖先来代替
	from, to之间夹了多少修改可以使用
	git log from..to 来查看
	

# 13 #
## 多个仓库 ##
clone pull push fetch

默认情况下, 只允许push到一个裸仓库(没有工作区的仓库)
git clone --bare ...
git clone --mirror ...
使用clone的时,会对源仓库进行注册

git init --bare

所以一般是到第二个仓库里进行 git pull 以进行同步

git push url master:master
将本地的master推到url的master

以 refs/heads/ 开头的是分支
以 refs/remotes/ 开头的是远程分支在本地的映射
以 refs/tags/ 开头的是里程碑

# 14 #
git fsck
git prune
git reflog
git gc 自动整理

# 15 #
pull = fetch + merge

# 16 冲突解决 #
关键是要看得懂git diff的格式
## diff格式 ##
http://www.ruanyifeng.com/blog/2012/08/how_to_read_diff.html

git blame 1.txt 可以追溯1.txt每一行的来源
一般来说当你进行push的时候, 要求你的基版本与服务端的master对应, 这样才能进行快进式提交
如果不一致的时候, 会要求你先git pull
git pull  = git fetch + git merge
如果merge成功, 那没什么好说的 ...
如果merge失败, 那么需要手动解决冲突
	在这个时候你的冲突文件比如 1.txt 里的已经被修改成 形如:
	<<<<<<< HEAD
	我是2 2
	=======
	我是2 1
	>>>>>>> ff0b952bf3f5125e98e9bdd762926d839c663b3e
	你需要手动解决他们, 如果有100处, 这样的内容, 然后你改了3处, 发现太累了, 想放弃本次合并 回到merge之前
	那么使用 merge --abort 放弃本次merge

# 17 里程碑 #
里程碑实际上就是指向一次提交, 要唯一确定一个提交的话需要有它的sha1, 但是不好记 于是就有tag
git tag 查看里程碑列表
git describe

## 创建里程碑 ##
git tag -m "描述信息" 将当前所在的HEAD创建一个里程碑 <tagname> [<commit>]
	-m
	-d <tagname> 删除里程碑

## 上传里程碑 ##
一般情况下里程碑不会被push到仓库
git push origin mytag 将本地的mytag推到origin的mytag
git push origin refs/tags/*
git ls-remote origin my*

## 删除远程里程碑 ##
git push <remote_url> :<tagname> 对没错 就是要这样写, 将 空 推送到远程的tagname

# 18 分支 #
git branch <branch-name> 以当前commit为基础, 建立一个分支
git branch查看当前分支
	-v 输出sha1
	-d <branch-name> 删除分支
	-b <branch-name> [<commit>] 以<commit>为起点建立一个分支

git push origin hello-1.x 推到origin

git format-patch a..b
将从a到b的变化打成一个补丁


# 19 远程版本库 #
git ls-remote 查看远程有哪些分支
git show-ref 显示全部的本地引用
git branch -r 查看远程分支
git checkout -b <branch-name> [<start-point>]
	以start-point(默认为HEAD)为起点, 建立分支branch-name
基于远程branch创建分支的话, 会有追踪功能
基于本地分支1创建分支2的话, 不会有追踪功能
	该分支1是基于某个远程分支的, 并且在创建分支2的时候使用了 --track
	才会让追踪功能传递过来

git remote -v 查看远程版本库

注册远程版本库
git remote add <remote-name> <url>
git remote rename <old-remote-name> <new-remote-name> 用这个方式重命名, 会自动修改其他地方的引用, 因此比较安全

执行git fetch操作的时候, 默认是从该分支配置的remote和merge处进行fetch操作
见.git目录下的gitconfig文件
```
[branch "master"]
	remote = origin
	merge = refs/heads/master
#	rebase = true
```
git pull默认会执行merge操作 可以修改这个行为为rebase操作, 只需要在上面的配置加上rebase = true

ddbranch.autosetuprebase

git fetch --no-tags fetch默认会获取tag, 取消掉




# 杂 #

reset是修改当前HEAD所指向的分支的内容
checkout是修改当前HEAD内容

git reflog HEAD
	 可以查看最近HEAD最终指向的提交的变化
	
merge合并两个分支
git log --graph --pretty=oneline
git cat-file -p HEAD
	-p 以良好的格式显示HEAD的内容
	-t 显示HEAD的类型

删除多余的文件和文件(未受管理)
git clean -nd
git clean -fd

git rev-parse <object> 可以查看任意object的id
比如master, 其实就是看它是哪个提交

git rev-list --pretty=oneline a..b


git cherry 可以查看本地master比远程master领先的内容
	也就是此时如果执行push, 将会被修改的内容

# 日志 #
git log -1 -m --stat
	可以查看最近一次提交的修改
git log --online --graph -3


# git练习 #
## 例子1 ##
### 描述 ###
1个项目, 2个人完成
	初始化
		main.cpp 里面有10个函数 由2个人完成, 分工见下面
		changelog.txt 由2个人共同完成
		readme.txt 两个人都可以任意改, 没有特殊要求
函数:
	1. int add(int a, int b){}
	2. int sub(int a, int b){}
	3. int mul(int a, int b){}
	4. int div(int a, int b){}
	5. int mod(int a, int b){}
	6. int sum(int from, int to){} 求from+(from+1)+...+to的结果
	7. int jc(int n){} 求n阶乘
	8. int fib(int n){} 斐波那契数列第n项
	9. void about(){} 打印 "Today is a good day."
	10. int abs(int x){}
为了模拟需要, 请大家将这些函数想象是很复杂的函数
1-5由第一个人完成
6-10由第一个人完成
两个人各开一个branch去添加新功能, 每个人一次性可以完成多个函数, 完成之后需要在changelog.txt里面进行一些说明. 然后5个函数可以分多次完成, 每次做完之后要合并到master上
由user1建立main.cpp changelog.txt readme.txt这3个文件的初始内容
主线的master,要做一些无关紧要的提交,以模拟其他的提交

1. 建立裸仓库
	git init --bare eg1
2. user1 clone一个仓库
	git clone ./eg1 ./eg1-1
	设置好name和email
	git config user.name user1
	git config user.email user1@abc.com
	(user2不用做)建立main.cpp changelog.txt readme.txt的初始内容, 并且建立一个里程碑t1,并且push到origin
3. user2 类似

第一天
4. user1以t1为基础建立一个新分支b1, 并且切换到b1
5. user2以t1为基础建立一个新分支b2, 并且切换到b2
6. user1第一次提交完成了add,sub 2个函数, 并且编写changelog, commit 并 push
	但是没有注意到add的实现有问题, 比如写成了 return a+b+1;

6.5. 有一个user3, 往master里随便改了点东西,然后commit,并push

7. user2第一次完成了sum,jc 2个函数, 并且编写changelog, commit 但不 push
	但是没有注意到sum的实现有问题, 比如s初始化为1而不是0

8. user2正确地完成了fib, about, abs 3个函数 ... commit
9. user2发现了它之前的错误,并且进行修正, 现在user2的功能全部正确了, 将该分支的功能合并到master上, 并且删除该分支, 此时master具有了user2的实现功能,并且建立一个里程碑v1.1
	主要是通过rebase
10. user1正确地完成mul, div, mod 3个函数... commit, push,将该分支的功能合并到master上, 并且删除该分支, 此时master具有了user1的实现功能,并且建立一个里程碑t4
11. 过了许久(这期间可能有其他的提交或其他操作, 如果有需要可以模拟一下), 由于user1之前的add实现有问题, 现在被发现了, 由user1从里程碑t4开始建立一个新的分支b3, 然后在这个分支修正add函数 并且进行提交, 合并到master.
12. 现在master就实现了10个功能

HEAD^与HEAD@{1}不一样
HEAD^是指当前HEAD指向的提交的父提交
HEAD@{1}是指HEAD的上一个值
一般commit之后HEAD的值不变(因为它通常都指向master,所以变的是master)
让你checkout,reset的时候HEAD本身就会变化了


# 20 补丁文件交互 #
git format-patch -s a..b
	-s 添加签名
git send-email *.patch


# 24 子模组 #
使用git submodule add url dir
将一个子模组添加到当前的仓库的dir目录下
	该子模组的内容会马上被checkout过来
	假设添加该子模组的时候, 子模组的master的sha1为1...
	
当你clone一个仓库,而这个仓库带有子模组的话, 子模组的具体内容是不会被复制的
可能目录会被clone过来,但是里面没有内容
但是它的一些信息, 比如url是有的, 他们被放在.gitmodules里
.gitmodules被当做是一个普通的文件纳入到仓库里

这时候你需要手动使用 git submodule init进行初始化
	这句话会在.git/config里面填写关于submodule的信息
	
然后使用 git submodule update
	会使得子模组的内容被加载进来
	其实就是将子模组checkout到相应位置
被加载进来的子模组默认都是分离头状态, 并且此时HEAD指向1...
	注意, 如果在update之前, 该子模组的仓库的master已经不是指向1...了
	那么该分离头还是指向1...


# add #
# rm #
# ls-files #
# reset #
# branch #
# remote #
# ls-remotes #
# checkout #
# status #
# log #
# show #
# diff #
# cat-file #
# rev-parse #