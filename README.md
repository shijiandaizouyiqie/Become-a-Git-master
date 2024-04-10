# 我要成为Git高手

## [教程链接](https://www.liaoxuefeng.com/wiki/896043488029600)

## 工作原理

![tupian](/Git学习/picture/版本库.jpg)

- git add命令实际上就是把要提交的所有修改放到暂存区（Stage），然后，执行git commit就可以一次性把暂存区的所有修改提交到分支。

![tupian](/Git学习/picture/工作原理2.jpg)

## 学习心得

### Git配置

```shell
git config --list --show-origin
git config --global user.name "bukebuke"
```

- 展示用户配置信息，修改用户名字

### .git目录（文件夹）

![.git目录](/Git学习/picture/-git目录.jpg)

- 这个目录是Git来跟踪管理版本库的

### git配置信息

![git配置信息](/Git学习/picture/git配置信息.jpg)

- 全局配置是针对当前用户的，对该用户在系统上所有 Git 仓库都生效。全局配置一般用于配置用户信息（如用户名和邮箱）以及个人偏好设置（如默认编辑器、换行符处理等）。
- 当前仓库配置是针对当前 Git 仓库的，只在当前仓库中生效。当前仓库配置优先级高于全局配置，即如果当前仓库配置和全局配置有冲突，当前仓库配置会覆盖全局配置。

### 修改文件并上传

![修改文件并上传](/Git学习/picture/修改文件并上传.jpg)
![修改文件并上传2](/Git学习/picture/上传之后.jpg)

### git diff

![tupian](/Git学习/picture/git_diff和git_add.jpg)

- git diff 命令用于比较工作区和暂存区的差异。
- 如果在使用 git add 将文件添加到暂存区后再运行 git diff，那么暂存区和工作区的内容应该是一致的，因此不会显示差异。
- 可以使用 git diff --cached 或 git diff --staged 命令查看当前暂存区的文件和最后一次提交之间的区别。

![tupian](/Git学习/picture/查看已经添加到暂存区的文件与最后一次提交的差异.jpg)

### 查看提交日志

![tupian](/Git学习/picture/查看提交日志.jpg)

- 上图看到的一大串类似1094adb...的是commit id（版本号）
  
### 回退版本

![tupian](/Git学习/picture/回退版本.jpg)

![tupian](/Git学习/picture/回退版本图解.jpg)

- 上一个版本就是HEAD^，上上一个版本就是HEAD^^，当然往上100个版本写100个^比较容易数不过来，所以写成HEAD~100。
- --hard 参数表示重置模式。--hard 模式会重置当前分支的 HEAD 指针、暂存区和工作区，使其完全匹配指定的提交。这意味着未提交的更改会被永久删除，慎重使用。
- 
![tupian](/Git学习/picture/git的版本是可以任意切换的.jpg)
- 
![tupian](/Git学习/picture/git_reflog.jpg)

### 撤销修改

![tupian](/Git学习/picture/修改了文件但是还没提交到暂存区的撤销修改.jpg)

- git checkout -- <file>它主要是用来撤销工作目录中对指定文件的修改，并将文件恢复到最近一次提交时的状态。（简单说就是修改文件之后，但还没添加到暂存区的话，就可以使用这个撤销修改）

![tupian](/Git学习/picture/修改并提交到暂存区后的撤销修改.jpg)

- 注意，git reset HEAD <file>这个指令本身只是取消暂存文件，将指定的文件从暂存区移除，但是不会改变工作目录中的文件内容，也就是说使用之后，文件本身依旧保持修改过后的状态，需要使用git checkout -- <file>来撤销修改，回到上次提交的状态。



- 注意，git checkout指令的功能远不止于此，它还能切换分支，如下所示。

![tupian](/Git学习/picture/切换分支.jpg)

![tupian](/Git学习/picture/分支之间是独立的.jpg)

### 删除文件

![tupian](/Git学习/picture/误删文件后恢复.jpg)

- 误删文件的恢复方法

![tupian](/Git学习/picture/确定删除文件.jpg)