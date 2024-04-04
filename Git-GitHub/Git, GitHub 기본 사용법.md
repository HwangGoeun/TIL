# Git, GitHub 기본 사용법

[제대로 파는 Git & GitHub - 깃 끝.장.내.기](https://www.youtube.com/watch?v=1I3hMwQU6GU) 강의 정리본

<br>

## 1. Git 최초 설정
### 1-1. Git 전역으로 사용자 이름과 이메일 주소를 설정
누가 어떤 것을 깃에 올렸고, 연락은 어디로 해야 하는지 등을 확인하기 위한 등록이 필요하다.
- GitHub 계정과는 별개
- 설정을 하지 않을 때 제한되는 기능이 있을 수 있으므로 설정해야 한다.

<br>

터미널 프로그램에서 아래 명령어 실행
``` bash
git config --global user.name "(본인 이름)"
```
``` bash
git config --global user.email "(본인 이메일)"
```
아래의 명령어들로 설정한 값을 확인할 수 있다.
``` bash
git config --global user.name
```
``` bash
git config --global user.email
```
<br>

### 1-2. 기존 브랜치명 변경
옛날에는 깃의 주브랜치 이름이 `master`였으나, 현재는 `main`이라는 이름으로 바뀌어 브랜치명의 변경이 필요하다.
``` bash
git config --global init.defaultBranch main
```
<br>
<br>

---

<br>
<br>

## 2. 프로젝트 생성 & Git 관리 시작
### 2-1. git init : 버전 관리 시작하기
내가 Git으로 관리하고 싶은 폴더 경로에 들어가 `git init` 명령어를 입력하면, `.git`이라는 숨겨진 폴더가 생성되며 버전 관리를 시작할 수 있다.
- `.git` 폴더를 통해 버전 관리가 진행되므로, `.git` 폴더를 삭제하면 Git 관리내역이 삭제된다.
``` bash
git init
```

<br>

### 2-2. git status : 변경 사항 확인하기
Git에서 버전 관리를 하고 있는 폴더 내에서 변경 사항이 발생했을 때, `git status` 명령어를 통해 변경사항을 확인할 수 있다.
``` bash
git status
```

<br>
<br>

---

<br>
<br>

## 3. Git ignore : Git의 관리에서 특정 파일/폴더 배제하기
Git에서 변경 사항을 저장하고 싶지 않을 파일/폴더를 지정할 때는 `.gitignore` 파일을 생성하고 파일 안에 정보를 입력하면 된다.

### .gitignore 형식
```
# 이렇게 #를 사용해서 주석

# 모든 file.c
file.c

# 최상위 폴더의 file.c
/file.c

# 모든 .c 확장자 파일
*.c

# .c 확장자지만 무시하지 않을 파일
!not_ignore_this.c

# logs란 이름의 파일 또는 폴더와 그 내용들
logs

# logs란 이름의 폴더와 그 내용들
logs/

# logs 폴더 바로 안의 debug.log와 .c 파일들
logs/debug.log
logs/*.c

# logs 폴더 바로 안, 또는 그 안의 다른 폴더(들) 안의 debug.log
logs/**/debug.log
```

<br>
<br>

---

<br>
<br>

## 4. 변경사항 저장하기
### 4-1. 변경사항 저장하기
Git에서 관리하는 폴더 내에서 변경 사항을 저장할 때는 [커밋](#4-2-변경사항-커밋하기)을 해주어야 한다. 이때, `commit` 할 대상 폴더, 파일을 지정해주기 위해서 `git add`를 사용한다.
- `git add`를 한 파일, 폴더는 `commit`의 대상이 된다.
``` bash
# 파일 하나만 add 할 때
git add (파일명)

# 변경 사항 전체를 add 할 때
git add .
```

### 4-1-1. add 되돌리기
이미 add를 했더라도 `rm --cached` 명령어를 통해 add를 안 한 상태로 돌아갈 수 있다.
``` bash
git rm --cached (파일명)
```

<br>

### 4-2. 변경사항 커밋하기
`Commit`이란 변경사항을 Git에 저장하는 단계이다.

- 커밋 메시지 작성과 함께 `commit`하기
``` bash
# git add를 한 다음
git commit -m "(커밋 메시지)"
```
- `add`와 `commit` 한꺼번에 하기
- 새로 추가된(untracked) 파일이 없을 때 한정으로 사용이 가능하다.
``` bash
git commit -am "(커밋 메시지)"
```

<br>

### 4-3. 커밋 내역 확인하기
`git log` 명령어를 입력하면 그동안의 커밋 내역을 확인할 수 있다.
``` bash
git log
```

<br>
<br>

---

<br>
<br>

## 5. 커밋 과거 기록으로 돌아가기
Git에는 과거로 돌아갈 수 있는 두 가지 방법이 있다.
1. [reset](#5-1-reset--원하는-시점으로-돌아간-뒤-이후-내역-삭제하기) : 원하는 시점으로 돌아간 뒤 이후 내역 삭제
2. [revert](#5-2-revert--원하는-시점의-커밋을-거꾸로-실행) : 되돌리기 원하는 시점의 커밋을 거꾸로 실행
### 5-1. reset : 원하는 시점으로 돌아간 뒤 이후 내역 삭제하기
`git reset` 명령어를 사용하면 원하는 커밋 시점으로 돌아갈 수 있으며, 이후 내역은 삭제된다.
- **해시정보** : `git log`를 입력했을 때 `commit` 글씨 옆에 나오는 영어+숫자의 조합
``` bash
git reset (옵션) (해시정보)
# ex) git reset --hard a123...
```

<br>

### 5-2. revert : 원하는 시점의 커밋을 거꾸로 실행
`git revert` 명령어를 사용하면 원하는 시점의 커밋의 작업 내역을 거꾸로 실행하게 된다. <br>
ex) 삭제 -> 생성 / 생성 -> 삭제
``` bash
git revert (해시정보)
```

<br>
<br>

---

<br>
<br>

## 6. 브랜치
브랜치란, 새로운 기능을 수정하거나 추가하고 싶을 때 파일을 복사한 뒤 수정하는 것이라고 생각하면 된다.
- 프로젝트를 하나 이상의 모습으로 관리해야 할 때
    - ex) 실배포용, 테스트서버용, 새로운 시도용...
- 여러 작업들이 각각 독립되어 진행될 때
    - ex) 신기능 1, 신기능 2, 코드개선, 긴급수정 등...

모든 기능을 구현한 브랜치는 [merge]() 또는 [rebase]() 후 삭제를 해주어야 히스토리를 깔끔하게 유지할 수 있다.

### 6-1. 브랜치 생성 / 이동 / 삭제
- 브랜치 생성하기
``` bash
git branch (생성할 브랜치 이름)
```
- 브랜치 목록 확인
``` bash
git branch
```
- 브랜치 이동하기
``` bash
git switch (이동할 브랜치 이름)

# 브랜치 생성과 동시에 이동하기
git switch -c (생성하고 이동할 브랜치 이름)
```
- 브랜치 삭제하기
``` bash
git branch -d (삭제할 브랜치명)

# 지워질 브랜치에만 있는 내용의 커밋이 있을 경우 -d 대신 -D로 강제 삭제를 해야 한다.
git branch -D (강제삭제할 브랜치명)
```
- 브랜치 이름 바꾸기
``` bash
git branch -m (기존 브랜치명) (새 브랜치명)
```

<br>

### 6-2. merge :  두 브랜치를 한 커밋에 합치기
merge를 하게 되면 merge를 한 커밋의 히스토리가 남아있게 된다.
- 협업 시에는 히스토리를 참조하는 경우가 많으므로, 대부분 merge를 이용한다.
``` bash
# merge 할 브랜치로 이동한 뒤
git merge (merge 될 브랜치)

# ex) to-merge 브랜치를 main 브랜치와 merge 하고싶을 때,
git switch main
git merge to-merge
```

<br>

### 6-3 rebase : 브랜치를 다른 브랜치로 이동시켜 이어 붙이기
- 한 줄로 깔끔히 정리된 내역을 유지하기 원할 때 적합하다.
- 이미 팀원과 공유된 커밋들에 대해서는 사용하지 않는 것이 좋다.
``` bash
# rebase 되는 브랜치로 이동한 뒤 (merge와 반대)
git rebase (rebase 하는 브랜치)

# ex) to-rebase 브랜치를 main 브랜치와 rebase 하고 싶을 때,
git switch to-rebase
git rebase main
git merge to-rebase
```

<br>

### 6-4 branch 합칠 때 충돌이 발생하는 경우
``` bash
<<<<<<< HEAD
이런 식으로 충돌이 나는 부분이
=======
출력이 된다.
>>>>>>> (충돌난 branch)
```
<br>

- `merge`의 경우에는 수정을 끝낸 뒤
```bash
git add .
git commit
```
을 통해 진행하면 된다.

<br>

- `rebase`의 경우에는 수정을 끝낸 뒤
``` bash
git add .
git rebase --continue
```
를 통해 충돌을 해결한다.

<br>

- 만약 충돌을 해결할 수 없는 경우에는
``` bash
# merge의 경우
git merge --abort

# rebase의 경우
git rebase --abort
```
명령어를 통해 `merge` 또는 `rebase`를 중단한다.

<br>
<br>

---

<br>
<br>

## 7. Github
깃허브를 사용하기 전, 깃과 깃허브의 차이점에 대해 알아야 한다.
- **깃** : 로컬 저장소. 작업하고 있는 디바이스 내에서 버전 관리를 하는 것. (인터넷 깃허브 사이트에 반영 X)
- **깃허브** : 원격 저장소. 인터넷을 통해 버전 관리를 할 수 있게 해주는 것.

이 말인 즉슨, 깃에서 커밋한 내용이 깃허브에 적용이 되지 않을 수 있고, 그 반대의 상황도 가능하다.

<br>

### 7-1. 로컬에 원격 저장소 추가하기
### 1. 깃허브에서 레포지토리를 생성한다.
### 2. 로컬에 원격 저장소(레포지토리)를 추가한다.
#### GitHub 레포지토리 생성 후 복붙 명령어
- 로컬의 Git 저장소에 원격 저장소로의 연결 추가
    - 원격 저장소 이름에 흔히 `origin`을 사용하는데, 이 이름은 변경해도 무관하다.
    ``` bash
    git remote add origin (원격 저장소 주소)
    ```
- 기본 브랜치명 `main`으로 바꾸기
    - GitHub 권장사항이다.
    ``` bash
    git branch -M main
    ```
- 로컬 저장소의 커밋 내역들 원격으로 `push` (업로드)
    ``` bash
    git push -u origin main
    ```
### 3. 원격 목록 확인하기
- `git remote` 명령어를 통해 현재 연결한 원격 저장소의 목록 확인이 가능하다.
    ``` bash
    git remote
    ```

#### 로컬 프로젝트와 원격 연결을 해제하고 싶을 때
- `git remote remove` 명령어를 사용하면 로컬 프로젝트와 원격 연결을 해제할 수 있다.
    - 로컬 프로젝트와의 연결만 없애는 것이므로, GitHub 레포지토리는 지워지지 않는다.
    ``` bash
    git remote remove (원격 이름)
    ```

<br>

### 7-2. GitHub에서 프로젝트 다운받기
깃허브에 저장된 레파지토리를 로컬 저장소에 다운받고 싶을 때 `git clone` 명령어를 사용한다.
- `Download ZIP`을 이용해 다운받는 방법도 있지만, `.git` 폴더가 포함되지 않아 버전 관리가 이루어질 수 없기 때문에 협업을 할 때는 `git clone`을 이용해 진행해야 한다.
``` bash
git clone (원격 저장소 주소)
```

<br>

### 7-3. push : 원격 저장소에 변경 사항 저장하기
깃에서 커밋한 내용을 깃허브에 올리기 위해서는 `push` 명령어를 사용해야 한다.
``` bash
git push
```
- 이미 위에서 `git push -u origin main` 명령어로 대상 원격 브랜치를 지정했기 때문에 `push`만 해도 가능하다.

<br>

### 7-4. pull : 원격 저장소의 변경 사항 가져오기
깃허브에서 변경 사항을 불러오기 위해서는 `git pull` 명령어를 사용해야 한다.
``` bash
git pull
```

<br>

### 7-5. `pull` 할 것이 있을 때 `push`를 해야 하는 경우
- 깃허브에 `push`를 하기 위해서는 내 로컬에 저장된 원격 저장소의 버전이 깃허브의 버전과 동일(=최신 상태가 유지되어야)해야 한다.<br>
    -> 그렇기 때문에 `pull`을 먼저 진행한 뒤 `push`를 진행해야 한다.

이 경우 두 가지 방법으로 `pull`을 할 수 있다.
- `git pull --no-rebase` : **merge** 방식
- `git pull --rebase` : **rebase** 방식

충돌상황 발생 시에는 [6-4](#6-4-branch-합칠-때-충돌이-발생하는-경우)와 같은 방식으로 해결하면 된다.

<br>

### 7-6. 로컬의 내역 강제 `push` 하기
로컬의 히스토리와 원격의 히스토리가 다른 경우가 있는데, 원격의 히스토리를 로컬의 커밋과 일치시킬 때 사용할 수 있다.<br>
- 예) 원격의 커밋은 30개고 로컬의 커밋은 15일 때, 강제로 `push`하게 되면 원격의 커밋은 15개가 된다.
- 협업을 진행하는 경우에는 잘 사용하지 않는다.
``` bash
git push --force
```