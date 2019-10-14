git is a distributed version control system.
git is a free softawre distributed under the GPL.
git has a mutable index called stage.
git tracks changes of files.

��¼һЩgit����
1.�����û����ƺ��ʼ���ַ.����������Ҫ��
��Ϊÿһ�� Git ���ύ����ʹ����Щ��Ϣ����������д�뵽���ÿһ���ύ�У����ɸ��ģ�
$ git config --global user.name "John Doe"
$ git config --global user.email johndoe@example.com
�ٴ�ǿ�������ʹ���� --global ѡ���ô������ֻ��Ҫ����һ�Σ�
��Ϊ֮���������ڸ�ϵͳ�����κ����飬 Git ����ʹ����Щ��Ϣ�� 
����������ض���Ŀʹ�ò�ͬ���û��������ʼ���ַʱ��
�������Ǹ���ĿĿ¼������û�� --global ѡ������������á�

2.���������Ϣ

�����Ҫ���������ã�����ʹ�� git config --list �������г����� Git ��ʱ���ҵ������á�

$ git config --list
user.name=John Doe
user.email=johndoe@example.com
color.status=auto
color.branch=auto
color.interactive=auto
color.diff=auto
...


3.������Ŀ¼�г�ʼ���ֿ�

��������ʹ�� Git �������е���Ŀ���й�����ֻ��Ҫ�������ĿĿ¼�����룺

$ git init

4.��¡���еĲֿ�
$ git clone https://github.com/libgit2/libgit2 mylibgit
$ git clone git@github.com:xoyimi/*.git


$ git status ��鵱ǰ�ļ�״̬
$ git status -s/--short ״̬����
�㽫�õ�һ�ָ�Ϊ���յĸ�ʽ����� ���� git status -s ��״̬����������£�
$ git status -s
 M README
MM Rakefile
A  lib/git.rb
M  lib/simplegit.rb
?? LICENSE.txt

����ӵ�δ�����ļ�ǰ���� ?? ��ǣ�����ӵ��ݴ����е��ļ�ǰ���� A ��ǣ��޸Ĺ����ļ�ǰ���� M ��ǡ� �����ע�⵽�� M ���������Գ��ֵ�λ�ã��������ұߵ� M ��ʾ���ļ����޸��˵��ǻ�û�����ݴ����������ڿ���ߵ� M ��ʾ���ļ����޸��˲��������ݴ����� ���磬�����״̬������ʾ�� README �ļ��ڹ��������޸��˵��ǻ�û�н��޸ĺ���ļ������ݴ���,lib/simplegit.rb �ļ����޸��˲����޸ĺ���ļ��������ݴ����� �� Rakefile �ڹ��������޸Ĳ��ύ���ݴ��������ڹ������б��޸��ˣ��������ݴ����͹��������и��ļ����޸��˵ļ�¼��



$ git add [file] �����ļ�,�������ݴ�״̬

�����ļ�

һ�������ܻ���Щ�ļ��������� Git �Ĺ���Ҳ��ϣ�������ܳ�����δ�����ļ��б� ͨ������Щ�Զ����ɵ��ļ���������־�ļ������߱�������д�������ʱ�ļ��ȡ� ����������£����ǿ��Դ���һ����Ϊ .gitignore ���ļ����г�Ҫ���Ե��ļ�ģʽ�� ����һ��ʵ�ʵ����ӣ�

$ cat .gitignore
*.[oa]
*~

��һ�и��� Git ���������� .o �� .a ��β���ļ���һ����������ļ��ʹ浵�ļ����Ǳ�������г��ֵġ� �ڶ��и��� Git ���������Բ��˷���~����β���ļ�������ı��༭��������� Emacs�������������ļ������渱���� ���⣬����ܻ���Ҫ���� log��tmp ���� pid Ŀ¼���Լ��Զ����ɵ��ĵ��ȵȡ� Ҫ����һ��ʼ�����ú� .gitignore �ļ���ϰ�ߣ����⽫�����ύ�������õ��ļ���

�ļ� .gitignore �ĸ�ʽ�淶���£�

    ���п��л����� �� ��ͷ���ж��ᱻ Git ���ԡ�

    ����ʹ�ñ�׼�� glob ģʽƥ�䡣

    ƥ��ģʽ�����ԣ�/����ͷ��ֹ�ݹ顣

    ƥ��ģʽ�����ԣ�/����βָ��Ŀ¼��

    Ҫ����ָ��ģʽ������ļ���Ŀ¼��������ģʽǰ���Ͼ�̾�ţ�!��ȡ����

��ν�� glob ģʽ��ָ shell ��ʹ�õļ��˵�������ʽ�� �Ǻţ�*��ƥ��������������ַ���[abc] ƥ���κ�һ�����ڷ������е��ַ����������Ҫôƥ��һ�� a��Ҫôƥ��һ�� b��Ҫôƥ��һ�� c�����ʺţ�?��ֻƥ��һ�������ַ�������ڷ�������ʹ�ö̻��߷ָ������ַ�����ʾ�������������ַ���Χ�ڵĶ�����ƥ�䣨���� [0-9] ��ʾƥ������ 0 �� 9 �����֣��� ʹ�������Ǻţ�*) ��ʾƥ�������м�Ŀ¼������ a/**/z ����ƥ�� a/z , a/b/z �� a/b/c/z �ȡ�

�����ٿ�һ�� .gitignore �ļ������ӣ�

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


$ git diff   Ҫ�鿴��δ�ݴ���ļ���������Щ����
$ git diff --staged/--cached   �鿴���ݴ�Ľ�Ҫ��ӵ��´��ύ�������
$ git commit -m "�ύ��Ϣ"    �ύ����
$ git commit -a   �������Ѿ����ٹ����ļ��ݴ�����һ���ύ���Ӷ����� git add ����
$ git rm file    ���ݴ������Ƴ��ļ��ݴ������Ƴ��������ӹ���Ŀ¼��ɾ��ָ�����ļ�

$ git mv file_from file_to ��Git�ж��ļ�����
��ʵ������ git mv ���൱�������������������
$ mv README.md README 
$ git rm README.md
$ git add README

$ git log �ᰴ�ύʱ���г����еĸ��£�����ĸ������������档
���г�ÿ���ύ�� SHA-1 У��͡����ߵ����ֺ͵����ʼ���ַ���ύʱ���Լ��ύ˵����
$ git log -p -2     -p��������ʾÿ���ύ�����ݲ��졣 ��Ҳ���Լ��� -2 ������ʾ��������ύ
$ git reset HEAD file  ȡ���ݴ���ļ�
$git checkout -- file �������ļ����޸�
���ڰ汾����/����
1.û��git addʱ����git checkout -- file

2.�Ѿ�git addʱ����git reset HEAD <file>���˵�1.���ٰ�1.����

3.�Ѿ�git commitʱ����git reset���˰汾

4.���͵�Զ�̿⣬GG?

$ git remote -v  �鿴Զ�ֿ̲�
$ git remote add <shortname> <url> ���Զ�ֿ̲�
git push [remote-name] [branch-name] ���͵�Զ�ֿ̲�

Creating a new branch is quick AND simple.