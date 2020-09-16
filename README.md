# GitBasic

git 협업 시 기초적인 정보

#### Step01. 추가 및 삭제의 위험
![gitmode](images/gitmode.png)


#### Step02. git pull 작업 시 conflict 문제
pull = fetch + merge

#### Step03. push와 merge, github를 통한 관리

#### Step04. Head와 history 문제 해결

#### 기본적인 git 명령어

기본 명령어(powerShell)
- ls -al 폴더 리스트 보기 확인
- mkdir "파일명" 폴더 만들기
- cd 경로 / 경로 이동

git bash 실행 후
- git init  = 깃 활성화
- git remote add origin 주소
	origin -> 별칭 // 주소 -> git 주소
- git remote rm 리모트명 
	(git remote 치면 나오는 리모트 리스트 중 특정 리모트삭제)
- git pull origin master : master의 코드 폴더에 다운로드
- git clone 주소 : 코드 가져오기
	pull과 clone의 차이점 pull은 init이 된 상태의 폴더에 git서버에서 최신 코드 받아와 local에 merge
	clone은 폴더 자체를 복사하는 개념

- git status 프로젝트 폴더의 상태를 확인
- git add .  (변경된 파일들을 모두 트래킹)
- git add f1.txt = git이 파일을 추적하도록 명령

- git config --global user.name "~"  
- git config --global user.email "~" // git 로그인(commit 내역)
- git commit -m "message" (인식 할 수 있는 commit, 메모) 
	메세지 입력 안했을 시 i 입력 후 메모 후 :wq 로 나오기

- git push origin 리모트명 (git에 push, master가 메인)


- git branch branch_name 브랜치 생성하기
- git checkout branch_name : 브랜치 선택(이동)하기(로컬)
- git checkout -b branch_name : 브랜치 생성하면서 이동

- git branch -d branch_name 삭제하기
- git push remote_name — delete branch_name : 원격 브랜치 삭제하기 ( git push origin — delete '폴더명' )


- git branch -r 원격 브랜치 목록보기
- git branch -a 로컬 브랜치 목록보기

- git reset --hard (코드 수정내역(push전, commit) 초기화, head초기화

- git pull origin Vue.dev1.01 --allow-unrelated-histories // history내역 상관없이 pull

#### 더 공부하고 싶으신 분
https://git-scm.com/book/ko/v2
https://nvie.com/posts/a-successful-git-branching-model/
