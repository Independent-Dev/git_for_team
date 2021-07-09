* unsolved
  * github repository의 이름을 바꿀 수 있나? 바꿀 때 로컬 저장소에 해야 하는 액션이 있나
  * global option과 local option의 차이는??
  * git conflict가 난 상황에서 git 또는 conflict가 난 파일의 상태는 무엇인가?? 
    * git status를 실행해보면 아래와 같이 나옴
      * You have unmerged paths.
      * Unmerged paths:
        * both modified: test.txt
    * 일종의 merging 상태라고 할 수 있는 것인가??
      * git merge --abort를 하면 이 상태가 풀림
  * 각 명령어의 option을 아는 방법은??
  * "git add 명령은 워킹트리의 내용을 스테이지에 반영하는 것이고 git commit 명령은 스테이지의 내용을 가지고 트리 객체를 만들고 이 트리 객체를 기반으로 기존 HEAD 커밋을 부모로 하는 새로운 커밋을 만듭니다. 마지막으로 생성된 커밋은 다시 HEAD가 됩니다."(<팀 개발을 위한 git/github 시작하기> 295page)
    * 여기서 트리 객체는 구체적으로 어떻게 구성되어 있는 것인가. 그냥 문자 그대로 tree 자료구조여서 "트리 객체"라고 하는 것인가??
  * git 내부에서 파일들이 어떻게 관리되는 것인지, 각 폴더와 파일이 어떤 역할을 하는 것인 좀 더 구체적으로 알고 싶다...지
  * git reset을 하면 커밋을 기준으로 stage와 working tree가 변경된다는 것...
  
* solved
  * 