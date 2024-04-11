# 我要成为Git高手

## [教程链接](https://www.liaoxuefeng.com/wiki/896043488029600)

## [Git指令表格](/Git学习/git-cheat-sheet.pdf)

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

### 本地仓库和远程仓库之间的联系

#### 方法一

1. 使用 git init 将一个文件夹初始化为一个 Git 本地仓库。

![tupian](/Git学习/picture/本地仓库和远程仓库之间传输/第一步.jpg)

2. 使用 SSH 或 HTTPS 将本地仓库与 GitHub 上的远程仓库链接。

![tupian](/Git学习/picture/本地仓库和远程仓库之间传输/第二步.jpg)

3. 使用 git remote add origin <远程仓库地址> 将本地仓库与远程仓库关联。

- 第一次绑定时要给远程仓库指定一个名字，一般都是用的"origin"。

![tupian](/Git学习/picture/本地仓库和远程仓库之间传输/第四步.jpg)

4. 使用 git push -u origin <分支名> 将本地分支推送到远程仓库。第一次推送时可能需要 -u 选项来建立关联。在以后的推送或者拉取时就可以简化命令。

![tupian](/Git学习/picture/本地仓库和远程仓库之间传输/第五步.jpg)

- git push -u origin <分支名> 其实git push -u <远程仓库名字> <分支名> ,但是默认都是给远程仓库命名为origin。
- git push 命令会默认将本地的所有分支推送到远程仓库中。(等价于git push --all origin)
- 也可以指定推送某个分支 git push origin <分支名>
   
#### 方法二

- 先在GitHub上建立一个仓库(记得建立个README文件，不然是空仓库，空仓库是无法克隆的)

- git clone到本地电脑，这样就省了手动在电脑中git init 创建本地版本库和git remote add origin这个链接本地仓库和远程仓库的过程。

- 然后正常add 和commit将文件保存到本地仓库.

![tupian](/Git学习/picture/本地仓库和远程仓库之间传输/法2的clone和add和commit.jpg)


- 然后就可以直接git push进远程仓库里面了。

![tupian](/Git学习/picture/本地仓库和远程仓库之间传输/法2的git_push.jpg)

- 可以看出成功的上传了
 
![tupian](/Git学习/picture/本地仓库和远程仓库之间传输/成功上传.jpg)

### 取消本地仓库跟远程仓库的联系

![tupian](/Git学习/picture/解除跟远程库的关系.jpg)

- 解除联系之后就不能使用git push了，因为本地仓库不知道push到那个远程仓库中，需要再次建立联系才能push。

![tupian](/Git学习/picture/解绑之后重新绑定.jpg)

### 合并分支

![tupian](/Git学习/picture/合并分支.jpg)

### 查看所有分支以及当前所处的分支

![tupian](/Git学习/picture/查看所有分支以及当前所处的分支.jpg)

### 删除分支

![tupian](/Git学习/picture/删除分支.jpg)

### 分支冲突

![tupian](/Git学习/picture/分支冲突1.jpg)
![tupian](/Git学习/picture/分支冲突2.jpg)
![tupian](/Git学习/picture/分支冲突3.jpg)

- 分支冲突解决方法

![tupian](/Git学习/picture/解决分支冲突1.jpg)
![tupian](/Git学习/picture/解决分支冲突2.jpg)


### 注意远程仓库命名

![tupian](/Git学习/picture/远程仓库绑定问题.jpg)

- Git 可以绑定多个远程仓库。可以通过添加不同的远程仓库来实现这一点。例如，假设已经有一个名为 origin 的远程仓库，可以添加一个名为 upstream 的额外远程仓库。注意git push 的时候填写正确远程仓库的名字。

### 分支管理策略

- 首先，master分支应该是非常稳定的，也就是仅用来发布新版本，平时不能在上面干活；

- 那在哪干活呢？干活都在dev分支上，也就是说，dev分支是不稳定的，到某个时候，比如1.0版本发布时，再把dev分支合并到master上，在master分支发布1.0版本；

- 你和你的小伙伴们每个人都在dev分支上干活，每个人都有自己的分支，时不时地往dev分支上合并就可以了。

- 所以，团队合作的分支看起来就像这样：

![tupian](/Git学习/picture/分支管理策略.jpg)

- Git分支十分强大，在团队开发中应该充分应用。

- 合并分支时，加上--no-ff参数就可以用普通模式合并，合并后的历史有分支，能看出来曾经做过合并，而fast forward合并就看不出来曾经做过合并。

### git stash

- 好难，之后再学吧，现在用不到。
- 当前工作区有文件未提交 此时想切换分支如果有同一文件会冲突（注意一下）

### 分支小结

- Git鼓励大量使用分支：

1. 查看分支：git branch

2. 创建分支：git branch <name>

3. 切换分支：git checkout <name>或者git switch <name>

4. 创建+切换分支：git checkout -b <name>或者git switch -c <name>

5. 合并某分支到当前分支：git merge <name>

6. 删除分支：git branch -d <name>