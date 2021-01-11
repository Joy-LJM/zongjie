### 用gitee码云
### git 设置用户名和邮件地址 命令
git config --global user.name 'Arthur'
git config --global user.email 1067599167@qq.com

### 合并并提交
### 1、自己的代码提交到本地 2、拉取别人代码到本地仓库 3、合并 4、查看文件解决冲突 5、提交
### 解决冲突：git命令行打印有冲突的文件，有三种方式：使用别人的代码、使用自己的代码、更改自己的代码
git add.
git commit -m '注释'  // 先把自己代码提交的本地仓库
git checkout master   // 切到别的分支
git pull    // 把远程master上的最新代码拉到本地仓库
git checkout 分支名   // 回到自己的分支
git merge   // 把master分支合并到自己的分支
git add.
git commit -m '修复了xxxx'
git push origin 分支名

### 拉取已有代码 步骤 命令
// 进入gitee找到项目，有克隆的地址，复制下
git branch --list   // 查看所有分支
git branch 分支名   // 创建分支
git checkout 分支名   // 切换到已创建好的分支


### 本地代码提交到代码仓库 新项目初始化提交 步骤命令
git init    // 初始化git仓库
git add .   // 将当前目录的所有文件添加到暂存区
git commit -m '修复了xxxx'    // 将暂存区提交到本地仓库
git remote add origin 远程仓库地址    // 连接到远程仓库
git push -u origin 你的分支名   // 提交到远程仓库 



分支管理
答：
    1、创建分支
     创建分支很简单：git branch <分支名>
     2、切换分支
     git checkout <分支名>
     该语句和上一个语句可以和起来用一个语句表示：git checkout -b <分支名>
     3、分支合并
     比如，如果要将开发中的分支（develop），合并到稳定分支（master），
     首先切换的master分支：git checkout master。
     然后执行合并操作：git merge develop。
     如果有冲突，会提示你，调用git status查看冲突文件。
     解决冲突，然后调用git add或git rm将解决后的文件暂存。
     所有冲突解决后，git commit 提交更改。
     4、分支衍合
     分支衍合和分支合并的差别在于，分支衍合不会保留合并的日志，不留痕迹，而 分支合并则会保留合并的日志。
     要将开发中的分支（develop），衍合到稳定分支（master）。
     首先切换的master分支：git checkout master。
     然后执行衍和操作：git rebase develop。
     如果有冲突，会提示你，调用git status查看冲突文件。
     解决冲突，然后调用git add或git rm将解决后的文件暂存。
     所有冲突解决后，git rebase --continue 提交更改。
     5、删除分支
     执行git branch -d <分支名>
     如果该分支没有合并到主分支会报错，可以用以下命令强制删除git branch -D <分支名>




