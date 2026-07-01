This project is for git learning.

- git init: 用git管理当前目录下的代码
- git add 文件名/.：将文件移交到暂存库
- git commit -m 'message'：提交版本

- git log --oneline：查看之前的所有版本号
- git reset --hard HEAD^/HEAD~1/版本号：回退上一个/指定版本
    - --hard：暂存区清空，工作区清空。
    - --mixed（默认）：暂存区清空，工作区保留
    - --soft：暂存区保留，工作区保留
- git reflog：查看版本历史（用于撤销回退）
- git status：查看当前工作区的状态（提示有哪些文件修改了，有哪些文件没有跟踪（即新创建的文件））