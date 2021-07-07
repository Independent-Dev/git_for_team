* terms
  * branch: 특정 커밋을 가리키고 있는 포인터(물리적이거나 특정 커밋에서 독립적인 요소가 아님!!).능
    * 별도의 브랜치를 만들지 않은 상태에서 하나의 커밋을 바탕으로 둘 이상의 커밋을 생성 후 원격 저장소에 push 하려 하면, 첫 커밋은 정상적으로 push 되지만 두 번째 커밋에서는 아래와 같은 메시지와 함께 에러 발생
      * Updates were rejected because the remote contains work that you do not have locally. This is usually caused by another repository pushing to the same ref. You may want to first integrate the remote changes (e.g., 'git pull ...') before pushing again. 
  * HEAD: git의 현재 상태를 보여주는 포인터. 일반적으로 특정 브랜치를 지시하고 있지만, 그렇지 않고 다른 커밋을 가리키고 있을 수도 있음.
    * cat .git/HEAD를 통해 HEAD의 정보 확인 가능
    * [더 많은 정보](https://stackoverflow.com/questions/2304087/what-is-head-in-git)
* component / element
  * .git
* action
  * add
  * commit
  * checkout
    * 'In Git terms, a "checkout" is the act of switching between different versions of a target entity. The git checkout command operates upon three distinct entities: files, commits, and branches.'([출처](https://www.atlassian.com/git/tutorials/using-branches/git-checkout))
      * HEAD를 특정 커밋에서 다른 커밋(또는 다른 커밋을 가리키는 브랜치)으로 옮기는 것
  * merge
  * pull
  * rebase: 머지와 마찬가지로 재배치하고(새로운 베이스로 삼고) 싶은 커밋 또는 브랜치에 명령을 실행해야함.
    * [더 많은 정보](https://www.atlassian.com/git/tutorials/merging-vs-rebasing)
* file status // 내용 보완 필요
  * 1)untracked: 새로 만들어진 이후 (아직 add 되지 않아) git이 관리하고 있지 않은 상태.
  * tracked
    * 2)staged: add 명령어를 통해 stage(index)에 올라간 상태.
    * 3)unmodified: add된 파일이 commit 된 상태. 수정은 할 수 있으나 이 상태로 다시 stage에 올릴 수는 없음.
    * 4)modified: unmodified 상태의 파일을 수정한 상태.