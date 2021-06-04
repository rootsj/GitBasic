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

- pull = fetch + merge

- push와 merge, github를 통한 관리

Step02.master를 mater의 개념으로 pull 진행 후
Step02.another로 pull request 진행하여 확인

나만의 branch를 생성 및 remote를만들어서 수정 후
merge가 된 Step02.master를 pull로 당겨 merge가 생기는지
이클립스, vsc 등 충돌 관리 후 

add 및 commit 후 push 가능


더 쉽게 해결하기 위한 추가 개념 단어) 
- git reset (soft와 hard개념 등)
- git stash (stash 활용 및 이용/ 알면 step03도 해결 가능)
https://wit.nts-corp.com/2014/03/25/1153

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

- git log   깃 로그내역 확인
- git reflog   깃 샐행 후 로그 내역만 확인   
- git log --graph  햣 로그 선 그래프로 확인

- git reset --hard (코드 수정내역(push전, commit) 초기화, head초기화
- git reset --hard origin/name 특정시점 헤드로 이동

- git pull origin origin name --allow-unrelated-histories // history내역 상관없이 pull

- git checkout --ours -- file1.txt # file1 에 대해 우리의 (ours - merge 를 실행하고 있는 브랜치) 버전을 사용하고, 그들의 (theirs - merge 의 대상이 되는 브랜치) 변경사항은 무효화
- git checkout --theirs -- file2.txt # file2 에 대해 그들의 (theirs) 버전을 사용하고, 우리의 (ours) 변경사항은 무효화

- git merge -X <ours/theirs> 

#### 더 공부하고 싶으신 분
오픈소스 참여를 위한 Git_Git 기본실습.pdf !참고! <br>
https://git-scm.com/book/ko/v2 <br>
https://nvie.com/posts/a-successful-git-branching-model/ <br>
https://parksb.github.io/article/28.html


# 커밋(commit) 단위  
커밋은 최종 목표를 달성하기 위한 이정표  
초보자가 가장 많이 하는 잘못된 습관 중 하나는 한꺼번에 모든 파일과 코드를 커밋하는 것  
작은 단계로 커밋하여 코드 개발 과정을 가시적으로 보여줘야 함  

ex) method, class 추가할 때마다 커밋. 실험이나 성능 튜닝을 할 때도 각 단계별로 커밋. 소스 코드 변경 내역이 없을 때는 커밋하지 않는다.

### commit -m "내용" 약식 사용 X
------
#### 제목
feat: 새로운 기능 / a new feature  
fix: 버그 수정 / a bug fix  
docs: 문서 수정 / changes to documentation  
style: 코드 포맷 변경, 세미 콜론 누락, 코드 수정이 없는 경우  
&nbsp;&nbsp; formatting, missing semi colons, etc; no code change  

refactor: 프로덕션 코드 리팩터링  
&nbsp;&nbsp; refactoring production code  

test: 테스트 추가, 테스트 리팩터링 (프로덕션 코드 변경 없음)   
&nbsp;&nbsp; adding tests, refactoring test; no production code change  

chore: 빌드 테스크 업데이트, 패키지 매니저 설정할 경우 (프로덕션 코드 변경 없음)  
&nbsp;&nbsp; updating build tasks, package manager configs, etc; no production code change  


#### 본문 (선택)  
본문은 커밋의 상세 내용을 작성한다.   
제목과 본문 사이에 한 줄 비운다.  본문은 한 줄에 72자 이내로 작성한다.  
한 줄을 띄워 문단으로 나누거나 불렛을 사용해 내용을 구분한다.  

#### 꼬리말 (선택)    
꼬리말에는 이슈 트래커 ID를 추가한다.  
(Resolves: #123, Issue: #123)  
resolves 사용 시 master에 병합되면 issue close 됨  
issue는 유지 됨   

ex)  
-----
> feat: login face emotion recognition
>
>\- 얼굴 감정 인식 기능 추가  
>\- 로그인 기능  
>
>Resolves: #123  
>See also: #456, #789
-----

# Issue 작성 법
Reviewers : 봐야할 사람  

Assignees : 해당 작업의 담당자  

Labels: 해당 작업의 성격    
- bug, question 등
Milestone: 해당 작업이 속한 파트  
- main page, login method, face recognition 등 
Epics: 같은 issue들의 묶음
