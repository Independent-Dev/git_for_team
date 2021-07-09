* terms
  * branch: 특정 커밋을 가리키고 있는 포인터(물리적이거나 특정 커밋에서 독립적인 요소가 아님!!).능
    * 별도의 브랜치를 만들지 않은 상태에서 하나의 커밋을 바탕으로 둘 이상의 커밋을 생성 후 원격 저장소에 push 하려 하면, 첫 커밋은 정상적으로 push 되지만 두 번째 커밋에서는 아래와 같은 메시지와 함께 에러 발생
      * Updates were rejected because the remote contains work that you do not have locally. This is usually caused by another repository pushing to the same ref. You may want to first integrate the remote changes (e.g., 'git pull ...') before pushing again. 
  * HEAD: git의 현재 상태를 보여주는 포인터. 일반적으로 특정 브랜치를 지시하고 있지만, 그렇지 않고 다른 커밋을 가리키고 있을 수도 있음.
    * cat .git/HEAD를 통해 HEAD의 정보 확인 가능([더 많은 정보](https://stackoverflow.com/questions/2304087/what-is-head-in-git))
    * Detached HEAD: HEAD가 어느 branch도 가리키고 있지 않은 커밋에 위치하여 branch로부터 Detached된 상황. 이 상황에서도 commit을 생성할 수는 있지만, 다른 브랜치로 생성한 순간 Detached HEAD에서 생성한 커밋은 다 사라져 (로그에서) 보이지 않게 됨.
  * upstream: 로컬저장소와 연결된 원격저장소를 일컫는 단어
  * checksum: 일종의 UUID
    * 종류
      * 파일: 내용이 같은 파일은 체크섬도 동일함
      * 트리
      * 커밋
* component / element
  * .git: git init 명령으로 생성되는 폴더. 커밋, 커밋을 구성하는 객체, 스테이지가 모두 이 폴더에 저장됨.
  * working tree: "일반적으로 사용자가 파일과 하위 폴더를 만들고 작업 결과물을 저장하는 곳. 작업 폴더에서 .git을 제외한 나머지 부분. 

* action
  * add
  * commit
  * checkout
    * 'In Git terms, a "checkout" is the act of switching between different versions of a target entity. The git checkout command operates upon three distinct entities: files, commits, and branches.'([출처](https://www.atlassian.com/git/tutorials/using-branches/git-checkout))
      * HEAD를 특정 커밋에서 다른 커밋(또는 다른 커밋을 가리키는 브랜치)으로 옮기는 것
  * merge
  * pull
  * rebase: 머지와 마찬가지로 재배치하고(새로운 베이스로 삼고) 싶은 커밋 또는 브랜치에 명령을 실행해야함. 주로 로컬 브랜치를 깔끔하게 정리하고 싶을 때 사용함. 
    * 단 conflict가 발생/이것을 해결한 경우 merge는 commit을 해야 하지만, rebase는 rebase -- continue를 찍어주어야 함.
      * 이 rebase --continue를 하게 되면 rebase되는 커밋은 원래 커밋과 다른 커밋이 됨.(체크섬이 변함)
    * rebase는 이력을 깔끔하게 정리할 수 있다는 장점과 여러 차례에 걸처 conflict가 발생할 수 있다는 단점을 함께 가지고 있음. 
    * [더 많은 정보](https://www.atlassian.com/git/tutorials/merging-vs-rebasing)
    * 꾸준히 연습해보기(270page) 

* file status // 내용 보완 필요
  * 1)untracked: 새로 만들어진 이후 (아직 add 되지 않아) git이 관리하고 있지 않은 상태.
  * tracked
    * 2)staged: add 명령어를 통해 stage(index)에 올라간 상태.
    * 3)unmodified: add된 파일이 commit 된 상태. 수정은 할 수 있으나 이 상태로 다시 stage에 올릴 수는 없음.
    * 4)modified: unmodified 상태의 파일을 수정한 상태.