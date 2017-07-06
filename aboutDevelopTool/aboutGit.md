[TOC]

## Git 使用

 - git 分布式代码管理工具

 - svn 集中式代码管理工具

### 一、git 安装

 - 下载地址：https://git-scm.com/downloads

 - 根据提示安装

 - 在桌面单击鼠标右键，有“ Git GUI Here ” 和 “ Git Base Here ” 就安装成功了

### 二、git 使用

#### git init  初始化一个仓库
 + 其实就是创建了一个 .git 的隐藏目录

 + 想在哪个目录创建 .git ，就在哪个目录打开 “ Git Base Here ”

 + 一般是在项目的根目录创建

#### 配置用户信息
 + 配置用户名：git config user.name "suting" ( git config --global  user.name "suting" )

 + 配置邮箱：git config user.email "...."

 + 查看配置信息：git config --list
 
#### 将代码提交到仓库中
 1. 先把代码提交到暂存区，命令：git add 文件路径（ git add ./test.html）
        一次性将当前目录下所有修改文件添加到暂存区：git add .

 2. 把暂存区的文件提交到仓库，命令：git commit "提交说明（相当于注释）"   （git commit -m "第一个版本"）

 3. 合并 add 与 commit 操作：git commit -a -m "提交与说明"
    + -a只对修改后的文件有效，新添加的无效

 4. 查看工作区状态，命令：git status
 
 5. 移除暂存区的文件，命令： `git rm --cached 文件名`

#### 添加忽略文件
 + 为避免将不必要的文件提交，可在 .git 文件所在目录下创建一个 .gitignore 的文件，然后在该文件夹中添加需要忽略的文件：
    ```
     /test.txt
     /.gitignore
     # * 代表通配符
     /css/*.css
    ```

#### 对比文件差异
 - 命令：git diff，比较暂存区与工作区文件的差异，如果暂存区没有文件，就会将工作区代码与最近一次提交代码的差异。

 - 命令：git diff --cached，直接比较工作区代码与最近一次提交代码的差异

 - 命令：git diff [版本号1] [版本号2] [想比较的文件路径]，对比之前某两次文件提交的差异，版本号可以通过 git log 查看，一般前6位即可。
    如：`git diff 489f2b 97c185 ./test.html`

#### 查看日志
 - 命令：git log

 - 命令：git log --oneline，以比较简洁的形式输出提交日志

 - 命令：git reflog，查看所有版本切换操作的记录。如果进行了版本回退，git log 无法查看被回退的版本

#### 版本回退

 - git reset --hard Head
    + Head 指向最近一次 commit 提交 
    + Head~1 最近一次 commit 提交的上一次，即上上次提交
    + Head~2 最近一次 commit 提交的上两次，即上上上次提交
 
 - git reset --hard 版本号
    + 通过每次提交时生成的版本号来指定回退版本
    + git reflog 查看被回退后的版本号

#### 分支管理
 - git branch，查看当前所有分支

 - git branch [分支名]，创建一个新的分支

 - git checkout [分支名]，切换分支
    切换分支后，可以在切换后的分支内进行正常的操作，完成后切换到主分支与主分支进行合并。

 - git merge [分支名]
    将指定的分支合并到当前分支

 - git branch -d [分支名] 删除指定分支，-d 表名要执行删除操作

 - 提交时的冲突管理
    + 如果 git 不能自动合并分支 ，就会有冲突。此时需要手动解决冲突（删除不需要的代码），然后再次提交。
 
### 三、结合 github 使用（或其他服务器）
 
#### 上传代码到 git 服务器（ push ）
 - `git push https://github.com/ST-suting/study.git master` ，上传到自己的github。需要输入github的账号和密码

 - `git push git@github.com:ST-suting/study.git`，ssh 方式上传代码
    git 生成公钥和私钥：`ssh-keygen -t rsa`

 - 如果不想每次都输入比较长的地址，可以采用变量的形式代替地址：
    `git remote add [变量名] [远程服务器地址]`
    `git remote add origin https://github.com/ST-suting/study.git master`
    再次提交时：`git push origin master`

#### 把代码 push 到服务器时需要先 pull 一下
 - 从服务器 pull 代码到本地
    + 如果本地没有 .git 目录，需要先初始化一个
    + `git pull [远程服务器地址] [远程的分支]`
    + `git pull https://github.com/ST-suting/study.git master`

 - 在 pull 之后如果远程的代码与本地的代码有冲突，git 会先自动合并冲突，如果不能自动合并，就需要手动去处理冲突。
 
### Git免登录，不需重复输入账号和密码
 - 命令行下：
 ```
 在~/下， touch创建文件 .git-credentials：
touch .git-credentials

# 用vim编辑此文件，
vim .git-credentials

#输入内容格式
https://username:password@github.com
 ```
 
 - 终端下：
 ```
 git config --global credential.helper store
 ```
 
 - 可以看到~/.gitconfig文件，会多了一项：
```
[credential]
    helper = store
 ```
 
