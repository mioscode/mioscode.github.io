---
title: "Git 명령어"
categories:
  - Github
tags:
  - Github
comments: true
---
# Create
원하는 작업 폴더 새로 만들고 폴더 안으로 이동해서 새로운 git 저장소 만들기
```
$ cd 작업디렉토리
$ git init
```

# Clone
## (local) 저장소 복제
```
$ git clone /로컬/저장소/경로
```

## (remote) 저장소 복제
```
$ git clone 사용자명@호스트:/원격/저장소/경로
```
# 변경 사항 제거
> 로컬 변경을 수행 할 때 파일 범주는 세 가지
> Type 1. Staged Tracked files : 준비 됨 – 준비 영역으로 이동 / 색인에 추가됨
> Type 2. Unstaged Tracked files : 추적 된 – 수정 된 파일
> Type 3. Unstaged UnTracked files a.k.a UnTracked files : 새 파일. 항상 무대 뒤에서. 준비가되면 추적된다는 의미입니다.

## 무인 추적 파일 만 제거 (Type 2)
### All
```
$ git checkout . 
```
### 특정 파일
```
$ git checkout -- <filename>
```
ex) src/hello.c 의 변경을 취소하는 경우
```
$ git checkout -- src/hello.c
```


## Unstaged UnTracked 파일 만 제거 (Type 3)
```
$ git clean -f 
```

## 단계별 추적 및 비 스테이지 추적 파일을 제거 (Type 1, Type 2)
```
$ git reset --hard
```

## 모든 변경 사항을 제거 (Type 1, Type 2, Type 3)
모든 수정 사항을 버리므로 주의
```
$ git stash -u
```

# Commit
## 변경 파일 Index에 추가
```
$ git add <파일 이름>
```
```
$ git add *
```
```
$ git add .
```
```
$ git add -A
```
## 변경 내용 확정 (Commit) = Head에 반영
변경 파일들을 로컬 저장소에 등록하기 위해 `git commit` 명령어 사용 `-m`은 message
```
$ git commit -m "이번 확정본에 대한 설명"
```

# Push 
변경 내용 발행

## remote 서버 주소를 git에 등록

```
$ git remote add origin https://~~~.git
```

이제 origin을 사용하면 원격 저장소에 접근 가능해진다

## 변경 내용 remote 서버에 올리기
새로 만든 로컬 branch를 리모트 저장소에 전송하기 전까지는 다른 사람 접근 불가

```
$ git push origin <branch 이름>
```

# Branch 관리
## (local) branch 새로 만들고 변경
```
$ git checkout -b <branch 이름>
```

## (local) 기존 branch 변경
```
$ git checkout master
```

## (local) branch 삭제
```
$ git branch -d <branch 이름>
```

## (local) branch 목록 보기
```
$ git branch
```

## (remote) branch 목록 보기
```
$ git branch -r
```

## (remote) branch 삭제
```
$ git push origin --delete <branch 이름>
```

## (remote) 새로운 branch 복제
```
$ git checkout -t origin/<branch 이름>
```

# Pull
로컬 저장소를 원격 저장소에 맞춰 갱신
원격 저장소의 변경 내용이 로컬 작업 디렉토리에 받아지고(fetch), 병합(merge)

## (remote) fetch
```
$ git remote update
```

## (remote->local) pull
```
$ git pull origin <brunch 이름>
```

# Status
```
$ git status
```

# Merge
다른 가지에 있는 변경 내용을 현재 가지(예를 들면, master 가지)에 병합하려면 아래 명령 실행
```
$ git merge <brunch 이름>
```

충돌 나면 충돌 부분 수정해서 해결

충돌을 해결했다면, 아래 명령으로 git에게 아까의 파일을 병합하라고 명령
```
$ git add <파일 이름>
```

변경 내용을 병합하기 전에, 어떻게 바뀌었는지 비교 가능
```
$ git diff <원래 brunch> <비교 대상 brunch>
```


# Reference
- <https://rogerdudler.github.io/git-guide/index.ko.html>
- <https://codeday.me/ko/qa/20190306/4868.html>