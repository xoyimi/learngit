��¼һЩgit����

$ git config --global user.name "xoyimi"  �����û��������� �����¼�ύ����Ϣ,
$ git config --global user.email xoyimi@foxmail.com   ����д�뵽���ÿһ���ύ�У����ɸ���
����ض���Ŀʹ�ò�ͬ���û��������ʼ���ַʱ ���Ǹ���ĿĿ¼������û�� --global ѡ������������á�
$ git config --list   �г����� Git ��ʱ���ҵ�������
$ git init   �ڵ�ǰĿ¼�г�ʼ���ֿ�
$ git remote add origin git@github.com:xoyimi/learngit.git   ����Զ�ֿ̲�
$ git remote -v   �鿴Զ�ֿ̲�
$ git remote rm origin   ɾ���ѹ�����Զ�̿�
$ git clone git@github.com:xoyimi/learngit.git   ��¡���еĲֿ�
$ git status ��鵱ǰ�ļ�״̬
$ git add [file] �����ļ�,��ӵ��ݴ���
$ git diff   Ҫ�鿴��δ�ݴ���ļ���������Щ����
$ git diff --staged/--cached   �鿴���ݴ�Ľ�Ҫ��ӵ��´��ύ�������
$ git commit -m "�ύ˵��"    �ύ����
$ git commit -a   �������Ѿ����ٹ����ļ��ݴ�����һ���ύ���Ӷ����� git add ����
$ git rm file    ���ݴ������Ƴ��ļ��ݴ������Ƴ��������ӹ���Ŀ¼��ɾ��ָ�����ļ�
$ git mv file_from file_to   ��Git�ж��ļ�����
��ʵ������ git mv ���൱�������������������
$ mv README.md README 
$ git rm README.md
$ git add README
$ git log   ���ύʱ���г����еĸ��£�ÿ���ύ�� SHA-1 У��͡������� �ʼ���ַ���ύʱ���Լ��ύ˵��
$ git log -p -2   -p ������ʾÿ���ύ�����ݲ��졣 -2 ����ʾ��������ύ
$ git reset HEAD file  ȡ���ݴ���ļ�
$git checkout -- file �������ļ����޸�
���ڰ汾����/����
1.û��git addʱ����git checkout -- file
2.�Ѿ�git addʱ����git reset HEAD <file>���˵�1.���ٰ�1.����
3.�Ѿ�git commitʱ����git reset���˰汾
4.���͵�Զ�̿⣬GG?

$ git push [remote-name] [branch-name] ���͵�Զ�ֿ̲�
$ git pull [remote-name] [branch-name] ץȡ����
$ git branch --set-upstream-to=origin/dev dev ָ������dev��֧��Զ��origin/dev��֧������
������ͬһ����֧��Э��ʱ�������׳��ֳ�ͻ����ʹû�г�ͻ����push��ͯЬ���ò���pull��
�ڱ��غϲ���Ȼ�����push�ɹ���
$ git rebase   rebase�������԰ѱ���δpush�ķֲ��ύ��ʷ�����ֱ�ߣ�
rebase��Ŀ����ʹ�������ڲ鿴��ʷ�ύ�ı仯ʱ�����ף���Ϊ�ֲ���ύ��Ҫ�����Աȡ�
$ git tag v1.0 ��һ���±�ǩ,Ĭ���������µ�commit�ϴ�,Ҳ���Դ���֮ǰ������,$ git tag v0.9 f52c633
$ git show <tagname>   �鿴��ǩ��Ϣ
$ git tag -a v0.1 -m "version 0.1 released" 1094adb  ��������˵���ı�ǩ��-a ָ����ǩ����-m ָ���ύ˵��
$ git push origin <tagname>   ��������һ�����ر�ǩ
$ git push origin --tags   ��������ȫ��δ���͹��ı��ر�ǩ
$ git tag -d <tagname>   ����ɾ��һ�����ر�ǩ
$ git push origin :refs/tags/<tagname>   ����ɾ��һ��Զ�̱�ǩ
$ git config --global alias.st status   �����������
$ git config --global alias.lg "log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit"
��GitHub�ϣ���������Fork��Դ�ֿ⣻
�Լ�ӵ��Fork��Ĳֿ�Ķ�дȨ�ޣ�
��������pull request���ٷ��ֿ������״��롣
.gitignore ���ļ����г�Ҫ���Ե��ļ�ģʽ��
