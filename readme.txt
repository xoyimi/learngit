git is a distributed version control system.
git is a free softawre distributed under the GPL.
git has a mutable index called stage.
git tracks changes of files.

记录一些git命令
1.设置用户名称和邮件地址.这样做很重要。
因为每一个 Git 的提交都会使用这些信息，并且它会写入到你的每一次提交中，不可更改：
$ git config --global user.name "John Doe"
$ git config --global user.email johndoe@example.com
再次强调，如果使用了 --global 选项，那么该命令只需要运行一次，
因为之后无论你在该系统上做任何事情， Git 都会使用那些信息。 
当你想针对特定项目使用不同的用户名称与邮件地址时，
可以在那个项目目录下运行没有 --global 选项的命令来配置。

2.检查配置信息

如果想要检查你的配置，可以使用 git config --list 命令来列出所有 Git 当时能找到的配置。

$ git config --list
user.name=John Doe
user.email=johndoe@example.com
color.status=auto
color.branch=auto
color.interactive=auto
color.diff=auto
...


3.在现有目录中初始化仓库

如果你打算使用 Git 来对现有的项目进行管理，你只需要进入该项目目录并输入：

$ git init

4.克隆现有的仓库
$ git clone https://github.com/libgit2/libgit2 mylibgit
$ git clone git@github.com:xoyimi/*.git


$ git status 检查当前文件状态
$ git status -s/--short 状态简览
你将得到一种更为紧凑的格式输出。 运行 git status -s ，状态报告输出如下：
$ git status -s
 M README
MM Rakefile
A  lib/git.rb
M  lib/simplegit.rb
?? LICENSE.txt

新添加的未跟踪文件前面有 ?? 标记，新添加到暂存区中的文件前面有 A 标记，修改过的文件前面有 M 标记。 你可能注意到了 M 有两个可以出现的位置，出现在右边的 M 表示该文件被修改了但是还没放入暂存区，出现在靠左边的 M 表示该文件被修改了并放入了暂存区。 例如，上面的状态报告显示： README 文件在工作区被修改了但是还没有将修改后的文件放入暂存区,lib/simplegit.rb 文件被修改了并将修改后的文件放入了暂存区。 而 Rakefile 在工作区被修改并提交到暂存区后又在工作区中被修改了，所以在暂存区和工作区都有该文件被修改了的记录。



$ git add [file] 跟踪文件,并处于暂存状态

忽略文件

一般我们总会有些文件无需纳入 Git 的管理，也不希望它们总出现在未跟踪文件列表。 通常都是些自动生成的文件，比如日志文件，或者编译过程中创建的临时文件等。 在这种情况下，我们可以创建一个名为 .gitignore 的文件，列出要忽略的文件模式。 来看一个实际的例子：

$ cat .gitignore
*.[oa]
*~

第一行告诉 Git 忽略所有以 .o 或 .a 结尾的文件。一般这类对象文件和存档文件都是编译过程中出现的。 第二行告诉 Git 忽略所有以波浪符（~）结尾的文件，许多文本编辑软件（比如 Emacs）都用这样的文件名保存副本。 此外，你可能还需要忽略 log，tmp 或者 pid 目录，以及自动生成的文档等等。 要养成一开始就设置好 .gitignore 文件的习惯，以免将来误提交这类无用的文件。

文件 .gitignore 的格式规范如下：

    所有空行或者以 ＃ 开头的行都会被 Git 忽略。

    可以使用标准的 glob 模式匹配。

    匹配模式可以以（/）开头防止递归。

    匹配模式可以以（/）结尾指定目录。

    要忽略指定模式以外的文件或目录，可以在模式前加上惊叹号（!）取反。

所谓的 glob 模式是指 shell 所使用的简化了的正则表达式。 星号（*）匹配零个或多个任意字符；[abc] 匹配任何一个列在方括号中的字符（这个例子要么匹配一个 a，要么匹配一个 b，要么匹配一个 c）；问号（?）只匹配一个任意字符；如果在方括号中使用短划线分隔两个字符，表示所有在这两个字符范围内的都可以匹配（比如 [0-9] 表示匹配所有 0 到 9 的数字）。 使用两个星号（*) 表示匹配任意中间目录，比如 a/**/z 可以匹配 a/z , a/b/z 或 a/b/c/z 等。

我们再看一个 .gitignore 文件的例子：

# no .a files
*.a

# but do track lib.a, even though you're ignoring .a files above
!lib.a

# only ignore the TODO file in the current directory, not subdir/TODO
/TODO

# ignore all files in the build/ directory
build/

# ignore doc/notes.txt, but not doc/server/arch.txt
doc/*.txt

# ignore all .pdf files in the doc/ directory
doc/**/*.pdf


$ git diff   要查看尚未暂存的文件更新了哪些部分
$ git diff --staged/--cached   查看已暂存的将要添加到下次提交里的内容
$ git commit -m "提交信息"    提交更新
$ git commit -a   把所有已经跟踪过的文件暂存起来一并提交，从而跳过 git add 步骤
$ git rm file    从暂存区域移除文件暂存区域移除并连带从工作目录中删除指定的文件

$ git mv file_from file_to 在Git中对文件改名
其实，运行 git mv 就相当于运行了下面三条命令：
$ mv README.md README 
$ git rm README.md
$ git add README

$ git log 会按提交时间列出所有的更新，最近的更新排在最上面。
会列出每个提交的 SHA-1 校验和、作者的名字和电子邮件地址、提交时间以及提交说明。
$ git log -p -2     -p，用来显示每次提交的内容差异。 你也可以加上 -2 来仅显示最近两次提交
$ git reset HEAD file  取消暂存的文件
$git checkout -- file 撤消对文件的修改
关于版本回退/撤销
1.没有git add时，用git checkout -- file

2.已经git add时，先git reset HEAD <file>回退到1.，再按1.操作

3.已经git commit时，用git reset回退版本

4.推送到远程库，GG?

$ git remote -v  查看远程仓库
$ git remote add <shortname> <url> 添加远程仓库
git push [remote-name] [branch-name] 推送到远程仓库

Creating a new branch is quick AND simple.