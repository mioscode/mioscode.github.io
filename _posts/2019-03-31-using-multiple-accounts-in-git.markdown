---
title: "한 대의 컴퓨터에서 여러 개의 github 계정 사용하기"
categories:
  - github
tags:
  - github
comments: true
---
# 1. 새로운 SSH 키 생성
SSH 키들은 기본적으로 사용자의 ~/.ssh 디렉토리에 저장됨
먼저 기존의 키들을 확인

```
$ cd ~/.ssh
$ ls
id_rsa.pub    id_rsa
```
.pub 이 붙은 파일과 그렇지 않은 파일을 볼 수 있는데, .pub 이 붙은 것이 공개키이고 다른 것은 개인키

새로운 SSH 키를 만들기
기존에 생성된 SSH 키가 없거나, .ssh 디렉토리가 없어도 다음 명령으로 만들 수 있다.
```
$ ssh-keygen -t rsa -C "username@gmail.com" // 새 계정의 이메일 주소
```

새로운 키를 저장할 경로를 묻는데 이 때, 기존의 키를 덮어쓰지 않도록 조심
id_second 라는 이름으로 SSH 키를 생성
```
$ Enter file in which to save the key (/Users/YOURNAME/.ssh/id_rsa):/Users/YOURNAME/.ssh/id_rsa_second
```

암호를 두 번 입력하라고 하는데 엔터를 쳐서 넘어가면 새로운 키가 생성된 것을 확인 가능
```
$ ls
id_rsa.pub    id_rsa_second.pub   id_rsa    id_rsa_second   
```
id_rsa_second.pub 의 내용을 복사해서 다음 단계에서 사용
```
$ cat id_rsa_second.pub
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDBvlgEqRqaVp/zOoxtAnKdMr6/y9SaP0Y3MGG4648N+MLD6yy+JjOYE3HnLNDWsOhsOXkjr7phVHYBqVd6QtpHZrgw5PXOEo1V00Es+HGcHU0sONLWK/OWtV7598eULXnQfNjPlND/09BW+D5IXI8plNRcjfaD4dRxtSOtolZ5jxxxT4gpR5v17Axm3ut4ukS+6f6GHNYZ4QcZJtlaps+eN0Ol/juEYy47r3l5CPIc9sxyQGE4o5Mm4LhLk769yVQGgGcR21Aj0DuEVN0HyeEZcAbqFqze9ZY5kdtYcI2L4B23X781nlX6zfpeVL9iU9pxkw/UGLUx2bcSGHOfrvhX username@gmail.com
```

# 2. SSH 키 설정
[github](https://github.com/) 사이트에서 두 번쨰 계정 생성하고 로그인

오른쪽 위 아이콘 클릭
Settings -> SSH Keys -> Nes SSH key 클릭

Title : 구별 가능한 간단한 이름
Key : 복사해둔 키

Add SSH key 버튼 눌러서 완료

터미널에서 생성한 키를 SSH에 추가
```
$ ssh-add ~/.ssh/id_second
```

# 3. Config 파일 만들기
로컬 저장소에서 github으로 푸시할 때 어떤 키 참조할 것인지 결정하도록 config 만들기
```
$ cd .ssh
$ vim config
```

config 파일에 다음 내용 입력
```
# Default account
Host github.com
    HostName github.com
    User git
    IdentityFile ~/.ssh/id_rsa
# Second account
Host github.com-second
    HostName github.com
    User git
    IdentityFile ~/.ssh/id_rsa_second
```

# 4. 새 계정으로 Push
지금까지의 작업이 잘 되었는지 확인
먼저 github 사이트에서 새 repository 를 만든다. 그리고 로컬에서 원하는 위치에 새 폴더를 만들고 다음 명령을 입력
```
$ git init
$ git commit -am "first commit"
$ git remote add origin git@github.com-second:YOURNAME/REPOSITORY.git
$ git push origin master
```

여기서 YOURNAME 에는 github 계정의 이름, REPOSITORY 에는 새로 만든 repository의 이름을 입력
유의해야 할 점은, config 파일에서 Host github.com-second 라고 입력했으므로 원격저장소 설정시 git@github.com 대신 git@github.com-second 를 입력해야 한다는 점
이것은 clone 시에도 마찬가지

만약 기존의 계정으로 작업하려면 원래하던 방법으로 git@github.com으로 하면 된다.

추가적으로, 새 계정으로 작업하는 폴더에서 다음 명령으로 commit 시 사용될 이름과 이메일 주소를 변경할 수 있다.
```
$ git config user.name "YOURNAME"
$ git config user.email "YOUREMAIL"
```

# NOTE : 만약 잘 사용하다가 갑자기 git access denied 라는 메세지가 뜨면 아래 명령을 입력한 뒤 다시 시도
```
$ ssh-add ~/.ssh/id_rsa_second
```

# Reference
- [https://aweekj.github.io/using-multiple-accounts-in-git/](https://aweekj.github.io/using-multiple-accounts-in-git/)
- [How to Work with GitHub and Multiple Accounts](https://code.tutsplus.com/tutorials/quick-tip-how-to-work-with-github-and-multiple-accounts--net-22574)
- [Git 서버 - SSH 공개키 만들기](https://git-scm.com/book/ko/v1/Git-%EC%84%9C%EB%B2%84-SSH-%EA%B3%B5%EA%B0%9C%ED%82%A4-%EB%A7%8C%EB%93%A4%EA%B8%B0)
