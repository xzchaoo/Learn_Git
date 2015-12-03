# Learn_Git
���� GitȨ��ָ��(���� ��) �ıʼ�

## ���� ##
����|˵��
:-:|:-:
���ؼ�(Ĭ��)|ֱ������Ŀ��.git/config�����������
�û���(--global)|�ڵ�ǰ������û��������ļ����������: C:\Users\Administrator\.gitconfig
ϵͳ��(--system)|D:\Program Files (x86)\Git\etc\.gitconfig


### ��ȡ���� ###
	git config --global user.name, ���ǻ�ȡȫ�ּ����user.name
	��Ȼ��Ҳ����ֱ�Ӵ���Ӧ���ļ�ȥ�鿴��...
	
### �������� ###
	git config key value, ��ȻҲ����ֱ�Ӵ��ļ������޸�
���� git config a.b.c.d hehe(��Ĭ���Ǳ����޸�)�Ľ����
```ini
[a "b.c"]
	d = hehe
```

#### ע�� ####
user.name��user.email���ڼ�¼�ύ�ߵ���Ϣ

### �� ###
ʹ�� git config -e --global ���git�Դ���vi���û������ļ����������޸�
### git���� ###
git config --system alias.st status
git config --system alias.ci commit


### ���� ###
>git config --global user.name "xzchaoo",����ȫ�ּ����user.name


## ״̬ ##
�г���ǰ��������״̬
git status

����|˵��
:-:|:-:
s|���ģʽ
b|��ʾ��ǰ������֧������

### ���ģʽ ###
git status -s
��һ�е�M��ʾ��ǰ�Ļ������뵱ǰ��HEAD�в��
�ڶ��е�M��ʾ��ǰ�������뻺�������ļ��в��


## ���� ##
git grep �ؼ���

## ��¡ ##

git clone

git fetch
	����ڵ�ǰ�������Ѿ���¡��һ����,����ʹ��fetch �ٴλ�ȡ�°汾(����òֿ�����˸��µĻ�)

### ���� ###
git clone https://github.com/takahirom/PreLollipopTransition, ���òֿ⸴�Ƶ���ǰĿ¼�µ�PreLollipopTransition


## TAG ��̱� ##

## ��־ ##

log

����|����
:-:|:-:
pretty|fuller,oneline,raw
stat|��ӡ��ǰ�����εĲ�֮ͬ��
graph|ͼ��
online|һ��


## �� ##
> gitҲ���Զ�svn�ֿ���в���

## �Ƚ� ##
diff:�鿴����֮��Ĳ�ͬ
������"����"�����Ǻܶ�
Ĭ���ǲ鿴�������ͻ������Ĳ��

git diff �鿴��ǰ�������ͻ�����������
git diff HEAD �鿴��ǰ��������HEAD�Ĳ��
git diff --cached �鿴��ǰ��������HEAD�Ĳ��

����|˵��
:-:|:-:
cached/staged|�Ƚϻ�������HEAD������

## HEAD����� ##
��ǰ�汾���ͷָ��
HEADͨ��ָ��refs/heads/master
��masterͨ��ָʾ��һ���ύ

## reset ##
�޸ĵ�ǰ��HEAD,��ָ����״̬
git reset HEAD <file>: �޸Ļ�������<file>�ļ�ΪHEAD��<file>�ļ�,�������������<file>�ļ�����ȥ

git reset [--soft | --mixed | hard] [<commit>]
--soft��HEADָ��<commit>
--mixed,��HEADָ��<commit>,����������Ϊ<commit>������,����Ĭ����Ϊ
--hard, ��HEADָ��<commit>,�������͹���������Ϊ<commit>������
����git reset,����HEAD���ǻ�����������,�൱��ȡ������������޸�


	
## checkout ##
git checkout -- 2.txt: �����������2.txt�ŵ�������
git checkout HEAD -- 1.txt ��HEAD��1.txt�滻�������ͻ�����

git checkout ĳ���汾��
���ܽ������ͷģʽ
,Ҳ����˵��ǰ��HEADָ����ĳ������İ汾�Ŷ�����master

git checkout
	��ʾ��������Ĳ��
git checkout ĳ��֧����
HEAD��ָ��ᷢ���仯
�л���ĳ����֧,������������ݶ������

git checkout �µķ�֧�� ��֧�����
���ڼ򵥵Ĵ���һ���µķ�֧ �����л�����
�����ڷ���ͷģʽ��ʱ��,��Ϊ���پ�����master

git checkout master
	�л���master�������



## rm ##
git rm --cached 1.txt: ɾ���������е�1.txt, �Թ������������Ӱ��


## clean ##
git clean -n ����
git clean -fd ɾ����ǰ·���µ�����û�б�׷�ٵ��ļ�

## branch ##
git branch �鿴��ǰ�ķ�֧����
-v
## reflog ##
.git/logs/refs/heads/master�����¼��master��֧���޸ļ�¼,ÿһ�����masterָ�����ı��ʱ��,���ﶼ���м�¼
����ֱ�Ӵ����鿴
����ʹ��git reflog show master ���в鿴

## merge ##
����ǰ��֧���ƶ���֧�ϲ�

## �� ##
git rev-parse master
	�鿴master��֧��Ӧ���ύ
git cat-file commit HEAD
	�鿴HEAD��Ӧ���ύ������
ʹ��master�����֧master�е������ύ
ʹ��HEAD����汾���������һ���ύ
^���Ա�ʾ���ύ
HEAD^ HEAD^^ a573106^2 �൱��HEAD^^

git reset --hard HEAD^
��masterָ��HEAD^,��������ָ����--hard,���Թ������ͻ�����������ҳ���滻��HEAD^

git show acc2f69 ��ʾ����ύ����Ϣ

## stash ##
**stashֻ�������Щ��������ļ�**
git stash ���浱ǰ�������ͻ�����,Ȼ�󽫹������ͻ��������ָ���HEAD
list
pop �������һ�α���,�ָ��������ͻ�����
	--index ���˻ָ������������Իָ������� ����ֻ�й��������ָ�
apply �����һ�α���ָ��������ͻ�����,�������е���
clear �������һ�α���,�������лָ�,�൱��ɾ�����һ�α���
git stash [save [-k] [-q] [message]]
	-k stashִ��֮����ջ����� -q����

tag
describe ��tag��sha1������ǰ�İ汾
git ls-files
	�г�λ�ڻ��������ļ�

git ls-files --with-tree=HEAD^
git cat-file -p HEAD^:1.txt
�ָ��ļ�
git cat-file -p HEAD^:1.txt > 1.txt ��HEAD^1�ָ�1.txt��������
git checkout HEAD^1 -- 1.txt
mv

git log --onlne --decorate -3
git add -i ���뽻��ģʽ


"ls" �� "git ls"������
git add -u
	���������еĸĶ���ɾ����ӵ���������
	��Ƶ����ļ�ֻ�б�git�������ļ�

git cat-file -p HEAD~1:1.txt
git show HEAD~1:1.txt
	��ʾ�ļ�������

git checkout HEAD~1 -- 1.txt
	��HEAD~1���1.txt���Ƶ��������͹�����


�ļ����� ͨ��.gitignore�ļ�
!lib.a ��������
/TODO ��ǰĿ¼�µ�!�ļ�!
/TODO/ ��ǰĿ¼�µ�!�ļ���!
1.txt ���н���1.txt�� ����Ŀ¼����
/1.txt ��ǰĿ¼�µ�1.txt
# �����Լ�
.gitignore

# ���Ե�ǰĿ¼�µ�1.txt
/1.txt


# �������н���222.txt��
222.txt

# ��������tempĿ¼�µ�ȫ��
temp/**

ceshi/*.bak

ceshi/**/3.txt


# 10.9 �ļ��鵵 #
�������ݿ�Ľ�������

#  #
## cherry-pick ##
���Խ�ĳ���ύ�ڵ�ǰ�İ汾�Ͻ����ط�
git cherry-picker <commit>
ֻ������ִ���������������, ����൱����һ���µ��ύ

## rebase ##
	--continue
	--abort
	--skip
git rebase [--onto <newbase>] <from> <to>
	��<from>��<to>���޸��طŵ�<newbase>(Ĭ����<from>)
	Ȼ��HEADָ�����ս��
	���from������to������, ��ô���跨�ҵ����ǵĹ�������������
	from, to֮����˶����޸Ŀ���ʹ��
	git log from..to ���鿴
	

# 13 #
## ����ֿ� ##
clone pull push fetch

Ĭ�������, ֻ����push��һ����ֿ�(û�й������Ĳֿ�)
git clone --bare ...
git clone --mirror ...
ʹ��clone��ʱ,���Դ�ֿ����ע��

git init --bare

����һ���ǵ��ڶ����ֿ������ git pull �Խ���ͬ��

git push url master:master
�����ص�master�Ƶ�url��master

�� refs/heads/ ��ͷ���Ƿ�֧
�� refs/remotes/ ��ͷ����Զ�̷�֧�ڱ��ص�ӳ��
�� refs/tags/ ��ͷ������̱�

# 14 #
git fsck
git prune
git reflog
git gc �Զ�����

# 15 #
pull = fetch + merge

# 16 ��ͻ��� #
�ؼ���Ҫ���ö�git diff�ĸ�ʽ
## diff��ʽ ##
http://www.ruanyifeng.com/blog/2012/08/how_to_read_diff.html

git blame 1.txt ����׷��1.txtÿһ�е���Դ
һ����˵�������push��ʱ��, Ҫ����Ļ��汾�����˵�master��Ӧ, �������ܽ��п��ʽ�ύ
�����һ�µ�ʱ��, ��Ҫ������git pull
git pull  = git fetch + git merge
���merge�ɹ�, ��ûʲô��˵�� ...
���mergeʧ��, ��ô��Ҫ�ֶ������ͻ
	�����ʱ����ĳ�ͻ�ļ����� 1.txt ����Ѿ����޸ĳ� ����:
	<<<<<<< HEAD
	����2 2
	=======
	����2 1
	>>>>>>> ff0b952bf3f5125e98e9bdd762926d839c663b3e
	����Ҫ�ֶ��������, �����100��, ����������, Ȼ�������3��, ����̫����, ��������κϲ� �ص�merge֮ǰ
	��ôʹ�� merge --abort ��������merge

# 17 ��̱� #
��̱�ʵ���Ͼ���ָ��һ���ύ, ҪΨһȷ��һ���ύ�Ļ���Ҫ������sha1, ���ǲ��ü� ���Ǿ���tag
git tag �鿴��̱��б�
git describe

## ������̱� ##
git tag -m "������Ϣ" ����ǰ���ڵ�HEAD����һ����̱� <tagname> [<commit>]
	-m
	-d <tagname> ɾ����̱�

## �ϴ���̱� ##
һ���������̱����ᱻpush���ֿ�
git push origin mytag �����ص�mytag�Ƶ�origin��mytag
git push origin refs/tags/*
git ls-remote origin my*

## ɾ��Զ����̱� ##
git push <remote_url> :<tagname> ��û�� ����Ҫ����д, �� �� ���͵�Զ�̵�tagname

# 18 ��֧ #
git branch <branch-name> �Ե�ǰcommitΪ����, ����һ����֧
git branch�鿴��ǰ��֧
	-v ���sha1
	-d <branch-name> ɾ����֧
	-b <branch-name> [<commit>] ��<commit>Ϊ��㽨��һ����֧

git push origin hello-1.x �Ƶ�origin

git format-patch a..b
����a��b�ı仯���һ������


# 19 Զ�̰汾�� #
git ls-remote �鿴Զ������Щ��֧
git show-ref ��ʾȫ���ı�������
git branch -r �鿴Զ�̷�֧
git checkout -b <branch-name> [<start-point>]
	��start-point(Ĭ��ΪHEAD)Ϊ���, ������֧branch-name
����Զ��branch������֧�Ļ�, ����׷�ٹ���
���ڱ��ط�֧1������֧2�Ļ�, ������׷�ٹ���
	�÷�֧1�ǻ���ĳ��Զ�̷�֧��, �����ڴ�����֧2��ʱ��ʹ���� --track
	�Ż���׷�ٹ��ܴ��ݹ���

git remote -v �鿴Զ�̰汾��

ע��Զ�̰汾��
git remote add <remote-name> <url>
git remote rename <old-remote-name> <new-remote-name> �������ʽ������, ���Զ��޸������ط�������, ��˱Ƚϰ�ȫ

ִ��git fetch������ʱ��, Ĭ���ǴӸ÷�֧���õ�remote��merge������fetch����
��.gitĿ¼�µ�gitconfig�ļ�
```
[branch "master"]
	remote = origin
	merge = refs/heads/master
#	rebase = true
```
git pullĬ�ϻ�ִ��merge���� �����޸������ΪΪrebase����, ֻ��Ҫ����������ü���rebase = true

ddbranch.autosetuprebase

git fetch --no-tags fetchĬ�ϻ��ȡtag, ȡ����




# �� #

reset���޸ĵ�ǰHEAD��ָ��ķ�֧������
checkout���޸ĵ�ǰHEAD����

git reflog HEAD
	 ���Բ鿴���HEAD����ָ����ύ�ı仯
	
merge�ϲ�������֧
git log --graph --pretty=oneline
git cat-file -p HEAD
	-p �����õĸ�ʽ��ʾHEAD������
	-t ��ʾHEAD������

ɾ��������ļ����ļ�(δ�ܹ���)
git clean -nd
git clean -fd

git rev-parse <object> ���Բ鿴����object��id
����master, ��ʵ���ǿ������ĸ��ύ

git rev-list --pretty=oneline a..b


git cherry ���Բ鿴����master��Զ��master���ȵ�����
	Ҳ���Ǵ�ʱ���ִ��push, ���ᱻ�޸ĵ�����

# ��־ #
git log -1 -m --stat
	���Բ鿴���һ���ύ���޸�
git log --online --graph -3


# git��ϰ #
## ����1 ##
### ���� ###
1����Ŀ, 2�������
	��ʼ��
		main.cpp ������10������ ��2�������, �ֹ�������
		changelog.txt ��2���˹�ͬ���
		readme.txt �����˶����������, û������Ҫ��
����:
	1. int add(int a, int b){}
	2. int sub(int a, int b){}
	3. int mul(int a, int b){}
	4. int div(int a, int b){}
	5. int mod(int a, int b){}
	6. int sum(int from, int to){} ��from+(from+1)+...+to�Ľ��
	7. int jc(int n){} ��n�׳�
	8. int fib(int n){} 쳲��������е�n��
	9. void about(){} ��ӡ "Today is a good day."
	10. int abs(int x){}
Ϊ��ģ����Ҫ, ���ҽ���Щ���������Ǻܸ��ӵĺ���
1-5�ɵ�һ�������
6-10�ɵ�һ�������
�����˸���һ��branchȥ����¹���, ÿ����һ���Կ�����ɶ������, ���֮����Ҫ��changelog.txt�������һЩ˵��. Ȼ��5���������Էֶ�����, ÿ������֮��Ҫ�ϲ���master��
��user1����main.cpp changelog.txt readme.txt��3���ļ��ĳ�ʼ����
���ߵ�master,Ҫ��һЩ�޹ؽ�Ҫ���ύ,��ģ���������ύ

1. ������ֿ�
	git init --bare eg1
2. user1 cloneһ���ֿ�
	git clone ./eg1 ./eg1-1
	���ú�name��email
	git config user.name user1
	git config user.email user1@abc.com
	(user2������)����main.cpp changelog.txt readme.txt�ĳ�ʼ����, ���ҽ���һ����̱�t1,����push��origin
3. user2 ����

��һ��
4. user1��t1Ϊ��������һ���·�֧b1, �����л���b1
5. user2��t1Ϊ��������һ���·�֧b2, �����л���b2
6. user1��һ���ύ�����add,sub 2������, ���ұ�дchangelog, commit �� push
	����û��ע�⵽add��ʵ��������, ����д���� return a+b+1;

6.5. ��һ��user3, ��master�������˵㶫��,Ȼ��commit,��push

7. user2��һ�������sum,jc 2������, ���ұ�дchangelog, commit ���� push
	����û��ע�⵽sum��ʵ��������, ����s��ʼ��Ϊ1������0

8. user2��ȷ�������fib, about, abs 3������ ... commit
9. user2��������֮ǰ�Ĵ���,���ҽ�������, ����user2�Ĺ���ȫ����ȷ��, ���÷�֧�Ĺ��ܺϲ���master��, ����ɾ���÷�֧, ��ʱmaster������user2��ʵ�ֹ���,���ҽ���һ����̱�v1.1
	��Ҫ��ͨ��rebase
10. user1��ȷ�����mul, div, mod 3������... commit, push,���÷�֧�Ĺ��ܺϲ���master��, ����ɾ���÷�֧, ��ʱmaster������user1��ʵ�ֹ���,���ҽ���һ����̱�t4
11. �������(���ڼ�������������ύ����������, �������Ҫ����ģ��һ��), ����user1֮ǰ��addʵ��������, ���ڱ�������, ��user1����̱�t4��ʼ����һ���µķ�֧b3, Ȼ���������֧����add���� ���ҽ����ύ, �ϲ���master.
12. ����master��ʵ����10������

HEAD^��HEAD@{1}��һ��
HEAD^��ָ��ǰHEADָ����ύ�ĸ��ύ
HEAD@{1}��ָHEAD����һ��ֵ
һ��commit֮��HEAD��ֵ����(��Ϊ��ͨ����ָ��master,���Ա����master)
����checkout,reset��ʱ��HEAD����ͻ�仯��


# 20 �����ļ����� #
git format-patch -s a..b
	-s ���ǩ��
git send-email *.patch


# 24 ��ģ�� #
ʹ��git submodule add url dir
��һ����ģ����ӵ���ǰ�Ĳֿ��dirĿ¼��
	����ģ������ݻ����ϱ�checkout����
	������Ӹ���ģ���ʱ��, ��ģ���master��sha1Ϊ1...
	
����cloneһ���ֿ�,������ֿ������ģ��Ļ�, ��ģ��ľ��������ǲ��ᱻ���Ƶ�
����Ŀ¼�ᱻclone����,��������û������
��������һЩ��Ϣ, ����url���е�, ���Ǳ�����.gitmodules��
.gitmodules��������һ����ͨ���ļ����뵽�ֿ���

��ʱ������Ҫ�ֶ�ʹ�� git submodule init���г�ʼ��
	��仰����.git/config������д����submodule����Ϣ
	
Ȼ��ʹ�� git submodule update
	��ʹ����ģ������ݱ����ؽ���
	��ʵ���ǽ���ģ��checkout����Ӧλ��
�����ؽ�������ģ��Ĭ�϶��Ƿ���ͷ״̬, ���Ҵ�ʱHEADָ��1...
	ע��, �����update֮ǰ, ����ģ��Ĳֿ��master�Ѿ�����ָ��1...��
	��ô�÷���ͷ����ָ��1...


# add #
# rm #
# ls-files #
# reset #
# branch #
# remote #
# ls-remotes #
# checkout #
# status #
# log #
# show #
# diff #
# cat-file #
# rev-parse #