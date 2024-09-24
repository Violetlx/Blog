---
title: Git 安装与使用
tags:
  - - 环境搭建
categories:
  - - 环境搭建
description: Git 安装与使用
top_img: 'https://picx.zhimg.com/v2-7ed54d37ea72cd82ab66a8fa3fc24c14_720w.jpg?source=172ae18b'
cover: 'https://picx.zhimg.com/v2-7ed54d37ea72cd82ab66a8fa3fc24c14_720w.jpg?source=172ae18b'
abbrlink: 386349fe
date: 2024-09-23 17:51:26
---

![ https://pic3.zhimg.com/v2-e34d3ad1878fd02e1b7d7f3052b04171_1440w.jpg?source=172ae18b](https://pic3.zhimg.com/v2-e34d3ad1878fd02e1b7d7f3052b04171_1440w.jpg?source=172ae18b)



# Git 教程

- Git 是一个开源的分布式版本控制系统，用于敏捷高效地处理任何或小或大的项目
- Git 是 Linus Torvalds 为了帮助管理 Linux 内核开发而开发的一个开放源码的版本控制软件
- Git 与常用的版本控制工具 CVS ，Subversion 等不同，它采用了分布式版本库的方式，不必服务器端软件支持



## Git 与 SVN 区别

Git 不仅仅是个版本控制系统，它也是个内容管理系统，工作管理系统等

如果你是一个具有使用 SVN 背景的人，你需要做一定的思想转换，来适应 Git 提供的一些概念和特征

`Git 与 SVN 区别点：`

- **Git 是分布式的，SVN 不是：**这是 Git 和其他非分布式的版本控制系统，例如 SVN ，CVS 等，最核心的区别
- **Git 把内容按元数据方式存储，而 SVN 是按文件：**所有的资源控制系统都是把文件的元信息隐藏在一个类似 SVN ，CVS 等的文件夹里
- **Git 分支和 SVN 的分支不同：**分支在 SVN 中一点都不特别，其实它就是版本库中的另一个目录
- **Git 没有一个全局的版本号，而 SVN 有：**目前为止这是跟 SVN 相比 Git 缺少的最大的一个特征
- **Git 的内容完整性要由于 SVN：**Git 的内容存储使用的是 SHA-1 哈希算法。这能确保代码的完整性，确保在遇到磁盘故障和网络问题时降低对版本库的破坏

![ https://www.runoob.com/wp-content/uploads/2015/02/0D32F290-80B0-4EA4-9836-CA58E22569B3.jpg](https://www.runoob.com/wp-content/uploads/2015/02/0D32F290-80B0-4EA4-9836-CA58E22569B3.jpg)



------



# Git 安装配置

在使用 Git 前我们需要先安装 Git

Git 目前支持 Linux / Unix、Solaris、Mac 和 Windows 平台运行

Git 各平台安装包下载地址为：http://git-scm.com/downloads

![ https://www.runoob.com/wp-content/uploads/2015/02/git-download.png](https://www.runoob.com/wp-content/uploads/2015/02/git-download.png)



## Linux 平台上安装

各大 Linux 平台可以使用包管理器（apt-get 、yum 等）进行安装

Debian / Ubuntu Git 安装最新稳定版本命令为：

```shell
apt-get install git
```

Centos / RedHat 安装命令为：

```shell
yum -y install git-core
```

Fedora 安装命令：

```shell
# yum install git (Fedora 21 及之前的版本)
# dnf install git (Fedora 22 及更高新版本)
```

FreeBSD 安装命令：

```shell
pkg install git
```

OpenBSD 安装命令：

```shell
pkg_add git
```

Alpine 安装命令：

```shell
apk add git
```



## 源码安装

我们也可以在官网下载源码包来安装，最新源码包下载地址：https://mirrors.edge.kernel.org/pub/software/scm/git/。

![img](https://www.runoob.com/wp-content/uploads/2015/02/git-source.png)

也可以在 GitHub 上克隆源码包：

```shell
git clone https://github.com/git/git
```

解压安装下载的源码包：

```shell
$ tar -zxf git-1.7.2.2.tar.gz
$ cd git-1.7.2.2
$ make prefix=/usr/local all
$ sudo make prefix=/usr/local install
```



## Windows 平台安装

在 Windows 平台上安装 Git 同样轻松，有个叫做 msysGit 的项目提供了安装包，可以到 GitHub 的页面上下载 exe 安装文件并运行：

安装包下载地址：https://gitforwindows.org/

直接官网下载也可以：https://git-scm.com/download/win。

![img](https://www.runoob.com/wp-content/uploads/2015/02/git-win.png)

下载后，双击安装包，打开界面如下所示，点击 "next" 按钮开始安装：

![img](https://www.runoob.com/wp-content/uploads/2015/02/20140127131250906)

完成安装之后，就可以使用命令行的 git 工具（已经自带了 ssh 客户端）了，另外还有一个图形界面的 Git 项目管理工具。

在开始菜单里找到 **"Git"->"Git Bash"**，会弹出 Git 命令窗口，你可以在该窗口进行 Git 操作。

**使用 winget 工具**

如果你已经安装了 winget，可以使用以下命令来安装：

```shell
winget install --id Git.Git -e --source winget
```



## Mac 平台上安装

通过 Homebrew 安装：

```shell
brew install git
```

如果您想要安装 git-gui 和 gitk（git 的提交 GUI 和交互式历史记录浏览器），您可以使用 homebrew 进行安装：

```shell
brew install git-gui
```

也可以使用图形化的 Git 安装工具，下载地址为：

https://sourceforge.net/projects/git-osx-installer/

安装界面如下所示：



![img](https://www.runoob.com/wp-content/uploads/2015/02/18333fig0107-tn.png)



## Git 配置

Git 提供了一个叫 `git config` 的命令，用来配置或读取相应的工作环境变量。

这些环境变量，决定了 Git 在各个环节的具体工作方式和行为。

这些变量可以存放在一下三个不同的地方：

- `/etc/gitconfig` 文件：系统中对所有用户都普遍适用的配置。若使用 `git config` 时用 `--system` 选项，读写的就是这个文件。
- `~/.gitconfig` 文件：用户目录下的配置文件只适用于该用户。若使用 `git config` 时用 `--global` 选项，读写的就是这个文件。
- 当前项目的 Git 目录中的配置文件（也就是工作目录中的 `.git/config` 文件）：这里的配置仅仅针对当前项目有效。每一个级别的配置都会覆盖上层的相同配置，所以 `.git/config` 里的配置会覆盖 `/etc/gitconfig` 中的同名变量。

在 Windows 系统上，Git 会找寻用户主目录下的 .gitconfig 文件。主目录即 $HOME 变量指定的目录，一般都是 C:\Documents and Settings\$USER。

此外，Git 还会尝试找寻 /etc/gitconfig 文件，只不过看当初 Git 装在什么目录，就以此作为根目录来定位。

### 用户信息

配置个人的用户名称和电子邮件地址，这是为了在每次提交代码时记录提交者的信息：

```shell
git config --global user.name "runoob"
git config --global user.email test@runoob.com
```

如果用了 **--global** 选项，那么更改的配置文件就是位于你用户主目录下的那个，以后你所有的项目都会默认使用这里配置的用户信息。

如果要在某个特定的项目中使用其他名字或者电邮，只要去掉 --global 选项重新配置即可，新的设定保存在当前项目的 .git/config 文件里。

### 文本编辑器

设置 Git 默认使用的文本编辑器,一般可能会是 Vi 或者 Vim，如果你有其他偏好，比如 VS Code 的话，可以重新设置：

```shell
git config --global core.editor "code --wait"
```

### 差异分析工具

还有一个比较常用的是，在解决合并冲突时使用哪种差异分析工具。比如要改用 vimdiff 的话：

```shell
git config --global merge.tool vimdiff
```

Git 可以理解 kdiff3，tkdiff，meld，xxdiff，emerge，vimdiff，gvimdiff，ecmerge，和 opendiff 等合并工具的输出信息。

当然，你也可以指定使用自己开发的工具，具体怎么做可以参阅第七章。

### 查看配置信息

要检查已有的配置信息，可以使用 **git config --list** 命令：

```shell
$ git config --list
http.postbuffer=2M
user.name=runoob
user.email=test@runoob.com
```

有时候会看到重复的变量名，那就说明它们来自不同的配置文件（比如 /etc/gitconfig 和 ~/.gitconfig），不过最终 Git 实际采用的是最后一个。

这些配置我们也可以在 **~/.gitconfig** 或 **/etc/gitconfig** 看到，如下所示：

```shell
vim ~/.gitconfig 
```

显示内容如下所示：

```shell
[http]
    postBuffer = 2M
[user]
    name = runoob
    email = test@runoob.com
```

也可以直接查阅某个环境变量的设定，只要把特定的名字跟在后面即可，像这样：

```shell
$ git config user.name
runoob
```

### 成 SSH 密钥（可选）

如果你需要通过 SSH 进行 Git 操作，可以生成 SSH 密钥并添加到你的 Git 托管服务（如 GitHub、GitLab 等）上。

```shell
ssh-keygen -t rsa -b 4096 -C "your.email@example.com"
```

按提示完成生成过程，然后将生成的公钥添加到相应的平台。

### 验证安装

在终端或命令行中运行以下命令，确保 Git 已正确安装并配置：

```shell
git --version
git config --list
```



------



# Git 工作流程

下图展示了 Git 的工作流程：

![img](https://www.runoob.com/wp-content/uploads/2015/02/git-process.png)



## 1.克隆仓库

如果你要参与一个已有的项目，首先需要将远程仓库克隆到本地：

```sh
git clone https://github.com/username/repo.git
cd repo
```

## 2.创建分支

为了避免直接在 main 或 master 分支上进行开发，通常会创建一个新的分支：

```sh
git checkout -b new-feature
```

## 3.工作目录

在工作目录中进行代码编辑、添加新文件或删除不需要的文件。

## 4.暂存文件

将修改过的文件添加到暂存区，以便进行下一步的提交操作：

```sh
git add filename
# 或者添加所有修改的文件
git add .
```

## 5.提交更改

将暂存区的更改提交到本地仓库，并添加提交信息：

```sh
git commit -m "Add new feature"
```

## 6.拉取最新更改

在推送本地更改之前，最好从远程仓库拉取最新的更改，以避免冲突：

```sh
git pull origin main
# 或者如果在新的分支上工作
git pull origin new-feature
```

## 7.推送更改

将本地的提交推送到远程仓库：

```sh
git push origin new-feature
```

## 8.创建 Pull Request (PR)

在 GitHub 或其他托管平台上创建 Pull Request，邀请团队成员进行代码审查，PR 合并后，你的更改就会合并到主分支。

## 9.合并更改

在 PR 审核通过合并后，可以将远程仓库的主分支合并到本地分支：

```sh
git checkout main
git pull origin main
git merge new-feature
```

## 10.删除分支

如果不再需要新功能分支，可以将其删除：

```sh
git branch -d new-feature
```

或者从远程仓库删除分支：

```sh
git push origin --delete new-feature
```



------



# Git 工作区、暂存区和版本库

## 基本概念

我们先来了解一下 Git 工作区、暂存区和版本库概念：

- **工作区：**就是你在电脑里能看到的目录。
- **暂存区：**英文叫 stage 或 index 。一般存放到 `.git` 目录下的 index 文件 `(.git / index)` 中，所以我们把暂存区有时也叫索引 `(index)`。
- **版本库：**工作区有一个隐藏目录 `.git` ，这个不算工作区，而是 Git 的版本库。

下面这个图展示了工作区、版本库中的暂存区和版本库之间的关系：

![Git 工作区、暂存区和版本库](https://www.runoob.com/wp-content/uploads/2015/02/1352126739_7909.jpg)

- 图中左侧为工作区，右侧为版本库。在版本库中标记为 **index** 的区域是暂存区（stage / index），标记为 **master** 的是 master 分支所代表的目录树。
- 图中我们可以看出此时的 **HEAD** 实际是指向 master 分支的一个 **游标**，所以图示的命令中出现 HEAD 的地方可以用 master 来替换。
- 图中的 objects 标识的区域为 Git 的对象库，实际位于 `git/objects` 目录下，里面包含了创建的各种对象及内容。
- 当对工作区修改（或新增）的文件执行 `git add`命令时，暂存区的目录树被更新，同时工作区修改（或新增）的文件内容被写入到对象库中的一个新的对象中，而该对象的 ID 被记录在暂存区的文件索引中。
- 当执行提交操作 `(git commit)`时，暂存区的目录树写到版本库（对象库）中，master 分支会做相应的更新。即 master 指向的目录树就是提交时暂存区的目录树。
- 当执行 `git rest HEAD` 命令时，暂存区的目录树会被重写，被 master 分支指向的目录树所替换，但是工作区不受影响。
- 当执行 `git rm --cached <file>` 命令时，会直接从暂存区删除文件，工作区则不做出改变。
- 当执行 `git checkout` ，或者 `git checkout -- <file>` 命令时，会用暂存区全部或指定的文件替换工作区的文件，这个操作很危险，会清除工作区中未添加到暂存区中的改动。
- 当执行 `git checkout HEAD .` 或者 `git checkout HEAD <file>` 命令时，会用 HEAD 指向的 master 分支中的全部或者部分文件替换暂存区和以及工作区的文件。这个命令也是极其危险的，因为不但会清除工作区中未提交的改动，也会清除暂存区中未提交的改动。



### 1.工作区（Working Directory）

工作区是你在本地计算机上的项目目录，你在这里进行文件的创建、修改和删除操作。工作区包含了当前项目的所有文件和子目录。

特点：

- 显示项目的当前状态
- 文件的修改

### 2.暂存区（Staging Area）

暂存区是一个临时存储区域，它包含了即将被提交到版本库中的文件快照，在提交之前，你可以选择性地将工作区中的修改添加到暂存区。

特点：

- 暂存区保存了将被包括在下一个提交的更改
- 你可以多次使用 git add 命令来讲文件添加到暂存区，直到你准备好提交所有更改

常用命令：

```sh
git add filename      # 将单个文件添加到暂存区
git add .             # 将工作区中的所有修改添加到暂存区
git status            # 查看哪些文件在暂存区
```

### 3.版本库（Repository）

版本库包含项目的所有版本历史记录。

每次提交都会在版本库中创建一个新的快照，这些快照是不可变的，确保了项目的完整历史记录。

特点：

- 版本库分为本地版本库和远程版本库。这里主要指本地版本库。
- 本地版本库存储在 .git 目录中，它包含了所有提交的对象和引用。

常用命令：

```sh
git commit -m "Commit message"   # 将暂存区的更改提交到本地版本库
git log                          # 查看提交历史
git diff                         # 查看工作区和暂存区之间的差异
git diff --cached                # 查看暂存区和最后一次提交之间的差异
```



## 工作区、暂存区和版本库之间的关系

### 1.工作区 -> 暂存区

使用 `git add` 命令将工作区中的修改添加到暂存区。

```sh
git add filename
```

### 2.暂存区 -> 版本库

使用 `git commit` 命令将暂存区中的修改提交到版本库。

```sh
git commit -m "Commit message"
```

### 3.版本库 -> 远程仓库

使用 `git push` 命令将本地版本库的提交推送到远程仓库。

```sh
git push origin branch-name
```

### 4.远程仓库 -> 本地版本库

使用 `git pull` 或 `git fetch` 从远程仓库获取更新。

```sh
git pull origin branch-name
# 或者
git fetch origin branch-name
git merge origin/branch-name
```



## 实例

假设你在工作目录中修改了 file.txt ：

### 1.工作区

修改 file.txt 并保存。

### 2.暂存区

将修改添加到暂存区：

```sh
git add file.txt
```

### 3.版本库

将暂存区的修改提交到本地版本库：

```sh
git commit -m "Update file.txt"
```

### 4.远程仓库

将本地提交推送到远程仓库：

```sh
git push origin main
```

通过理解工作区、暂存区和版本库的作用及其相互关系，你可以更加高效地使用 Git 进行版本控制和协同开发。



------



# Git 创建仓库

可以使用一个已经存在的目录作为 Git 仓库。



## git init

Git 使用 git init 命令来初始化一个 Git 仓库，Git 的很多命令都需要在 Git 的仓库中运行，所以 git init 是使用 Git 的第一个命令。

在执行完 git init 命令后，Git 仓库会生成一个 git 目录，该目录包含了资源的所有元数据，其他的项目目录保持不变。

使用方法：

进入你想要创建仓库的目录，或者先创建一个新的目录：

```sh
mkdir my-project
cd my-project
```

使用当前目录作为 Git 仓库，我们只需要使它初始化：

```sh
git init
```

该命令执行完后会在当前目录生成一个 .git 目录。

使用我们指定目录作为 Git 仓库。

```sh
git init newrepo
```

初始化后，会在 newrepo 目录下会出现一个名为 .git 的目录，所有 Git 需要的数据和资源都存放在这个目录中。

如果当前目录下有几个文件想要纳入版本控制，需要先用 git add 命令告诉 Git 开始对这些文件进行跟踪，然后提交：

```sh
$ git add *.c
$ git add README
$ git commit -m '初始化项目版本'
```

以上命令将目录下 .c 结尾及 README 文件提交到仓库中。

> 注：在 Linux 系统中，commit 信息使用单引号 `' '` , Windows 系统中，commit 信息使用双引号 `" "` 。
>
> 所以在 git bash 中 `git commit -m '提交说明'` 这样是可以的，在 Windows 命令行中就要使用双引号 `git commit -m "提交说明"`



## git clone

我们使用 git clone 从现有 Git 仓库中拷贝项目 （类似 svn checkout）

克隆仓库的命令格式为：

```sh
git clone <repo>
```

如果我们需要克隆到指定的目录，可以使用以下命令格式：

```sh
git clone <repo> <directory>
```

参数说明：

- repo ：Git 仓库
- directory ：本地目录

比如，要克隆 Ruby 语言的 Git 代码仓库 Grit ,可以使用下面的命令：

```sh
$ git clone git://github.com/schacon/grit.git
```

执行该命令后，会在当前目录下创建一个名为 grit 的目录，其中包含一个 .git 目录，用于保存下载下来的所有版本记录。

如果自己定义要新建的项目目录名称，可以在上面的命令末尾指定新的名字：

```sh
$ git clone git://github.com/schacon/grit.git mygrit
```



**配置**

git 的设置使用 git config 命令。

显示当前的 git 配置信息：

```sh
$ git config --list
credential.helper=osxkeychain
core.repositoryformatversion=0
core.filemode=true
core.bare=false
core.logallrefupdates=true
core.ignorecase=true
core.precomposeunicode=true
```

编辑 git 配置文件：

```sh
$ git config -e        # 针对当前仓库
```

或者：

```sh
$ git config -e --global     # 针对系统上所有仓库
```

设置提交代码时的用户信息：

```sh
$ git config --global user.name "runoob"
$ git config --global user.email test@runoob.com
```

如果去掉 --global 参数则只对当前仓库有效。



------



# Git 基本操作

Git 的工作就是创建和保存你项目的快照及与之后的快照进行对比。

Git 常用的是以下 6 个命令：**git clone** 、**git push** 、**git add** 、**git commit** 、**git checkout** 、**git pull** 

![Git 基本操作](https://www.runoob.com/wp-content/uploads/2015/02/git-command.jpg)

说明：

- workspace：工作区
- staging area：暂存区 / 缓存区
- local repository：版本库或本地仓库
- remote repository：远程仓库

一个简单的操作步骤：

```sh
$ git init
$ git add .
$ git commit
```

- git init - 初始化仓库
- git add . - 添加文件到暂存区
- git commit - 将暂存区内容添加到仓库中



## 创建仓库命令

下表列出了 git 创建仓库的命令：

| 命令        | 说明                                   |
| :---------- | :------------------------------------- |
| `git init`  | 初始化仓库                             |
| `git clone` | 拷贝一份远程仓库，也就是下载一个项目。 |



## 提交与修改

Git 的工作就是创建和保存你的项目的快照及与之后的快照进行对比。

下表列出了有关创建与提交你的项目的快照的命令：

| 命令                                | 说明                                     |
| :---------------------------------- | :--------------------------------------- |
| `git add`                           | 添加文件到暂存区                         |
| `git status`                        | 查看仓库当前的状态，显示有变更的文件。   |
| `git diff`                          | 比较文件的不同，即暂存区和工作区的差异。 |
| `git difftool`                      | 使用外部差异工具查看和比较文件的更改。   |
| `git range-diff`                    | 比较两个提交范围之间的差异。             |
| `git commit`                        | 提交暂存区到本地仓库。                   |
| `git reset`                         | 回退版本。                               |
| `git rm`                            | 将文件从暂存区和工作区中删除。           |
| `git mv`                            | 移动或重命名工作区文件。                 |
| `git notes`                         | 添加注释。                               |
| `git checkout`                      | 分支切换。                               |
| `git switch （Git 2.23 版本引入）`  | 更清晰地切换分支。                       |
| `git restore （Git 2.23 版本引入）` | 恢复或撤销文件的更改。                   |
| `git show`                          | 显示 Git 对象的详细信息。                |



## 提交日志

| 命令               | 说明                                                         |
| :----------------- | :----------------------------------------------------------- |
| `git log`          | 查看历史提交记录                                             |
| `git blame <file>` | 以列表形式查看指定文件的历史修改记录                         |
| `git shortlog`     | 生成简洁的提交日志摘要                                       |
| `git describe`     | 生成一个可读的字符串，该字符串基于 Git 的标签系统来描述当前的提交 |



## 远程操作

| 命令            | 说明                        |
| :-------------- | :-------------------------- |
| `git remote`    | 远程仓库操作                |
| `git fetch`     | 从远程获取代码库            |
| `git pull`      | 下载远程代码并合并          |
| `git push`      | 上传远程代码并合并          |
| `git submodule` | 管理包含其他 Git 仓库的项目 |



## Git 文件状态

Git 的文件状态分为三种：工作目录 （Working Directory）、暂存区（Staging Area）、本地仓库（Local Repository）。了解这些概念及其交互方式是掌握 Git 的关键。

### 工作目录（Working Directory）

工作目录是你在本地计算机上看到的项目文件。它是你实际操作文件的地方，包括查看、编辑、删除和创建文件。所有对文件的更改首先发生在工作目录中。

在工作目录中的文件可能有以下几种状态：

- **未跟踪（Untracked）：**新创建的文件，未被 Git 记录。
- **已修改（Modified）：**已被 Git 跟踪的文件发生了更改，但这些更改还没有被提交到 Git 记录中。

### 暂存区（Staging Area）

暂存区，也称索引（index），是一个临时存储区域，用于保存即将提交到本地仓库的更改。你可以选择性地将工作目录中的更改添加到暂存区中，这样你可以一次提交多个文件的更改，而不必提交所有文件的更改。

- 使用 `git add <filename>` 命令将文件从工作目录添加到暂存区。
- 使用 `git add .` 命令将当前目录下的所有更改添加到暂存区。

```sh
git add <filename>  # 添加指定文件到暂存区
git add .           # 添加所有更改到暂存区
```

### 本地仓库（Local Repository）

本地仓库是一个隐藏在 .git 目录中的数据库，用于存储项目中的所有提交历史记录，每次你提交更改时，Git 会将暂存区中的内容保存到本地仓库中。

使用 `git commit -m "commit message"` 命令将暂存区中的更改提交到本地仓库。

```sh
git commit -m "commit message"  # 提交暂存区的更改到本地仓库
```



### 文件状态转换流程

**未跟踪（Untracked）**：新创建的文件最初是未跟踪的。它们存在与工作目录中，但没有被 Git 跟踪。

```sh
touch newfile.txt         # 创建一个新文件
git status                # 查看状态，显示 newfile.txt 未跟踪
```

**已跟踪（Tracked）：**通过 `git add` 命令将未跟踪的文件添加到暂存区后，文件变为已跟踪状态。

```sh
git add newfile.txt       # 添加文件到暂存区
git status                # 查看状态，显示 newfile.txt 在暂存区
```

**已修改（Modified）：**对已跟踪的文件进行更改后，这些更改会显示为已修改状态，但这些更改还未添加到暂存区。

```sh
echo "Hello, World!" > newfile.txt  # 修改文件
git status                          # 查看状态，显示 newfile.txt 已修改
```

**已暂存（Staged）：**使用 `git add` 命令将修改过的文件添加到暂存区后，文件进入已暂存状态，等待提交。

```sh
git add newfile.txt     # 添加文件到暂存区
git status              # 显示状态，显示 newfile.txt 已暂存
```

**已提交（Commited）：**使用 `git commit` 命令将暂存区的更改提交到本地仓库后，这些更改被记录下来，文件状态返回为已跟踪状态。

```sh
git commit -m "Added newfile.txt"   # 提交更改
git status                          # 查看状态，工作目录干净
```



------



# Git 分支管理

Git 分支管理是 Git 强大功能之一，能够让多个开发人员并行工作，开发新功能，修复 bug 或进行试验，而不影响主代码效率。

几乎每一种版本控制系统都以某种形式支持分支，一个分支代表一条独立的开发线。

使用分支意味着你可以从开发主线分离开来，然后再不影响主线的同时继续工作。

![img](https://static.jyshare.com/images/svg/git-brance.svg)

Git 分支实际上是指向更改快照的指针。

有人把 Git 的分支模型成为 **必杀技特性** ，而正式因为它，将 Git 从版本控制系统家族里区分出来。



## 创建分支

创建新分支并切换到该分支：

```sh
git checkout -b <branchname>
```

例如：

```sh
git checkout -b feature-xyz
```

切换分支命令：

```sh
git checkout (branchname)
```

例如：

```sh
git checkout main
```

当你切换分支的时候，Git 会用该分支的最后提交的快照替换你的工作目录的内容，所以多个分支不需要多个目录。



## 查看分支

查看所有分支：

```sh
git branch
```

查看远程分支：

```sh
git branch -r
```

查看所有本地和远程分支：

```sh
git branch -a
```



## 合并分支

将其他分支合并到当前分支：

```sh
git merge <branchname>
```

例如，切换到 main 分支合并 feature-xyz 分支：

```sh
git checkout main
git merge feature-xyz
```



## 解决合并冲突

当合并过程中出现冲突时，Git 会标记冲突文件，你需要手动解决冲突。

打开冲突文件，按照标记解决冲突。

标记冲突解决完成：

```sh
git add <conflict-flie>
```

提交合并结果：

```sh
git commit
```



## 删除分支

删除本地分支：

```sh
git branch -d <branchname>
```

强制删除未合并的分支：

```sh
git branch -D <branchname>
```

删除远程分支：

```sh
git push origin --delete <branchname>
```



## 实例

开始前我们先创建一个测试目录：

```sh
$ mkdir gitdemo
$ cd gitdemo/
$ git init
Initialized empty Git repository...
$ touch README
$ git add README
$ git commit -m '第一次版本提交'
[master (root-commit) 3b58100] 第一次版本提交
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 README
```



## Git 分支管理

### 列出分支

列出分支基本命令：

```sh
git branch
```

没有参数时，git branch 会列出你在本地的分支。

```sh
$ git branch
* master
```

此例的意思就是，我们有一个叫做 master 的分支，并且该分支是当前分支。

当你执行 git init 的时候，默认情况下 Git 就会为你创建 master 分支。

如果我们要手动创建一个分支，执行 `git branch (branchname)` 即可。

```sh
$ git branch testing
$ git branch
* master
  testing
```

现在我们可以看到，有了一个新分支 testing。

当你以此方式在上次提交更新之后创建了新分支，如果后来又有更新提交，然后又切换到了 testing 分支，Git 将还原你的工作目录到你创建分支的时候的样子。

接下来我们将演示如何切换分支，我们用 `git checkout (branch)`切换到我们要修改的分支。

```sh
$ ls
README
$ echo 'runoob.com' > test.txt
$ git add .
$ git commit -m 'add test.txt'
[master 3e92c19] add test.txt
 1 file changed, 1 insertion(+)
 create mode 100644 test.txt
$ ls
README        test.txt
$ git checkout testing
Switched to branch 'testing'
$ ls
README
```

当我们切换到 testing 分支的时候，我们添加的新文件 test.txt 被移除了。切换回 master 分支的时候，它们又重新出现了。

```sh
$ git checkout master
Switched to branch 'master'
$ ls
README        test.txt
```

我们也可以使用 `git checkout -b (branchname)` 命令来创建新分支并立即切换到该分支下，从而在该分支中操作。

```sh
$ git checkout -b newtest
Switched to a new branch 'newtest'
$ git rm test.txt 
rm 'test.txt'
$ ls
README
$ touch runoob.php
$ git add .
$ git commit -am 'removed test.txt、add runoob.php'
[newtest c1501a2] removed test.txt、add runoob.php
 2 files changed, 1 deletion(-)
 create mode 100644 runoob.php
 delete mode 100644 test.txt
$ ls
README        runoob.php
$ git checkout master
Switched to branch 'master'
$ ls
README        test.txt
```

如你所见，我们创建了一个新分支，在该分支上移除了一些文件 text.txt ，并添加了 runoob.php 文件，然后切换回我们的主分支，删除的 test.txt 问及那又回来了，且新增加的 runoob.php 不存在主分支中。

使用分支将工作切分开来，从而让我们能够在不同开发环境中做事，并来回切换。



### 删除分支

删除分支命令：

```sh
git branch -d (branchname)
```

例如我们要删除 testing 分支：

```sh
$ git branch
* master
  testing
$ git branch -d testing
Deleted branch testing (was 85fc7e7).
$ git branch
* master
```



## 分支合并

一旦某分支有了独立内容，你终究会希望将他合并回到你的主分支，你也可以使用以下命令将任何分支合并到当前分支中去：

```sh
git merge
```

```sh
$ git branch
* master
  newtest
$ ls
README        test.txt
$ git merge newtest
Updating 3e92c19..c1501a2
Fast-forward
 runoob.php | 0
 test.txt   | 1 -
 2 files changed, 1 deletion(-)
 create mode 100644 runoob.php
 delete mode 100644 test.txt
$ ls
README        runoob.php
```



以上实例中我们将 newtest 分支合并到主分支区，test.txt 文件被删除。

合并完后就可以删除分支：

```sh
$ git branch -d newtest
Deleted branch newtest (was c1501a2)
```

删除后，就只剩下 master 分支了：

```sh
$ git branch
* master
```



## 合并冲突

合并并不仅仅是简单的文件添加和移除操作，Git 也会合并修改。

```sh
$ git branch
* master
$ cat runoob.php
```

首先，我们创建一个叫做 change_site 的分支，切换过去，我们将 runoob.php 内容改为：

```sh
<?php
echo 'runoob';
?>
```

创建 change_site 分支：

```sh
$ git checkout -b change_site
Switched to a new branch 'change_site'
$ vim runoob.php
$ head -3 runoob.php
<?php
echo 'runoob';
?>
$ git commit -am 'changed the runoob.php'
[change_site 7774248] changed the runoob.php
 1 file changed, 3 insertions(+)
```

将修改的内容提交到 change_site 分支中。现在，加入切换回 master 分支我们可以看内容恢复到我们修改前的（空文件，没有代码），我们再次修改 runoob.php 文件。

```sh
$ git checkout master
Switched to branch 'master'
$ cat runoob.php
$ vim runoob.php    # 修改内容如下
$ cat runoob.php
<?php
echo 1;
?>
$ git diff
diff --git a/runoob.php b/runoob.php
index e69de29..ac60739 100644
--- a/runoob.php
+++ b/runoob.php
@@ -0,0 +1,3 @@
+<?php
+echo 1;
+?>
$ git commit -am '修改代码'
[master c68142b] 修改代码
 1 file changed, 3 insertions(+)
```

现在这些改变已经记录到我的 "master" 分支了。接下来我们将 "change_site" 分支合并过来。

```sh
$ git merge change_site
Auto-merging runoob.php
CONFLICT (content): Merge conflict in runoob.php
Automatic merge failed; fix conflicts and then commit the result.

$ cat runoob.php     # 打开文件，看到冲突内容
<?php
<<<<<<< HEAD
echo 1;
=======
echo 'runoob';
>>>>>>> change_site
?>
```

我们将前一个分支合并到 master 分支，一个合并冲突就出现了，接下来我们需要手动去修改它。

```sh
$ vim runoob.php 
$ cat runoob.php
<?php
echo 1;
echo 'runoob';
?>
$ git diff
diff --cc runoob.php
index ac60739,b63d7d7..0000000
--- a/runoob.php
+++ b/runoob.php
@@@ -1,3 -1,3 +1,4 @@@
  <?php
 +echo 1;
+ echo 'runoob';
  ?>
```

在 Git 中，我们可以用 `git add` 要告诉 Git 文件冲突已经解决

```sh
$ git status -s
UU runoob.php
$ git add runoob.php
$ git status -s
M  runoob.php
$ git commit
[master 88afe0e] Merge branch 'change_site'
```

现在我们成功解决了合并中的冲突，并提交了结果。



## 命令手册

| **命令**        | **说明**                                                     | **用法示例**                                                 |
| :-------------- | :----------------------------------------------------------- | :----------------------------------------------------------- |
| `git branch`    | 列出、创建或删除分支。它不切换分支，只是用于管理分支的存在。 | `git branch`：列出所有分支 `git branch new-branch`：创建新分支 `git branch -d old-branch`：删除分支 |
| `git checkout`  | 切换到指定的分支或恢复工作目录中的文件。也可以用来检出特定的提交。 | `git checkout branch-name`：切换分支 `git checkout file.txt`：恢复文件到工作区 `git checkout <commit-hash>`：检出特定提交 |
| `git switch`    | 专门用于切换分支，相比 `git checkout` 更加简洁和直观，主要用于分支操作。 | `git switch branch-name`：切换到指定分支 `git switch -c new-branch`：创建并切换到新分支 |
| `git merge`     | 合并指定分支的更改到当前分支。                               | `git merge branch-name`：将指定分支的更改合并到当前分支      |
| `git mergetool` | 启动合并工具，以解决合并冲突。                               | `git mergetool`：使用默认合并工具解决冲突 `git mergetool --tool=<tool-name>`：指定合并工具 |
| `git log`       | 显示提交历史记录。                                           | `git log`：显示提交历史 `git log --oneline`：以简洁模式显示提交历史 |
| `git stash`     | 保存当前工作目录中的未提交更改，并将其恢复到干净的工作区。   | `git stash`：保存当前更改 `git stash pop`：恢复最近保存的更改 `git stash list`：列出所有保存的更改 |
| `git tag`       | 创建、列出或删除标签。标签用于标记特定的提交。               | `git tag`：列出所有标签 `git tag v1.0`：创建一个新标签 `git tag -d v1.0`：删除标签 |
| `git worktree`  | 允许在一个仓库中检查多个工作区，适用于同时处理多个分支。     | `git worktree add <path> branch-name`：在指定路径添加新的工作区并切换到指定分支 `git worktree remove <path>`：删除工作区 |





------



# Git 查看提交历史

查看 Git 提交历史可以帮助你了解代码的变更情况和开发进度。

Git 提供了多种命令和选项来查看提交历史，从简单的日志到详细的差异对比。

Git 提交历史一般常用两个命令：

- `git log` - 查看历史提交记录
- `git blame <file>` - 以列表形式查看指定文件的历史修改记录。



## git log

在使用 Git 提交了若干更新之后，又或者克隆了某个项目，想回顾下提交历史，我们可以使用 `git log` 命令查看。

git log 命令用于查看 Git 仓库中提交历史记录。

git log 显示了从最新提交到最早提交的所有提交信息，包括提交的哈希值、作者、提交日期和提交消息等。

git log 命令的基本语法：

```sh
git log [选项] [分支名/提交哈希]
```

常用的选项包括：

- `-p`：显示提交的补丁（具体更改内容）。
- `--oneline`：以简洁的一行格式显示提交信息。
- `--graph`：以图形化方式显示分支和合并历史。
- `--decorate`：显示分支和标签指向的提交。
- `--author=<作者>`：只显示特定作者的提交。
- `--since=<时间>`：只显示指定时间之后的提交。
- `--until=<时间>`：只显示指定时间之前的提交。
- `--grep=<模式>`：只显示包含指定模式的提交消息。
- `--no-merges`：不显示合并提交。
- `--stat`：显示简略统计信息，包括修改的文件和行数。
- `--abbrev-commit`：使用短提交哈希值。
- `--pretty=<格式>`：使用自定义的提交信息显示格式。

针对我们前一章节的操作，使用 **git log** 命令列出历史提交记录如下：

```sh
$ git log
commit d5e9fc2c811e0ca2b2d28506ef7dc14171a207d9 (HEAD -> master)
Merge: c68142b 7774248
Author: runoob <test@runoob.com>
Date:   Fri May 3 15:55:58 2019 +0800

    Merge branch 'change_site'

commit c68142b562c260c3071754623b08e2657b4c6d5b
Author: runoob <test@runoob.com>
Date:   Fri May 3 15:52:12 2019 +0800

    修改代码

commit 777424832e714cf65d3be79b50a4717aea51ab69 (change_site)
Author: runoob <test@runoob.com>
Date:   Fri May 3 15:49:26 2019 +0800

    changed the runoob.php

commit c1501a244676ff55e7cccac1ecac0e18cbf6cb00
Author: runoob <test@runoob.com>
Date:   Fri May 3 15:35:32 2019 +0800
```

我们可以用 --oneline 选项来查看历史记录的简洁的版本。

```sh
$ git log --oneline
$ git log --oneline
d5e9fc2 (HEAD -> master) Merge branch 'change_site'
c68142b 修改代码
7774248 (change_site) changed the runoob.php
c1501a2 removed test.txt、add runoob.php
3e92c19 add test.txt
3b58100 第一次版本提交
```

这告诉我们的是，此项目的开发历史。

我们还可以用 --graph 选项，查看历史中什么时候出现了分支、合并。以下为相同的命令，开启了拓扑图选项：

```sh
*   d5e9fc2 (HEAD -> master) Merge branch 'change_site'
|\  
| * 7774248 (change_site) changed the runoob.php
* | c68142b 修改代码
|/  
* c1501a2 removed test.txt、add runoob.php
* 3e92c19 add test.txt
* 3b58100 第一次版本提交
```

现在我们可以更清楚明了地看到何时工作分叉、又何时归并。

你也可以用 **--reverse** 参数来逆向显示所有日志。

```sh
$ git log --reverse --oneline
3b58100 第一次版本提交
3e92c19 add test.txt
c1501a2 removed test.txt、add runoob.php
7774248 (change_site) changed the runoob.php
c68142b 修改代码
d5e9fc2 (HEAD -> master) Merge branch 'change_site'
```

如果只想查找指定用户的提交日志可以使用命令：git log --author , 例如，比方说我们要找 Git 源码中 Linus 提交的部分：

```sh
$ git log --author=Linus --oneline -5
81b50f3 Move 'builtin-*' into a 'builtin/' subdirectory
3bb7256 make "index-pack" a built-in
377d027 make "git pack-redundant" a built-in
b532581 make "git unpack-file" a built-in
112dd51 make "mktag" a built-in
```

如果你要指定日期，可以执行几个选项：--since 和 --before，但是你也可以用 --until 和 --after。

例如，如果我要看 Git 项目中三周前且在四月十八日之后的所有提交，我可以执行这个（我还用了 --no-merges 选项以隐藏合并提交）：

```sh
$ git log --oneline --before={3.weeks.ago} --after={2010-04-18} --no-merges
5469e2d Git 1.7.1-rc2
d43427d Documentation/remote-helpers: Fix typos and improve language
272a36b Fixup: Second argument may be any arbitrary string
b6c8d2d Documentation/remote-helpers: Add invocation section
5ce4f4e Documentation/urls: Rewrite to accomodate transport::address
00b84e9 Documentation/remote-helpers: Rewrite description
03aa87e Documentation: Describe other situations where -z affects git diff
77bc694 rebase-interactive: silence warning when no commits rewritten
636db2c t3301: add tests to use --format="%N"
```



## 常用选项

限制显示的提交数：

```sh
git log -n <number>
```

例如，显示最近的 5 次提交：

```sh
git log -n 5
```

显示自指定日期之后的提交：

```sh
git log --since="2024-01-01"
```

显示指定日期之前的提交：

```sh
git log --until="2024-07-01"
```

只显示某个作者的提交：

```sh
git log --author="Author Name"
```

更多 **git log** 命令可查看 http://git-scm.com/docs/git-log 或使用 **git log --help** 命令查看帮助信息。



## git blame

git blame 命令用于逐行显示指定文件的每一行代码是由谁在什么时候引入或修改的。

git blame 可以追踪文件中每一行的变更历史，包括作者、提交哈希、提交日期和提交消息等信息。

如果要查看指定文件的修改记录可以使用 git blame 命令，格式如下：

```sh
git blame [选项] <文件路径>
```

常用的选项包括：

- `-L <起始行号>,<结束行号>`：只显示指定行号范围内的代码注释。
- `-C`：对于重命名或拷贝的代码行，也进行代码行溯源。
- `-M`：对于移动的代码行，也进行代码行溯源。
- `-C -C` 或 `-M -M`：对于较多改动的代码行，进行更进一步的溯源。
- `--show-stats`：显示包含每个作者的行数统计信息。

显示文件每一行的代码注释和相关信息：

```sh
git blame <文件路径>
```

只显示指定行号范围内的代码注释：

```sh
git blame -L <起始行号>,<结束行号> <文件路径>
```

对于重命名或拷贝的代码进行溯源：

```sh
git blame -C <文件路径>
```

对于移动的代码进行溯源：

```sh
git blame -M <文件路径>
```

显示行数统计信息：

```sh
git blame --show-status <文件路径>
```

git blame 命令是以列表形式显示修改记录，如下实例：

```sh
$ git blame README 
^d2097aa (tianqixin 2020-08-25 14:59:25 +0800 1) # Runoob Git 测试
db9315b0 (runoob    2020-08-25 16:00:23 +0800 2) # 菜鸟教程 
```



## 恢复和回退

Git 提供了多种方式来恢复和回退到之前的版本，不同的命令适用于不同的场景和需求。

以下是几种常见的方法：

- `git checkout`：切换分支或恢复文件到指定提交
- `git reset`：重置当前分支到指定提交（软重置、混合重置、硬重置）。
- `git revert`：创建一个新的提交以撤销指定提交，不改变提交历史。
- `git reflog`：查看历史操作记录，找回丢失的提交。

### 1、git checkout：检查出特定版本的文件

git checkout 命令用于切换分支或恢复工作目录中的文件到指定的提交。

恢复工作目录中的文件到某个提交：

```sh
git checkout <commit> -- <filename>
```

例如，将 file.txt 恢复到 abc123 提交时的版本：

```sh
git checkout abc123 -- file.txt
```

切换到特定提交：

```sh
git checkout <commit>
```

例如：

```sh
git checkout abc123
```

这种方式切换到特定的提交时，处于分离头指针（detached HEAD）状态。

### 2、git reset：重置当前分支到特定提交

git reset 命令可以更改当前分支的提交历史，它有三种主要模式：--soft、--mixed 和 --hard。

**--soft**：只重置 HEAD 到指定的提交，暂存区和工作目录保持不变。

```sh
git reset --soft <commit>
```

**--mixed（默认）**：重置 HEAD 到指定的提交，暂存区重置，但工作目录保持不变。

```sh
git reset --mixed <commit>
```

**--hard**：重置 HEAD 到指定的提交，暂存区和工作目录都重置。

```sh
git reset --hard <commit>
```

例如，将当前分支重置到 abc123 提交：

```sh
git reset --hard abc123
```

### 3、git revert：撤销某次提交

git revert 命令创建一个新的提交，用来撤销指定的提交，它不会改变提交历史，适用于已经推送到远程仓库的提交。

```sh
git revert <commit>
```

例如，撤销 abc123 提交：

```sh
git revert abc123
```

### 4、git reflog：查看历史操作记录

git reflog 命令记录了所有 HEAD 的移动。即使提交被删除或重置，也可以通过 reflog 找回。

```sh
git reflog
```

利用 reflog 可以找到之前的提交哈希，从而恢复到特定状态。例如：

```sh
git reset --hard HEAD@{3}
```

### 实例

以下是一个综合示例，演示如何使用这些命令恢复历史版本：

查看提交历史：

```sh
git log --oneline
```

假设输出如下：

```sh
abc1234 Commit 1
def5678 Commit 2
ghi9012 Commit 3
```

切换到 Commit 2（处于分离头指针状态）：

```sh
git checkout def5678
```

重置到 Commit 2，保留更改到暂存区：

```sh
git reset --soft def5678
```

重置到 Commit 2，取消暂存区更改：

```sh
git reset --mixed def5678
```

重置到 Commit 2，丢弃所有更改：

```sh
git reset --hard def5678
```

撤销 Commit 2：

```sh
git revert def5678
```

查看 reflog 找回丢失的提交：

```sh
git reflog
```

找到之前的提交哈希并恢复：

```sh
git reset --hard HEAD@{3}
```



------



# Git 标签



如果你达到一个重要的阶段，并希望永远记住提交的快照，你可以使用 **git tag** 给它打上标签。

Git 标签（Tag）用于给仓库中的特定提交点加上标记，通常用于发布版本（如 v1.0, v2.0）。



比如说，我们想为我们的 runoob 项目发布一个 "1.0" 版本，我们可以用 **git tag -a v1.0** 命令给最新一次提交打上（HEAD） "v1.0" 的标签。



***\*-a\** 选项意为**"创建一个带注解的标签"，不用 **-a** 选项也可以执行的，但它不会记录这标签是啥时候打的，谁打的，也不会让你添加个标签的注解，我们推荐一直创建带注解的标签。

**标签语法格式：**

```sh
git tag <tagname>
```

例如：

```sh
git tag v1.0
```

**-a** 选项可以添加注解：

```sh
$ git tag -a v1.0 
```

当你执行 git tag -a 命令时，Git 会打开你的编辑器，让你写一句标签注解，就像你给提交写注解一样。

现在，注意当我们执行 **git log --decorate** 时，我们可以看到我们的标签了：

```sh
*   d5e9fc2 (HEAD -> master) Merge branch 'change_site'
|\  
| * 7774248 (change_site) changed the runoob.php
* | c68142b 修改代码
|/  
* c1501a2 removed test.txt、add runoob.php
* 3e92c19 add test.txt
* 3b58100 第一次版本提交
```

如果我们忘了给某个提交打标签，又将它发布了，我们可以给它追加标签。

例如，假设我们发布了提交 85fc7e7(上面实例最后一行)，但是那时候忘了给它打标签。 我们现在也可以：

```sh
$ git tag -a v0.9 85fc7e7
$ git log --oneline --decorate --graph
*   d5e9fc2 (HEAD -> master) Merge branch 'change_site'
|\  
| * 7774248 (change_site) changed the runoob.php
* | c68142b 修改代码
|/  
* c1501a2 removed test.txt、add runoob.php
* 3e92c19 add test.txt
* 3b58100 (tag: v0.9) 第一次版本提交
```

如果我们要查看所有标签可以使用以下命令：

```sh
$ git tag
v0.9
v1.0
```

### 推送标签到远程仓库

默认情况下，git push 不会推送标签，你需要显式地推送标签。

```sh
git push origin <tagname>
```

推送所有标签：

```sh
git push origin --tags
```

### 删除轻量标签

本地删除：

```sh
git tag -d <tagname>
```

远程删除：

```sh
git push origin --delete <tagname>
```

### 附注标签

附注标签存储了创建者的名字、电子邮件、日期，并且可以包含标签信息。附注标签更为正式，适用于需要额外元数据的场景。

创建附注标签语法：

```sh
git tag -a <tagname> -m "message"
```

例如：

```sh
git tag -a <tagname> -m "runoob.com标签"
```

PGP 签名标签命令：

```sh
git tag -s <tagname> -m "runoob.com标签"
```

查看标签信息：

```sh
git show <tagname>
```

### 实例

以下是一个综合示例，演示如何创建、查看、推送和删除标签。

创建轻量标签和附注标签：

```sh
git tag v1.0
git tag -a v1.1 -m "runoob.com标签"
```

查看标签和标签信息：

```sh
git tag
git show v1.1
```

推送标签到远程仓库：

```sh
git push origin v1.0
git push origin v1.1
git push origin --tags  # 推送所有标签
```

### 删除标签

本地删除：

```sh
git tag -d v1.0
```

远程删除：

```sh
git push origin --delete v1.0
```



------



# Git Flow

Git Flow 是一种基于 Git 的分支模型，旨在帮助团队更好地管理和发布软件。

Git Flow 由 Vincent Driessen 在 2010 年提出，并通过一套标准的分支命名和工作流程，使开发、测试和发布过程更加有序和高效。

Git Flow 主要由以下几类分支组成：`master`、`develop`、`feature`、`release`、`hotfix`。

## Git Flow 安装

### Linux

**Debian/Ubuntu:**

```bash
sudo apt-get install git-flow
```

**Fedora:**

```bash
sudo dnf install gitflow
sudo apt-get install git-flow
```

### macOS

在 macOS 上，你可以使用 Homebrew 来安装 Git Flow:



```bash
brew install git-flow
```

### 源码安装

如果你的发行版的包管理器中没有 Git Flow，你也可以从源代码进行安装：

```sh
git clone https://github.com/nvie/gitflow.git
cd gitflow
sudo make install
```

安装完成后，你可以通过以下命令验证 Git Flow 是否成功安装：

```sh
git flow version
```

### Windows

在 Windows 上，你可以通过以下方式安装 Git Flow：

- **使用 Git for Windows**: Git for Windows 包含了 Git Flow。你可以从 [Git for Windows](https://gitforwindows.org/) 安装 Git，然后使用 Git Bash 来使用 Git Flow。

- **使用 Scoop**: 如果你使用 Scoop 包管理工具，可以通过以下命令安装 Git Flow：

  ```sh
  scoop install git-flow
  ```

- **使用 Chocolatey**: 如果你使用 Chocolatey 包管理工具，可以通过以下命令安装 Git Flow：

  ```sh
  choco install gitflow
  ```

------

## Git Flow 分支模型

**`master` 分支**：

- 永远保持稳定和可发布的状态。
- 每次发布一个新的版本时，都会从 `develop` 分支合并到 `master` 分支。

**`develop` 分支**：

- 用于集成所有的开发分支。
- 代表了最新的开发进度。
- 功能分支、发布分支和修复分支都从这里分支出去，最终合并回这里。

**`feature` 分支**：

- 用于开发新功能。
- 从 `develop` 分支创建，开发完成后合并回 `develop` 分支。
- 命名规范：`feature/feature-name`。

**`release` 分支**：

- 用于准备新版本的发布。
- 从 `develop` 分支创建，进行最后的测试和修复，然后合并回 `develop` 和 `master` 分支，并打上版本标签。
- 命名规范：`release/release-name`。

**`hotfix` 分支**：

- 用于修复紧急问题。
- 从 `master` 分支创建，修复完成后合并回 `master` 和 `develop` 分支，并打上版本标签。
- 命名规范：`hotfix/hotfix-name`。

![img](https://www.runoob.com/wp-content/uploads/2024/07/git-flow.png)

### 分支操作原理

- Master 分支上的每个 Commit 应打上 Tag，Develop 分支基于 Master 创建。
- Feature 分支完成后合并回 Develop 分支，并通常删除该分支。
- Release 分支基于 Develop 创建，用于测试和修复 Bug，发布后合并回 Master 和 Develop，并打 Tag 标记版本号。
- Hotfix 分支基于 Master 创建，完成后合并回 Master 和 Develop，并打 Tag 1。

### Git Flow 命令示例

- 开始 Feature 分支：`git flow feature start MYFEATURE`
- 完成 Feature 分支：`git flow feature finish MYFEATURE`
- 开始 Release 分支：`git flow release start RELEASE [BASE]`
- 完成 Release 分支：合并到 Master 和 Develop，打 Tag，删除 Release 分支。
- 开始 Hotfix 分支：`git flow hotfix start HOTFIX [BASE]`
- 完成 Hotfix 分支：合并到 Master 和 Develop，打 Tag，删除 Hotfix 分支。

### Git Flow 工作流程

#### 1. 初始化 Git Flow

首先，在项目中初始化 Git Flow。可以使用 Git Flow 插件（例如 `git-flow`）来简化操作。

```sh
git flow init
```

初始化时，你需要设置分支命名规则和默认分支。

#### 2. 创建功能分支

当开始开发一个新功能时，从 `develop` 分支创建一个功能分支。

```sh
git flow feature start feature-name
```

完成开发后，将功能分支合并回 `develop` 分支，并删除功能分支。

```sh
git flow feature finish feature-name
```

#### 3. 创建发布分支

当准备发布一个新版本时，从 `develop` 分支创建一个发布分支。

```sh
git flow release start release-name
```

在发布分支上进行最后的测试和修复，准备好发布后，将发布分支合并回 `develop` 和 `master` 分支，并打上版本标签。

```sh
git flow release finish release-name
```

#### 4. 创建修复分支

当发现需要紧急修复的问题时，从 `master` 分支创建一个修复分支。

```sh
git flow hotfix start hotfix-name
```

修复完成后，将修复分支合并回 `master` 和 `develop` 分支，并打上版本标签。

```sh
git flow hotfix finish hotfix-name
```

### 实例操作

以下是一个实际使用 Git Flow 的综合实例。

**初始化 Git Flow**：

```sh
git flow init
```

**创建和完成功能分支**：

```sh
git flow feature start new-feature # 开发新功能
git flow feature finish new-feature
```

**创建和完成发布分支**：

```sh
git flow release start v1.0.0 # 测试和修复
git flow release finish v1.0.0
```

**创建和完成修复分支**：

```sh
git flow hotfix start hotfix-1.0.1. # 修复紧急问题
git flow hotfix finish hotfix-1.0.1
```

### 优点和缺点

**优点**

- **明确的分支模型**：清晰的分支命名和使用规则，使得开发过程井然有序。
- **隔离开发和发布**：开发和发布过程分离，减少了开发中的不确定性对发布的影响。
- **版本管理**：每次发布和修复都会打上版本标签，方便回溯和管理。

**缺点**

- **复杂性**：对于小型团队或简单项目，Git Flow 的分支模型可能显得过于复杂。
- **频繁的合并**：在大型团队中，频繁的分支合并可能导致合并冲突增加。

Git Flow 是一种结构化的分支管理模型，通过定义明确的分支和工作流程，帮助团队更好地管理软件开发和发布过程。虽然它增加了一定的复杂性，但对于大型项目和团队协作，Git Flow 提供了强大的支持和管理能力。



------



# Git 进阶操作

在掌握了 Git 的基础操作之后，进阶操作可以帮助你更高效地管理和优化你的代码库。

以下是一些常见的进阶操作及其详细说明：

- **交互式暂存**：逐块选择要暂存的更改，精细控制提交内容。
- **Git Stash**：临时保存工作进度，方便切换任务。
- **Git Rebase**：将一个分支上的更改移到另一个分支之上，保持提交历史线性。
- **Git Cherry-Pick**：选择特定提交并应用到当前分支。

### 1、交互式暂存（Interactive Staging）

`git add` 命令可以选择性地将文件或文件的一部分添加到暂存区，这在处理复杂更改时非常有用。

- **使用 `git add -p`**：逐块选择要暂存的更改。

```sh
git add -p
```

执行此命令后，Git 会逐块显示文件的更改，你可以选择是否暂存每个块。常用选项包括：

- `y`：暂存当前块
- `n`：跳过当前块
- `s`：拆分当前块
- `e`：手动编辑当前块
- `q`：退出暂存

### 2、Git Stash：临时保存工作进度

`git stash` 命令允许你临时保存当前工作目录的更改，以便你可以切换到其他分支或处理其他任务。

**保存当前工作进度**：

```sh
git stash
```

**查看存储的进度**：

```sh
git stash list
```

**应用最近一次存储的进度**：

```sh
git stash apply
```

**应用并删除最近一次存储的进度**：

```sh
git stash pop
```

**删除特定存储**：

```sh
git stash drop stash@{n}
```

**清空所有存储**：

```sh
git stash clear
```

### 3、Git Rebase：变基

`git rebase` 命令用于将一个分支上的更改移到另一个分支之上。它可以帮助保持提交历史的线性，减少合并时的冲突。

**变基当前分支到指定分支**：

```sh
git rebase <branchname>
```

例如，将当前分支变基到 `main` 分支：

```sh
git rebase main
```

- **交互式变基**：

```sh
git rebase -i <commit>
```

交互式变基允许你在变基过程中编辑、删除或合并提交。常用选项包括：

- `pick`：保留提交
- `reword`：修改提交信息
- `edit`：编辑提交
- `squash`：将当前提交与前一个提交合并
- `fixup`：将当前提交与前一个提交合并，不保留提交信息
- `drop`：删除提交

### 4、Git Cherry-Pick：拣选提交

`git cherry-pick` 命令允许你选择特定的提交并将其应用到当前分支。它在需要从一个分支移植特定更改到另一个分支时非常有用。

**拣选提交**：

```sh
git cherry-pick <commit>
```

例如，将 `abc123` 提交应用到当前分支：

```sh
git cherry-pick abc123
```

**处理拣选冲突**：如果拣选过程中出现冲突，解决冲突后使用 `git cherry-pick --continue` 继续拣选。

### 示例操作

以下是一个综合示例，展示了如何使用这些进阶操作：

**交互式暂存**：

```sh
git add -p
```

**保存工作进度**：

```sh
git stash
```

**查看存储的进度**：

```sh
git stash list
```

**应用存储的进度**：

```sh
git stash apply
```

**变基当前分支到 `main` 分支**：

```sh
git rebase main
```

**交互式变基，编辑提交历史**：

```sh
git rebase -i HEAD~3
```

编辑提交历史，如合并和重命名提交。

**拣选 `feature` 分支上的特定提交到 `main` 分支**：

```sh
git checkout main
git cherry-pick abc123
```
