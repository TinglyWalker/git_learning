This project is for git learning and test.

# 常用操作
- git init: 用git管理当前目录下的代码
- git add 文件名/.：将文件移交到暂存库
- git commit -m 'message'：提交版本

# 查看操作
- git log --oneline：查看之前的所有版本号
- git reset --hard HEAD^/HEAD~1/版本号：回退上一个/指定版本
    - --hard：暂存区清空，工作区清空。
    - --mixed（默认）：暂存区清空，工作区保留
    - --soft：暂存区保留，工作区保留
    - HEAD：一个指针，指向当前分支的最新版本
- git reflog：查看版本历史（用于撤销回退）
- git status：查看当前工作区的状态（提示有哪些文件修改了，有哪些文件没有跟踪（即新创建的文件））

# 修改
1. git只会将暂存区中的文件提交版本，没有add的修改不会提交
- git restore --staged 文件名：丢弃暂存区的修改（改为 HEAD 的版本）
    - 不加staged参数，表示丢弃工作区的修改（改为 暂存区 的版本）

# 恢复
1. 改了工作区，暂存区未改：git restore 文件名 恢复。
2. 改了工作区，且提交到了暂存区：git restore --staged 文件名，然后 git restore 文件名 恢复。

# 对比文件的不同
1. 对比工作区和当前版本中文件的不同（减号表示前面的有，加号表示后面的有）
    - git diff HEAD 文件名
2. 对比两个版本中文件的不同
    - git diff HEAD^ HEAD 文件名（或使用版本号代替HEAD）

# 删除文件
1. rm 删除文件后，用 git add . 或 git rm 文件名 来同步到暂存区。


# 分支
1. 创建分支，就是新建一个 branch 指针，指向新版本。将 HEAD 指向 branch。后续的修改会移动 branch，而 master 指针不动；
    * 快速合并：master 没变，直接将 master 移动到 branch 的位置。
    * 无法快速合并：master 修改了 file1，branch 新建了 file2。合并之后会做一次新的提交，并弹出弹窗，写提交的说明信息。
    - git merge --no-ff -m 'xxx' 分支名：禁止快速合并，方便之后看到提交信息。
- git branch：查看分支，以及在哪个分支下工作
- git branch 分支名：创建一个新的分支
- git switch 分支名：切换分支
- git switch -c 分支名：创建并切换 

- git merge 分支名（在 master 上操作）：合并分支
- git branch -d 分支名：删除已合并的分支（安全）
- git branch -D 分支名：强制删除，不管是否合并

2. 解决分支冲突：两个不同的分支各自有新的提交，会产生冲突。
    手动更改后，重新提交。
- git log --graph --oneline：查看冲突合并过程图。

3. 临时保存当前分支，当前分支工作内容清空（要新的分支改 bug，但是当前分支的任务还不能提交）
- git stash：保存
- git stash list：查看已保存的
- git stash pop：恢复工作现场

# github
1. 创建仓库 == git init
2. 配置 Email 和 name ：.git_config 文件
3. 生成 ssh 密钥：ssh-keygen -t rsa -C "邮箱地址"
4. 到提示的目录下找 id_rsa（私钥）和 id_rsa.pub（公钥）
5. 将公钥添加到 GitHub
6. 若本地没有项目：
- 用 SSH 地址 clone
    - git clone 地址
7. 若本地有项目要推送：
    - git remote add origin 仓库地址（将仓库地址的别名设为 origin）
8. 推送：git push origin 分支名称
