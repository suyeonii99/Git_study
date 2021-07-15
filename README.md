# Git_study
Git 공부용 📝

📍git 기초 (mac os 내장 terminal or vsc terminal)
  ! git 명령어 -> 프로젝트 디렉토리 내부에서 실행.

✅ git 시작하기.
* git init: 프로젝트 파일을 git으로 버전관리를 할 수 있는 상태가 되도록 하는 명령어.
  > 프로젝트 디렉토리 안에 .git (직접 건드리지 않으므로 숨김 파일 처리) 폴더가 생성되어 버전 관리하기 위해 필요한 것 자동 저장.
* git config user.name “이름”: git 사용자 이름 설정.
* git config user.email “이메일”: git 사용자 이메일 설정.
   > 같은 컴퓨터라도 다른 디렉토리일 경우 유저 이름, 이메일 재설정 가능.

✅ 특정 버전을 저장 = 커밋(commit)
- working directory: 실제로 다루는 프로젝트 디렉토리
- staging area: 특정 버전으로 관리하고 싶은 파일을 모아두는 장소 (지금 당장 commit 을 남기고 싶지 않은 파일이 존재할 수 있기 때문.)
- repository: 특정 시점의 staging area 모습을 커밋(commit)으로 남기면 커밋(commit)들로 저장되는 영역
  > commit 과정: 현재 작업 중인 working directory에서 commit을 하고 싶은 모든 파일을 staging area 파일에 올린 후
                commit 명령어를 실행하면 해당 시점의 staging area에 존재하던 파일이 commit 단위로 repository에 순차적으로 저장되어 버전관리를 할 수 있게 됨.

✅ commit 하는 이유? 작업 이력을 남겨두고 원하는 시점으로 자유롭게 이동하기 위함.

✅ git commit하기.
* git add 파일명(확장자까지 ex) .js 등): 지정한 파일명의 프로젝트 파일을 staging area에 올리는 명령어.
* git add . : 새롭게 만들어지거나 수정된 파일을 모두 staging area에 올리는 명령어.
* git commit -m “커밋메세지”: 현재 staging area 에 올라간 파일들을 하나의 commit으로 만들어 repository에 저장하는 명령어.
  * git diff {commit1_id} {commit2_id}: 커밋 사이의 차이점을 보여주는 명령어 (보통 commit id 는 앞 네자리만 따옴.)
    > 수정된 부분만 반영하여 보여줌, 수정되지 않은 (staging area에 올라가지 않은) 부분은 반영 X.

  * git reset —{option} {commit_id or HEAD@{숫자}(reflog에서 기록된 표기법)}: Head 가 가리키는 commit을 바꾸는 명령어. (공통)
    - option이 hard 일 경우: working directory 모습이 변경됨(코드 변경).
      > 직전 commit 들을 날려도 괜찮을 때 주의하여 사용
    - option이 mixed 일 경우: working directory 모습이 변경되지 않음. / staging area 는 현재 가리키는 commit 으로 변경됨.
    - option이 soft 일 경우: working directory 모습이 변경되지 않음. / staging area도 건드리지 않음.


✅ 작업 상태, 기록 확인
* git status: commit에 변경 사항이 있는지 확인하는 명령어.
* git status: commit에 변경 사항이 있는지 확인하는 명령어.
* git log / git history: commit의 기록을 시간 순으로 보여주는 명령어.
* git reflog: head 가 한번이라도 가리켰던 commit 기록을 모두 보여주는 명령어.
  > head@{숫자}의 숫자가 작을수록 최근 commit임.


✅외부 저장소(gitHub, gitlab 등) 저장시 장점
1. 프로젝트 복구 가능
2. 협업과 동시에 버전 관리 가능.

✅ 외부 저장소에 저장하여 작업하기
* git remote add origin {gitlab_url(gitlab(github) 페이지의 clone에서 링크 가져오기)}
  : git remote는 내 컴퓨터에서 외부 저장소 작업을 할 경우 사용하는 명령어로 url이 가리키는 외부 서버 프로젝트를 원격 저장소로 지정하고 그 이름을 origin으로 함.
    즉, 원격 저장소(gitlab_url)을 추후 이용하기 쉽도록 origin으로 지정.
* git push -u origin master: 현재 프로젝트 내용을 origin이 가리키는 원격 저장소에 올리는 명령어.
  > .git 디렉토리 내부에서 관리되던 repository 영역을 업로드 한 것.
  > 이전에 git push -u origin master 명령어를 작성한 기록이 있으면 이미 origin이 가리키는 원격 저장소를 알기 때문에 git push 만 작성해도 ok.
* README.md 파일: 해당 프로젝트에 대한 설명을 담고있는 파일.
* git clone {프로젝트_url}: url이 가리키는 원격 저장소의 프로젝트를 디렉토리 형태로 가져옴.
  > 제일 처음 상대가 gitlab에 올린 프로젝트의 commit을 내 컴퓨터에 가져오는 명령어.
  > clone을 한 경우에는 원격 저장소를 가져 온 것이므로 remote 명령어로 원격 저장소 지정 필요 없음.
* git pull: gitlab 서버 상의 최신 commit이 생겼을 경우 내 컴퓨터로 가져오는 명령어.
  > gitlab history 상의 commit 들이 서로 다를 경우 충돌이 일어나므로 반드시 최신 commit이 모두 반영되었는지 확인 후 pull.


📍 git 심화

✅ 실무 프로젝트 진행 방식
❗️ fork: 프로젝트의 완성도를 위해 원본 프로젝트 아래에 개인 개발자의 프로젝트 copied(복제)본 생성.
     > git clone 하여 내 컴퓨터에 깃랩 서버를 가져옴.
     > 작업(commit)하여 git push 하면 원본 프로젝트가 아닌 copied 프로젝트에 올라감.
     > 이후 깃랩에서 나의 복제본 프로젝트에서 원본 프로젝트로 merge request를 보냄 (새로운 작업 확인 후 반영을 위함.)
     > merge request 에 대한 글을 남기고 싶다면 discussion을 통해 글 남기기.
❗️ branch : 특정 커밋을 가리키는 포인터 > 하나 이상의 개발 흐름을 생성하기 위해 브랜치 사용. > master: git 사용시 기본 설정되는 브랜치, 실제 서비스 배포를 목적으로 완성된 커밋만 둠.

  HEAD -> master (헤드는 브랜치를 통해 커밋을 가리킴.)
  origin/master(gitlab 서버의 master 브랜치를 가리킴.)

* git branch {브랜치명}: 브랜치 생성 명령어.
* git checkout {브랜치명}: HEAD가 가리키고자 하는 브랜치를 지정하는 명령어.
* git log --all --graph: HEAD가 가리키는 branch 뿐만 아니라 모든 branch에 대한 commit 기록을 그래프 형식으로 보여주는 명령어.

✅ 협업시 중요한 명령어: (merge)
* Head 가 가리킬 브랜치로 이동 (git checkout {브랜치명})
* git merge {합칠 브랜치명}: 현재 head가 가리키는 브랜치에 합칠 브랜치의 모든 작업을 합히는 명령어.
  - 흐름의 분기가 없을 경우: Fast-forward merge: 새로운 커밋을 만들지 않고 브랜치가 당겨져 옮.
  - 흐름의 분기가 있을 경우: 새로운 merge commit을 만듦.


* Git push -u origin master: master branch를 origin이 의미하는 깃랩 서버의 프로젝트에 올리는 명령어. > -u 옵션 (= —set-upstream): 내 컴퓨터의 master 브랜치가 깃랩 서버의 master 브랜치를 바라보게 하는 명령어.   > 이후에는 작성할 필요 X
* Git push —force: 업로드를 강제함.
