git is a distributed version control system.
git is a free softawre distributed under the GPL.
git has a mutable index called stage.
git tracks changes of files.

记录一些git命令
关于版本回退/撤销
1.没有git add时，用git checkout -- file

2.已经git add时，先git reset HEAD <file>回退到1.，再按1.操作

3.已经git commit时，用git reset回退版本

4.推送到远程库，GG?