* git init
  * 명령어를 실행한 위치에 .git 디렉토리 생성
    * .git = 로컬 저장소(원격 저장소는 github 등). git으로 생성한 버전들의 정보와 원격 저장소 주소 등이 들어있음. 이 디렉토리는 git clone 명령어를 통해서도 생성될 수 있음.
* git config
  * Get and set repository or global options(git help -a 참조)
  * 변수 확인
    * global: git config --global -l
    * local: git config --local -l
  * (협업 및 버전 관리를 위한)사용자 등록
    * email: git config --global user.email "user_email"
    * name: git config --global user.name "user_name"
    * github와 연동하기 위해서는 해당 사이트 계정의 email과 name을 등록해야함.
* git remote add 원격저장소_닉네임 원격저장소_url
  * 원격저장소 주소를 알려주기 위해 쓰는 명령어. 원격저장소_닉네임으로 원격저장소_url의 원격저장소를 추가하라는 의미
  * ex) git remote add origin https://github.com/Independent-Dev/git_for_team.git
    * 닉네임이 중복되지 않게 하여 하나 이상의 원격저장소를 연결할 수 있음. 