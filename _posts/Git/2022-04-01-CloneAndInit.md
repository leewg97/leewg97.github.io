---
title:  "[Git] Clone & Init" 
excerpt: "Git Clone & Init"

categories:
  - Git
tags:
  - [Git, Github]

toc: true
toc_sticky: true

date: 2022-04-01
last_modified_at: 2022-04-01
---

## Colne(복제)

<br>
git clone 주소 (github상의 repositories 주소)

git status : git에서 상태확인

  - ex)  changes not staged for commit : staging area에 놀려두지 않은 변경사항이 있다. → add command 이용

staging area에 올리는 법 : git add 파일이름 

“origin”이라는  remote repo 자동 등록 됨

git remote : origin 으로 출력

git remote -v : detail한 주소

<br>

### Commit

- 제목이 가장 중요하다

내용에는 정해진 양식이 없다. (문장형식도 괜찮고 보고서 형식도 괜찮다)

Commit을 설명하는 내용이어야 하며 가독성이 좋아야 한다. ex)띄어쓰기, 대소문자 확인

완료된 후 git status로 확인 

- 작업단위 분리의 이유를 이해할 것.
    - 나는 작업 내용을 어떤 단위로 잘라서 commit할 것인가.
    - But, 동작하는 단위여야 함. 즉, 의미 단위로 잘라내야 한다.
<br><br>
- message상태에서는 제목이 가장 중요하다.(50자 이내)
    - git commit -m “전달하고자 하는 메세지”
        - → -m은 commit message option
    
    ### ★**Prefix**★
    
    | feat | features | 기능개발,구현 관련 |
    | --- | --- | --- |
    | docs | documentations | 문서작업 관련 |
    | conf | configurations | 환경설정 관련 |
    | test | test | test 관련 |
    | fix | bug-fix | 기능에 대해 malfunction / 오타수정. |
    | refactor | refactoring | 일어나는 code에 대해 수정 / 잘 돌아가는 코드를 enhancement 시키는 것(기능 향상 했을 때) |
    | ci | Continuous Integration | Continuous Integration 관련(시간 save해줌) |
    | build | Build | 빌드 관련 |
    

<br><br>

## Git init

<br>
- Clone과 반대 방향
    - git init → local 시작 → remote 끌어올리기
    - 선언 필요함. 위치 잘 확인해야 함.
        - 선언 취소 방법 : .git 제거
- git init을 함으로써 staging area, localrepo를 만드는 것. But,  remote repo는 만들지 않음 → github, gitbucket과 같은 곳 연결

- remote repo 추가
    - git remote add <이름> <주소>
- Branch
    - 일종의 독립적인 작업 공간
    - 최초 git 초기화시 기본적으로 “master”라는 branch 생성됨.(main branch)
    - branch 이름 변경 : ex) master → main : git branch -M main
    - git push -u <remote name> <branch name>
<br><br>

**Clone과 Git init차이**

1. Clone : remote에 있는 것을 복제해서 가져오는 것. 복제를 했기에 상태가 같음.
2. Git init : 생김새와 이름은 똑같지만 서로 연결성이 없음. 서로를 연결해주기 위해서 “-u”를 사용.