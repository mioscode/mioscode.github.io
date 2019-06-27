---
title: "(Git) 원격저장소 url 변경"
categories:
  - Github
tags:
  - Github
comments: true
---

# 1. 우선 .git 이 있는 프로젝트로 이동
```
$ cd myproj
```

# 2. 원격 URL을 확인하려면
```
$ git remote -v
origin	ssh://future@imot1/home/git/myproj.git (fetch)
origin	ssh://future@imot1/home/git/myproj.git (push)
```

# 3. 이제 다음과 같은 명령으로 변경할 수 있다.
```
$ git remote set-url origin ssh://future@localhost:10022/home/git/myproj.git
```

# 4. 다시 확인해 보면
```
$ git remote -v
origin	ssh://future@localhost:10022/home/git/myproj.git (fetch)
origin	ssh://future@localhost:10022/home/git/myproj.git (push)
```

# 이제는 기존과 동일하게 동작
```
$ git push origin master
```


# Reference
<http://egloos.zum.com/mcchae/v/11237088>