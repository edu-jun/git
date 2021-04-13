git_git_git
===

git 내용 보충을 위한, 명령어 및 개념 모아서 정리해두기.  

``` bash

$ git commit --allow-empty -m "commit message"

$ git remote remove origin  # remove remote repo

$ git remote -v # view remote repo

$ git remote set-url origin REPOSITORY # change remote url

#서브모듈 삭제 3단계 절차 
$ git submodule deinit -f REPO-NAME # REPO-NAME 으로 등록된 서브 모둘을 deinit 함
$ rf -rf .git/modules/REPO-NAME # 모듈 삭제
$ git rm -rf REPO-NAME # 레포 삭제

$ git submodule update -recursive # 모든 서브모듈에 대해 참조중인 상태로의 checkout 을 수행함

$ git submodule foreach git pull REMOTE BRANCH # 각 서브모듈의 REMOTE이름으로 지정된 리모트의 BRANCH를 최신 상태로 업데이트한다. 

$ git submodule update --remote REPO-NAME # 특정 서브모듈만 최신상태로 업데이트한다. 

```