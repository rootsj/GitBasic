# GitBasic

git 협업 시 기초적인 정보

#### Step01. 추가 및 삭제의 위험

Step01.master를 기준으로
Step01.another와 Step01.mine이 동시에 작업을 한다.

Step01.another가 실수로 3번 파일을 master에 merge 하였고
Step01.mine이 삭제된 내용을 인지하지 못했을 경우

Step01.master를 pull로 당겼을 시
3번 파일이 날아간다.

---
branch에서 pull로 작업 시 (branch와 branch 이동이라) merge가 일어나나 <br>
master에서는 merge를 인지하지 못하고 바로 변경점이 적용된다

---
파일 추가시 경고를 안하듯이 <br>
삭제도 경고를 안함

master에 직접 pull과 push를 이용 시 파일 관리의 어려움이 상승함 <br>
참고 - https://m.blog.naver.com/PostView.nhn?blogId=mug896&logNo=140191101787&proxyReferer=https:%2F%2Fwww.google.com%2F
![gitmodel](images/gitmodel.png)


#### Step02. git pull 작업 시 conflict 문제
Step02.master를 mater의 개념으로 pull 진행 후
Step02.another로 pull request 진행하여 확인

나만의 branch를 생성 및 remote를만들어서 수정 후
merge가 된 Step02.master를 pull로 당겨 merge가 어떻게 

- pull = fetch + merge

- push와 merge, github를 통한 관리

#### Step03. Head와 history 문제 해결

- 문제 발생 경우
Step02.master의 code를 다운 받고
git init 후 git pull origin master 진행

1. 자잘한 폴더 변경
src를 Step03으로 윈도우에서 수정 및 정리 (master branch에서 진행)

2. 원래내가쓰는 romote branch로 branch를 관리하려고 했는데 master에서 진행한 것을 확인

3. git checkout -b origin name 후 remote branch와 헤드를 연결하기 위해 pull을 당겼으나 불가능

4. git pull origin origin name --allow-unrelated-histories 로 해결 가능

5. 그후 커밋 및 git push -f origin name 으로 진행 가능

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
- git reset --hard origin/name 특정시점 헤드로 이동

- git pull origin origin name --allow-unrelated-histories // history내역 상관없이 pull

#### 더 공부하고 싶으신 분
오픈소스 참여를 위한 Git_Git 기본실습.pdf !참고! <br>
https://git-scm.com/book/ko/v2 <br>
https://nvie.com/posts/a-successful-git-branching-model/ <br>
https://parksb.github.io/article/28.html
