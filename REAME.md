This project is for git learning.

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
    - HEAD：一个指针，指向最新的版本
- git reflog：查看版本历史（用于撤销回退）
- git status：查看当前工作区的状态（提示有哪些文件修改了，有哪些文件没有跟踪（即新创建的文件））

# 修改
1. git只会将暂存区中的文件提交版本，没有add的修改不会提交。
- git restore --staged 文件名：丢弃暂存区的修改
    - 不加staged参数，表示丢弃工作区的修改，恢复为暂存区或仓库版本

# 恢复
1. 改了工作区，暂存区未改：git restore 文件名 恢复。
2. 改了工作区，且提交到了暂存区：git reset HEAD 文件名，然后 git restore 文件名 恢复。

# 对比文件的不同
1. 对比工作区和当前版本中文件的不同（减号表示前面的有，加号表示后面的有）
    - git diff HEAD 文件名
2. 对比两个版本中文件的不同
    - git diff HEAD^ HEAD 文件名（或使用版本号代替HEAD）

# 删除文件
1. rm 删除文件后，用 git add . 或 git rm 文件名 来同步到暂存区。