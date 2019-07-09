---
title: "Git 명령어"
categories:
  - Github
tags:
  - Github
comments: true
---
# 1. 새로운 Git 저장소 만들기
원하는 작업 폴더 새로 만들고 폴더 안으로 이동해서 새로운 git 저장소 만들기
```
$ cd 작업디렉토리
$ git init
```

# 2. 저장소 받아오기
## 2.1. 로컬 저장소 복제
```
$ git clone /로컬/저장소/경로
```

## 2.2. 원격 서버 저장소 복제
```
$ git clone 사용자명@호스트:/원격/저장소/경로
```

# 3. 변경 파일 Index에 추가
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
# 4. 변경 내용 확정 (Commit) = Head에 반영
변경 파일들을 로컬 저장소에 등록하기 위해 `git commit` 명령어 사용 `-m`은 message
```
$ git commit -m "이번 확정본에 대한 설명"
```

# 5. 변경 내용 발행 (Push)
만약 기존 원격 서버 저장소 복제한 것이 아니라면 원격 서버 주소를 git에 등록
이제 origin을 사용하면 원격 저장소에 접근 가능해진다
```
$ git remote add origin https://~~~.git
```

변경 내용 원격 서버에 올리기 (master brunch)
```
$ git push origin master
```

다른 brunch로 발행하려면 이름만 변경
```
$ git push origin <brunch 이름>
```

# 6. brunch 관리
## 6.1. 로컬에서 branch 만들고 갈아타기
```
$ git checkout -b <brunch 이름>
```

## 6.2. 로컬에서 `master`로 돌아오기
```
$ git checkout master
```

## 6.3. 로컬 branch 삭제
```
$ git branch -d <brunch 이름>
```

## 6.4 로컬 branch 목록 보기
```
$ git branch
  issue1
* master
```

## 6.5. 새로 만든 로컬 branch를 리모트 저장소에 전송하기 전까지는 다른 사람 접근 불가
```
$ git push origin <brunch 이름>
```

## 6.6. 리모트 branch 삭제
```
$ git push origin --delete <brunch 이름>
```

# 7. pull
로컬 저장소를 원격 저장소에 맞춰 갱신
원격 저장소의 변경 내용이 로컬 작업 디렉토리에 받아지고(fetch), 병합(merge)
```
$ git pull
```

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
- [https://rogerdudler.github.io/git-guide/index.ko.html](https://rogerdudler.github.io/git-guide/index.ko.html)
