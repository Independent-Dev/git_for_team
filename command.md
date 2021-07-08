* git init
  * 명령어를 실행한 위치에 .git 디렉토리 생성
    * .git = 로컬 저장소(원격 저장소는 github 등). git으로 생성한 버전들의 정보와 원격 저장소 주소 등이 들어있음. 이 디렉토리는 git clone 명령어를 통해서도 생성될 수 있음.

* git config
  * Get and set repository or global options(git help -a 참조)
  * 세 종류의 옵션
    * --local: 현재 git 저장소에만 유효
    * --global: 현재 사용자를 위한 옵션
    * --system: PC 전체 사용자를 위한 옵션
  * 변수 확인: git config [--local | --global | --system] -l\
  * (협업 및 버전 관리를 위한)사용자 등록
    * email: git config --global user.email "user_email"
    * name: git config --global user.name "user_name"
    * github와 연동하기 위해서는 해당 사이트 계정의 email과 name을 등록해야함.

* git status
  * Git 워킹트리의 상태를 보는 명령. 해당 내용을 짧게 요약하여 보려면 끝에 -s 옵션 추가(git status -s)

* git log
  * 기본적으로 HEAD와 관련된 커밋들이 출력
  * git log --oneline: 간단히 커밋 해시와 제목만 보고 싶을 때
  * git log --oneline --graph --decorate: HEAD와 관련된 커밋을 좀 더 자세히 보고 싶을 때
  * git log --oneline --graph --all --decorate: HEAD와 관련된 커밋들을 조금 더 자세히 보고 싶을 때

* git remote add 원격저장소_닉네임 원격저장소_url
  * 원격저장소 주소를 알려주기 위해 쓰는 명령어. 원격저장소_닉네임으로 원격저장소_url의 원격저장소를 추가하라는 의미
  * ex) git remote add origin https://github.com/Independent-Dev/git_for_team.git
    * 닉네임이 중복되지 않게 하여 하나 이상의 원격저장소를 연결할 수 있음.
  * git remote -v: 원격저장소 목록 출력
  * 원격저장소 변경 방법[참조](https://gist.github.com/480/4681b67d2a906db8c6c1321cc678f05f)
    * 1)해당 remote 제거: git remote remove repository_alias
    * 2)remote 다시 추가: git git remote add repository_alias repository_url
   
* git commit --amend
  * 현재 브랜치의 선두에 커밋 덮어쓰기
  * 만약에 스테이지에 올라간 파일이 없다면 메시지만 변경
  * [참조](https://cselabnotes.com/kr/2021/03/31/git-%EB%AA%85%EB%A0%B9%EC%96%B4-git-cherry-pick/)
    * 이미 해당 커밋을 push하여 원격 저장소의 이력을 덮어써야 할 때에는 git push 대신 git push -f 로 강제 push 실행 필요. 

* git cherry-pick commit_hash
  * 다른 브랜치에 있는 커밋을 선택적으로 내 브랜치에 적용시킬 때 사용하는 명령어
  * cherry pick 시 conflict가 생길 경우 아래 두 가지 방식으로 대처 가능
    * git cherry-pick --abort: cherry pick 중단
    * conflict 수정 후 커밋
    * [참조](https://cselabnotes.com/kr/2021/03/31/git-%EB%AA%85%EB%A0%B9%EC%96%B4-git-cherry-pick/)

* git reset (--soft | --mixed(default) | --hard)
  * "HEAD 브랜치를 이동"시키는 명령어, 달리 말하자면 "HEAD는 계속 현재 브랜치를 가리키고 있고, 현재 브랜치가 가리키는 커밋을" 바꾸는 명령(<->checkout 명령어는 HEAD가 가리키는 브랜치를 바꿈)
  * --soft: git이 관리하는 세 트리, 즉 HEAD, index(stage area), working directory 가운데 HEAD만 변경함
  * --mixed: HEAD와 index까지 변경함.
    * 이 명령으로 staging을 취소할 수도 있음. 
  * --hard: working directory까지 변경함. 변경사항을 **완전히** 날려버리기 때문에 굉장히 신중하게 써야함.
    * 단, 만약 해당 커밋이 이미 원격저장소에 push된 상태라면 원격저장소에 push된 commit을 지정하고 해당 commit까지 reset 명령어를 실행하면, 원상복구 가능(reset이 HEAD 브랜치가 가리키는 커밋을 변경하는 명령어임을 기억하자!!) 
  * [참조](https://git-scm.com/book/ko/v2/Git-%EB%8F%84%EA%B5%AC-Reset-%EB%AA%85%ED%99%95%ED%9E%88-%EC%95%8C%EA%B3%A0-%EA%B0%80%EA%B8%B0)
    * git이 관리하는 세 상태, HEAD/index/working tree에 대한 더 깊은 지식이 필요하다.

* git revert
  * 잘못된 커밋을 rollback하는 새로운 커밋을 만드는 명령어, reset보다 더 안전하며, push를 한 상황에서 코드 작업을 초기화할 수 있게 해줌.