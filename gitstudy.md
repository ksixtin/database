## Git Study

## 0. 준비 사항

* [git bash](http://https://gitforwindows.org/) 설치.

  * git을 활용하기 위한 `CLI(Command Line Interface)`를 제공한다.
  * source tree, github desktop 등을 통해 `GUI` 환경에서도 활용 가능하다.

* [Visual Studio Code](https://code.visualstudio.com/Download) 설치.

  설치중 추가 작업 선택의 기타항목을 아래와 같이 모두 체크해야 한다.

  ![image-20191218002645728](C:\Users\LEO\AppData\Roaming\Typora\typora-user-images\image-20191218002645728.png)

* [typora](typora.io) 설치 : Typora는 마크다운(일반 텍스트 문서의 양식을 편집)프로그램으로 사용이 편리하며 쉽게 HTML과 PDF등 다른 문서형태로 변환 가능하다

## 1. 로컬 저장소 활용하기

### 1. 저장소 초기화

``` bash
$ git init
Initialized empty Git repository in C:/LEO/til/.git/		//초기화 한 주소가 나온다.
(master) $
```

* 저장소(repository)를 초기화 하게 되면, '.git 폴더가 해당 디렉토리에 생성된다.
* bash 창에서는 (master)라고 표기된다.
  * 현재 브랜치가 master라는 것을 의미함.

### 2. add - staging area

> git으로 관리되는 파일들은 Working directory(작업 환경), Staging Area, commit 단계를 거쳐 이력에 저장된다.

~~~ bash
$ git add a.txt # 파일명
$ git add images/ # 폴더명
$ git add . # 현재 디렉토리의 모든 파일 및 폴더
~~~

* add 전 상태

  ~~~ bash
  $ git status
  On branch master
  
  No commits yet
  
  Untracked files:
    (use "git add <file>..." to include in what will be committed)
          git.md
          image/
          markdown.md
  
  nothing added to commit but untracked files present (use "git add" to track)
  ~~~

  

* add 후 상태

  ~~~ bath
  $ git add .
  $ git status
  $ git status
  On branch master
  
  No commits yet
  
  Untracked files:
    (use "git add <file>..." to include in what will be committed)
          git.md
          image/
          markdown.md
          penguin.jpg
  
  
  ~~~

### 3. commit



> 커밋은 코드의 이력을 남기는 과정이다.

~~~ bash
$ git commit -m '커밋 메시지'
[master (root-commit) 13be642] 마크다운 및 git기초 정리
 3 files changed, 102 insertions(+)
 create mode 100644 git.md
 create mode 100644 "image/\353\213\244\354\232\264\353\241\234\353\223\234.jpg"
 create mode 100644 markdown.md
~~~

* 커밋 메시지는 항상 해당 이력에 대한 정보를 담을 수 있도록 작성하는 것이 좋다.
* 일반적인 커밋 메시지를 작성하는 습관을 들이자.
* 특정 파일만 커밋하고 싶으면 git 파일명.확장자 -m '커밋 메시지'를 입력한다.

~~~ bash
$ git log
commit 13be642a93d7deab9e51b841b4a7ff240f688696 (HEAD -> master)
Author: Hae-gun <newchk610gmail.com>
Date:   Mon Dec 16 14:25:53 2019 +0900

    마크다운 및 git기초 정리

~~~

**햣항상 status 명령어를 통해 git의 상태를 확인하자! commit 이후에는 log 명령어를 통해 이력들을 확인하자!**



##### github에서 Create a new repository를 만들고 아래 2줄을 복사해서 git cmd에 넣고 엔터치면 로그인 창이 나오고 로그인을 하면 업로드 된다.

![image-20191216143504098](C:/leo_study/til/image/image-20191216143504098.png)



## 2. 원격 저장소 활용하기

> 원격 저장소(remote repository)를 제공하는 서비스는 다양하게 존재한다.
>
> github를 기준으로 설명한다.

### 0. 준비하기

​	Github에서 저장소(repository) 생성

### 1. 원격 저장소 설정

~~~ bash
$ git remote add origin {github url}
~~~

* {github url} 부분에는 원격 저장소 url을 작성한다.

* 원격 저장소(remote)로 {github url} 을 origin 이라는 이름으로 추가(add)하는 명령어이다.

* 원격 저장소 목록을 보기 위해서는 아래의 명령어를 활용한다.

  ~~~ bash
  $ git remote -v
  origin  https://github.com/ksixtin/TIL.git (fetch)
  origin  https://github.com/ksixtin/TIL.git (push)
  $ git remote remove origin
  ~~~

## 2. push

~~~ bash
$ git push origin master
~~~

* 설정된 원격 저장소(origin)으로 push!

폴더의 내용을 수정 및 삭제, 생성 등을 하게 된다면, add, commit, 명령어를 통해서 이력을 저장하고 push 명령어를 통해 업로드 한다.



####  ※ 순서 : 파일저장> git add . > git commit -m '메세지' > git push origin master

~~~ git순서
git연결계정 확인 - 삭제 - 새로등록

student@M16029 MINGW64 /c/LEO/startbootstrap-resume-gh-pages (master)
$ git remote -v					// 현재 연결계정 확인
origin  https://github.com/ksixtin/leo.github.io.git (fetch)
origin  https://github.com/ksixtin/leo.github.io.git (push)

student@M16029 MINGW64 /c/LEO/startbootstrap-resume-gh-pages (master)
$ git remote remove origin		//현재 연결계정 삭제

student@M16029 MINGW64 /c/LEO/startbootstrap-resume-gh-pages (master)
$ git remote -v	

student@M16029 MINGW64 /c/LEO/startbootstrap-resume-gh-pages (master)
$ git remote add origin https://github.com/ksixtin/ksixtin.github.io.git
//새로운 계정 연결
student@M16029 MINGW64 /c/LEO/startbootstrap-resume-gh-pages (master)
$ git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   index.html

no changes added to commit (use "git add" and/or "git commit -a")

student@M16029 MINGW64 /c/LEO/startbootstrap-resume-gh-pages (master)
$ git add .
warning: LF will be replaced by CRLF in index.html.
The file will have its original line endings in your working directory

student@M16029 MINGW64 /c/LEO/startbootstrap-resume-gh-pages (master)
$ git commit -m 'Update title and name'
[master 577e3ae] Update title and name
 1 file changed, 1 insertion(+), 1 deletion(-)

student@M16029 MINGW64 /c/LEO/startbootstrap-resume-gh-pages (master)
$ git push origin master
Enumerating objects: 100, done.
Counting objects: 100% (100/100), done.
Delta compression using up to 8 threads
Compressing objects: 100% (98/98), done.
Writing objects: 100% (100/100), 2.16 MiB | 1.42 MiB/s, done.
Total 100 (delta 22), reused 0 (delta 0)
remote: Resolving deltas: 100% (22/22), done.
To https://github.com/ksixtin/ksixtin.github.io.git
 * [new branch]      master -> master

student@M16029 MINGW64 /c/LEO/startbootstrap-resume-gh-pages (master)
$ git commit -m 'Update profile photo'
On branch master
Changes not staged for commit:
        modified:   img/profile.jpg

no changes added to commit

student@M16029 MINGW64 /c/LEO/startbootstrap-resume-gh-pages (master)
$ git push origin master
Everything up-to-date

student@M16029 MINGW64 /c/LEO/startbootstrap-resume-gh-pages (master)
$ git add profile.jpg
fatal: pathspec 'profile.jpg' did not match any files

student@M16029 MINGW64 /c/LEO/startbootstrap-resume-gh-pages (master)
$ git commit -am "update profile photo'
> git push origin master
>
> git add .

~~~



집에서 클론해서 사용



![image-20191217132142691](C:/leo_study/til/image/image-20191217132142691.png)

git full origin master로 회사에서 집에서 수정한 내용은 불러들임

#### 주요 명령어

git init : 저장소 생성

#### 로그보기 등

~~~ 
$ git log --oneline
255b282 (HEAD -> master) test.txt				//맨앞 숫자는 해쉬코드
010037b (origin/master, origin/HEAD) 4.멀캠작업
36f6fdf 3.집 작업
968a04d 02멀캠작업
df5d88d 집 - 수정
d516fe0 first commit

~~~

esc + : , 그리고 wq 입력후 엔터

### 충돌 상황

원격저장소의 이력과 로컬 저장소의 이력이 다른 경우에는 아래의 메시지가 발생한다.

~~~ 
$ git push origin master
To https://github.com/ksixtin/database.git
 ! [rejected]        master -> master (fetch first)
error: failed to push some refs to 'https://github.com/ksixtin/database.git'
# 원격저장소의 작업내용(work - commit)과 로컬 내용이 다르다.
hint: Updates were rejected because the remote contains work that you do
hint: not have locally. This is usually caused by another repository pushing
# 원격 저장소 변경사항(changes)을 통합하고 다시 push 해라.
# 예)git pull ...
hint: to the same ref. You may want to first integrate the remote changes
hint: (e.g., 'git pull ...') before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.
~~~

** 이 메시지를 보게 된다면, 로컬에서 git log, 원격저장소(github)의 커밋 이력들을 확인하고 다른 부분을 체크하자!!

~~~ 
$ git pull origin master
~~~

통합 후,

~~~ 
$ git push origin master
~~~

![image-20191217142635186](C:/leo_study/til/image/image-20191217142635186.png)



#### Branch

git branch 새로 만들 브런치명

git branch : 브런치 목록

git checkout 브런치명 : 해당 브런치로 이동