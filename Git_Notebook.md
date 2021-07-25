---
title: "Git_Notebook"
date: 2021-04-01T16:44:38+08:00
draft: false
tag: ["Tools","Git"]
categories: ["Tools"]
---

# Git_Notebook

# Debian/Ubuntu安装Git

```bash
# For the latest stable version for your release of Debian/Ubuntu
sudo apt install git
# For Ubuntu, this PPA provides the latest stable upstream Git version
sudo add-apt-repository ppa:git-core/ppa
sudo apt update
sudo apt install git
```

## 使用git的最小配置
```bash
git config --global user.name "<MyName>"
git config --global user.email "<MyEmail>"
```

## git config的三个作用域

```bash
# --local --global --system缺省等同于--local
git config --local	# --local只对某个仓库有效
git config --global	# --global对当前用户所有的仓库有效
git config --system	# --system对系统所有登录的用户有效
```

## 显示config的配置， 加 --list

```bash
git config --list --local
git config --list --global
git config --list --system
```

## 建Git仓库

两种场景：

1. 把已有的项目代码纳入Git管理

   ```bash
   cd <ProjectFile>
   git init
   ```

2. 新建的项目直接用Git管理

   ```bash
   cd <ProjectParentFile>
   git init <ProjectFileName>	# 会在当前路径下创建和项目名称同名的文件夹
   cd <ProjectFileName>
   ```

## Git仓库三大区：

* Working Directory(工作区)

* Stage(暂存区)

* Repository(版本库)

  ```bash
  # git version 2.x
  git add <files>	# 把文件添加到Stage
  git add -u # 仅监控已经被add的文件（即tracked file），他会将被修改或删除的文件提交到暂存区。add -u 不会提交新文件（untracked file）
  git add --ignore-removal	# 监控工作区的状态树，使用它会把工作时的所有变化提交到暂存区，包括文件内容修改(modified)以及新文件(new)，但不包括被删除的文件。
  git add .	# 监控工作区的状态树，使用它会把工作时的所有变化提交到暂存区，包括文件内容修改(modified)以及新文件(new)，包括被删除的文件。
  git commit -m '<Comment>'	# 把文件提交到Repository
  ```

## git 打标签

* 附注标签

```bash
git tag
git tag -a v<版本号+others> -m "version <版本号>"
git show v<版本号+others>
```

* 轻量标签

```bash
git tag v<版本号+others>
git show v<版本号+others>
```



## 给文件重命名的方法

  ```bash
  # 法一：
  mv <file1> <file2>
  git add <file2>
  git rm <file1>
  git commit -m 'Modified fileName'

  git reset --hard	# 危险操作：该操作会把工作区与暂存区的修改都删掉

  # 法二：
  git mv <file1> <file2>
  git commit -m 'Modified fileName'
  ```

## 通过git log查看版本演变的历史

  ```bash
  git log
  git log --oneline
  git log -n<num> --oneline
  git branch -av
  git check out -b <BranchName>	# 创建并切换到<BranchName>分支上
  git log --all --graph
  git log --oneline --all -n<num> --graph
  ```

## 探秘 `.git` 文件

  [参考](https://juejin.cn/post/6844903986839945229)

  * config: config 文件顾名思义就是包含项目特有的配置选项

    ```bash
    cat .git/config
    ```

  * HEAD: 此文件永远存储当前位置指针，指向当前工作区的分支

    ```bash
    cat .git/HEAD
    ```

  * logs: logs就是用来记录操作信息的

  * refs: refs文件夹存储着分支和标签的引用

    ```bash
    cd .git/refs/ && cd heads/	# .git/refs/HEAD 存储着各个分支的引用
    cd .git/refs/ && cd tags/	# .git/refs/tags 储存着各个标签的引用 tag指向一个commit

    git cat-file -t + <hash值>	# 可以查看hash对应的类型
    git cat-file -p + <hash值>	# 可以查看hash对应的内容
    ```

* objects: 在初始化的时候，objects里有两个空的文件夹：info和pack。Git 往磁盘保存对象时默认使用的格式叫松散对象 (loose object) 格式，当你对同一个文件修改哪怕一行，git 都会使用全新的文件存储这个修改了的文件，放在了objects中。Git 时不时地将这些对象打包至一个叫 packfile 的二进制文件以节省空间并提高效率，当版本库中有太多的松散对象，或者你手动执行 `git gc` 命令，或者你向远程服务器执行推送时，Git 都会这样做。

## commit tree blob三者之间的关系

[参考](https://juejin.cn/post/6844904190058184718)

## 分离头指针（detached HEAD）情况下的注意事项

* detached HEAD(分离头指针的状态)：HEAD没有指向任何一个分支

* git进入到分离头指针状态：

  ```bash
  git checkout <commit_Hash> && git status
  ```

* 分离头指针的情况下抛弃变更：

  ```bash
  git checkout <branch_Name>
  ```

* 分离头指针情况下为该变更创建分支：

  ```bash
  git checkout -b <new-branch-name> <commit_Hash>
  ```


## HEAD与branch

```bash
git diff HEAD HEAD~<n>	# 前面n阶祖先
git diff HEAD HEAD^	# 一个^表示一阶祖先
```

## 怎么删除不需要的git分支

```bash
git branch -d <branchName>
git branch -D <branchName>
```

## 修改commit的message

```bash
git commit -amend
```

## 修改老旧的commit的message

```bash
git rebase -i <被变更的commit的父commit的hash>
```

把pick改为`reword`

## 怎么把连续的多个commit整理成一个

```bash
git rebase -i <连续的多个被变更的commit的父commit的hash>
```

把需要合并的commit的 `pick` 改为 `squash`

## 怎么把间隔的几个commit整理成一个

```bash
git rebase -i <需要合并的最早的那个commit的hash>
```

把最早的那个commit 的hash 添加到顶部行(pick <要合并的最早的那个commit的hash>) ，把需要合并的commit的行移动到一块 并把`pick`改为`squash`

## 怎么比较暂存区和HEAD所含文件的差异

```bash
git diff --cached
git diff -- <fileName1> <fileName2>	# 查看工作区上<fileName1> <fileName2> 与暂存区的<fileName1> <fileName2>的区别
```

## 如何让暂存区恢复成与HEAD的一样(取消暂存)

```bash
git reset HEAD
```

## 如何让工作区的文件恢复和暂存区的一样

```bash
git checkout -- <fileName> <fileName1>
```

## 怎么取消暂存区部分文件的变更

```bash
git reset HEAD -- <fileName> <fileName1>
```

## 消除最近几次commit

```bash
git reset --hart <需要回跳到的commit的hash值>
```

## 查看不同提交的指定文件的差异

```bash
git diff <branchNameOne> <branchNameTwo>	# 查看两个分支的所有差异
git diff <branchNameOne> <branchNameTwo> -- <fileName>	# 查看两个分支指定文件<fileName>的差异
git diff <branch_hash_One> <branch_hash_Two> -- <fileName>	# 查看两个分支指定文件<fileName>的差异
```

## 正确删除文件的方法

```bash
# 法一：
rm <fileName> && git rm <fileName>
# 法二：
git rm <fileNameOne> <fileNameTwo>
```

## 开发中临时加塞了紧急任务怎么处理

```bash
git diff	# 查看工作区有什么不同
git stash	# Saved working directory
git stash list	# 查看stash列表
git stash pop	# 起到两个作用： 1. 将stash保存的内容保存回工作目录 2，删除改stash保存的信息
git stash apply	# 起到两个作用： 1. 将stash保存的内容保存回工作目录 2. 该stash保存的信息还在
```

##  指定不需要Git管理的文件(编辑`.gitignore文件`)

`*`: 通配符
`/`: 该文件夹下的所有文件都不要纳入git版本控制系统中  注意：带`/`与不带`/`是不一样的，不带`/`说明符合该匹配的文件或符合该匹配的文件夹都被忽略，带`/`说明只有符合该匹配的文件夹被忽略

## 将Git仓库备份到本地

1. 常用的传输协议
   * 本地协议(1):`/path/to/repo.git` 说明：哑协议
   * 本地协议(2): `file:///path/to/repo.git` 说明：智能协议
   * http/https协议: `http://git-server.com:prot/path/to/repo.git`及`https://git-server.com:port/path/to/repo.git` 说明：平时接触到的都是智能协议
   * ssh协议: `user@git-server.com:path/to/repo.git` 说明：工作中最常用的智能协议
2. 哑协议与智能协议区别
   * 直观区别：哑协议传输进度不可见，智能协议传输可见
   * 传输速度：智能协议比哑协议传输速度快

```bash
git clone --bare <RepoURL>	# --bare: clone一个不带工作区的仓库,这样以后做push操作的时候方便一点
git clone <RepoURL> <文件名>	# 把仓库clone到<文件名下>
git remote -v	# 与远端仓库关联 会显示需要读写远程仓库使用的 Git 保存的简写与其对应的 URL
git remote add <ShortName> <RepoURL>
git push --set-upstream <ShortName> <BranchName>
git push <ShortName> --all	# 所有分支都被push
# 如果远程仓库的某些分支拒绝推送
# 法一：
git pull <ShortName> <BranchName>	# git pull 等于 git fetch + git merge
# 法二：
git fetch <ShortName> <BranchName>
# 如果本地仓库分支不是基于远程仓库分支做的修改
git merge --allow-unrelated-histories <ShortName/BranchName>
```

## git push 常见错误及解决办法

使用 `git push -u origin main`出错(`error:failed to push some refs to 'https://github.com/*****/xxx.git'`)
原因：
 github上创建远程仓库的时候选择添加README.md文件,
 github中的README.md文件不在本地代码目录中;

Solutions:

```bash
# 法一：（会导致commit的hash值发生变化）
# 1.执行将代码合并
git pull --rebase origin main
# 2.执行
git push -u origin main
# 法二：
git merge --allow-unrelated-histories <ShortName/BranchName>
```
[参考](https://blog.csdn.net/qq_29393273/article/details/90691905)

## 不同人修改了不同文件要怎么处理

```bash
git config --add --local user.<name>
git checkout -b <branchName> <remoteBranchName>	# 基于远程分支<branchName> 创建远程分支<remoteBranchName> 并切换到<branchName>上
git add -u
git config --local -l
git merge <ShortName/BranchName>	# 不同人修改了不同文件
```

## 同时变更了文件名和文件内容怎么处理

```bash
git pull	# git会智能的感知到文件名的变化
```

## 把同一文件改成了不同的文件名怎么处理

```bash
git push	# 报错
git status
git rm <原文件名>
git status
git add <修改后的文件名>
git rm <需要保留的文件名>
git commit -am ""
```

## 禁止向集成分支执行变更历史的操作

## github高级搜索

[Official Docs](https://docs.github.com/en/github/searching-for-information-on-github)

* `<keyword> in readme`: 在readme中搜索
* `<keyword> star > <num> `: 搜索star大于多少的项目
*  `<keyword> filename:<filename>`: 项目里需要包括该文件

## Github分支集成策略

* Allow merge commits: Add all commits from the head branch to the base branch with a merge commit.
* Allow squash merging: Combine all commits from the head branch into a single commit in the base branch.
* Allow rebase  merging: Add all commits from head branch onto the base branch individually.

## Github启用issue跟踪需求和任务

## Github用project管理issue

## Github项目内部怎么实施 code review

## Github怎么保证集成的质量（CI/CD）

* Codecov
* TravisCI

## Github怎么把产品包发布到Github上

## Github怎么给项目增加详细的指导文档

## github 配置公私钥

why: 配置了公私钥后对远程分支进行操作不需要输入密码

```bash
# Step 1:检查本地是否有公钥
ssh-keygen -t rsa -C "<MyEmail>"
# Step 2: 将~/.ssh/id_rsa.pub 复制并粘贴进Github的ssh key中
```

## 把本地仓库同步到GitHub上
