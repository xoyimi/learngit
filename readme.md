记录一些git命令

$ git config --global user.name "xoyimi"  设置用户名和邮箱 方便记录提交者信息,
$ git config --global user.email xoyimi@foxmail.com   它会写入到你的每一次提交中，不可更改
针对特定项目使用不同的用户名称与邮件地址时 在那个项目目录下运行没有 --global 选项的命令来配置。
$ git config --list   列出所有 Git 当时能找到的配置
$ git init   在当前目录中初始化仓库
$ git remote add origin git@github.com:xoyimi/learngit.git   关联远程仓库
$ git remote -v   查看远程仓库
$ git remote rm origin   删除已关联的远程库
$ git clone git@github.com:xoyimi/learngit.git   克隆现有的仓库
$ git status 检查当前文件状态
$ git add [file] 跟踪文件,添加到暂存区
$ git diff   要查看尚未暂存的文件更新了哪些部分
$ git diff --staged/--cached   查看已暂存的将要添加到下次提交里的内容
$ git commit -m "提交说明"    提交更新
$ git commit -a   把所有已经跟踪过的文件暂存起来一并提交，从而跳过 git add 步骤
$ git rm file    从暂存区域移除文件暂存区域移除并连带从工作目录中删除指定的文件
$ git mv file_from file_to   在Git中对文件改名
其实，运行 git mv 就相当于运行了下面三条命令：
$ mv README.md README 
$ git rm README.md
$ git add README
$ git log   按提交时间列出所有的更新，每个提交的 SHA-1 校验和、作者名 邮件地址、提交时间以及提交说明
$ git log -p -2   -p 用来显示每次提交的内容差异。 -2 仅显示最近两次提交
$ git reset HEAD file  取消暂存的文件
$git checkout -- file 撤消对文件的修改
关于版本回退/撤销
1.没有git add时，用git checkout -- file
2.已经git add时，先git reset HEAD <file>回退到1.，再按1.操作
3.已经git commit时，用git reset回退版本
4.推送到远程库，GG?

$ git push [remote-name] [branch-name] 推送到远程仓库
$ git pull [remote-name] [branch-name] 抓取下来
$ git branch --set-upstream-to=origin/dev dev 指定本地dev分支和远程origin/dev分支的链接
多人在同一个分支上协作时，很容易出现冲突。即使没有冲突，后push的童鞋不得不先pull，
在本地合并，然后才能push成功。
$ git rebase   rebase操作可以把本地未push的分叉提交历史整理成直线；
rebase的目的是使得我们在查看历史提交的变化时更容易，因为分叉的提交需要三方对比。
$ git tag v1.0 打一个新标签,默认是在最新的commit上打,也可以打在之前的上面,$ git tag v0.9 f52c633
$ git show <tagname>   查看标签信息
$ git tag -a v0.1 -m "version 0.1 released" 1094adb  创建带有说明的标签，-a 指定标签名，-m 指定提交说明
$ git push origin <tagname>   可以推送一个本地标签
$ git push origin --tags   可以推送全部未推送过的本地标签
$ git tag -d <tagname>   可以删除一个本地标签
$ git push origin :refs/tags/<tagname>   可以删除一个远程标签
$ git config --global alias.st status   配置命令别名
$ git config --global alias.lg "log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit"
在GitHub上，可以任意Fork开源仓库；
自己拥有Fork后的仓库的读写权限；
可以推送pull request给官方仓库来贡献代码。
.gitignore 的文件，列出要忽略的文件模式。
