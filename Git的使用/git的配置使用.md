## 1 镜像源下载git的环境

## 2 一般使用Git Bash启动git（操作为linux的命令）

## 3 查看配置

`git config -l`

```cpp
查看系统config
git config --system --list
查看当前用户配置
git config --global --list
```

**Git相关的配置文件：**

1）Git\etc\gitconfig  ：Git 安装目录下的 gitconfig     --system 系统级

2）C:\Users\Administrator\ .gitconfig    只适用于当前登录用户的配置  --global 全局

# 4 设置用户名与邮箱（用户标识，必要）

当你安装Git后首先要做的事情是设置你的用户名称和e-mail地址。这是非常重要的，因为每次Git提交都会使用该信息。它被永远的嵌入到了你的提交中：

```cpp
git config --global user.name "lucien"  #名称
git config --global user.email 1020263522@qq.com   #邮箱
```

## 5 本地仓库搭建

### 5.1 全新的仓库

#### 5.1.1 创建全新的仓库，需要使用GIT管理的项目的根目录执行

`git init`

#### 5.1.2 执行后出现.git目录的文件夹，关于版本的所有信息都在

### 5.2 克隆远程仓库

 将远程服务器上的仓库完全镜像一份至本地

```cpp
# 克隆一个项目和它的整个代码历史（版本信息）
$ git clone [url] 路径
```

## 6 Git的文件操作

* Untracked: 未跟踪, 此文件在文件夹中, 但并没有加入到git库, 不参与版本控制. 通过git add 状态变为Staged.
* Unmodify: 文件已经入库, 未修改, 即版本库中的文件快照内容与文件夹中完全一致. 这种类型的文件有两种去处, 如果它被修改, 而变为Modified. 如果使用git rm移出版本库, 则成为Untracked文件
* Modified: 文件已修改, 仅仅是修改, 并没有进行其他的操作. 这个文件也有两个去处, 通过git add可进入暂存staged状态, 使用git checkout 则丢弃修改过, 返回到unmodify状态, 这个git checkout即从库中取出文件, 覆盖当前修改 !
* Staged: 暂存状态. 执行git commit则将修改同步到库中, 这时库中的文件和本地文件又变为一致, 文件为Unmodify状态. 执行git reset HEAD filename取消暂存, 文件状态为Modified

查看指定文件的状态

git status [filename]

查看所有文件状态

git status

添加所有文件到暂存区

git add .

提交暂存区中的内容到本地仓库 -m 提交信息

## 7 忽略文件

有些时候我们不想把某些文件纳入版本控制中，比如数据库文件，临时文件，设计文件等

在主目录下建立".gitignore"文件，此文件有如下规则：

1. 忽略文件中的空行或以井号（#）开始的行将会被忽略。
2. 可以使用Linux通配符。例如：星号（*）代表任意多个字符，问号（？）代表一个字符，方括号（[abc]）代表可选字符范围，大括号（{string1,string2,...}）代表可选的字符串等。
3. 如果名称的最前面有一个感叹号（!），表示例外规则，将不被忽略。
4. 如果名称的最前面是一个路径分隔符（/），表示要忽略的文件在此目录下，而子目录中的文件不忽略。
5. 如果名称的最后面是一个路径分隔符（/），表示要忽略的是此目录下该名称的子目录，而非文件（默认文件或目录都忽略）。

```
#为注释
*.txt        #忽略所有 .txt结尾的文件,这样的话上传就不会被选中！
!lib.txt     #但lib.txt除外
/temp        #仅忽略项目根目录下的TODO文件,不包括其它目录temp
build/       #忽略build/目录下的所有文件
doc/*.txt    #会忽略 doc/notes.txt 但不包括 doc/server/arch.txt
```

## 8 使用github

### 8.1 github添加SSH公钥

### 8.2 git的使用及上传至远程仓库

新建git项目

git init

创建新的工程项目或将已有的项目加入到.git文件夹下，注意尽量包括README文件和.gitgnore文件

* 添加到暂存区，git add .
* commit 提交，git commit -m""
* push到远程仓库, git push

8.3 git分支

git分支中常用指令：

```
# 列出所有本地分支
git branch


# 列出所有远程分支
git branch -r


# 新建一个分支，但依然停留在当前分支
git branch [branch-name]


# 新建一个分支，并切换到该分支
git checkout -b [branch]


# 合并指定分支到当前分支
$ git merge [branch]


# 删除分支
$ git branch -d [branch-name]


# 删除远程分支
$ git push origin --delete [branch-name]
$ git branch -dr [remote/branch]
```
