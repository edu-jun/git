git submodule
=

이번에 다룰 내용은 git submodule 에 관련된 내용입니다.  

git 저장소 내부에 외부 저장소를 submodule 명령어를 통해서 넣읗 수 있다.  
간단하게 submodule 활용하는 방법에 대해서 알아본다. 

외부 저장소를 추가하고 싶은 레포로 들어간다.
``` bash
$ git submodule add 외부-레포-주소 이름
# 외부-레포-주소 에 본인이 추가하고자하는 레포 주소를 넣는다. 
# 이름에 해당 레포가 들어갈 폴더의 이름을 설정해준다. 
# ex) git submodule add https://github.com/lee-sj/gittest.git sungjunrepo
```

위의 방식으로 레포를 넣고 status 를 확인해보면  

``` bash
$ git status
On branch master
Your branch is up-to-date with 'origin/master'.
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

    new file:   .gitmodules # 서브 모듈을 관리하기위한 파일이 생성된다. 
    new file:   sungjunrepo # 본인이 작성한 이름의 폴더가 생성되고 추가한 레포가 해당 폴더안에 있다. 

$ git diff --cached sungjunrepo/ # 해당명령어로 subproject 의 커밋을 추적중인것을 확인할 수 있다. 
diff --git a/sungjunrepo b/sungjunrepo
new file mode 160000
index xxxxxxxxx
--- /dev/null
+++ b/sungjunrepo
@@ -0,0 +1 @@
+Subproject commit xxxxxxxxx

```
이후 추가된 내용을 commit 명령어로 커밋을 해준다.  
그리고 내부의 repo 로 들어가서 새로운 커밋을 생성해본다.  
다시 밖으로 나와서 status를 확인해본다. 

``` bash
$ git status
On branch master
Your branch is ahead of 'origin/master' by 1 commit.
  (use "git push" to publish your local commits)
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

    modified:   sungjunrepo (new commits)

no changes added to commit (use "git add" and/or "git commit -a")
# 이전처럼 diff 로 추적을 해보자 
$ git diff
diff --git a/sungjunrepo b/sungjunrepo
index xxxxxxxxx 160000
--- a/sungjunrepo
+++ b/sungjunrepo
@@ -1 +1 @@
-Subproject commit xxxxxxxxx
+Subproject commit yyyyyyyyy
```
diff 까지 확인해보면, 서브 모듈에 새로운 커밋이 생겼음을 알려준다. 

바깥의 레포와 안쪽에 들어간 레포가 다른사람이 관리하거나 같은 로컬에 있지 않을경우  
바깥의 레포에서는 submodule 위치로 들어가서 git pull 을 진행한후 바깥의 repo 위치로 들어와서 변경사항을 저장하고, remote 저장소로 push 할수 있다. 



[이전으로](git_5.md)  

[README.md 로 이동](README.md)  