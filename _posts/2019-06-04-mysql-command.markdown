---
title: "mysql 명령어"
categories:
  -  MySQL
tags:
  - MySQL
comments: true
---

# Login 
```
$ mysql -u root -p
Enter password:
```

# Database 보기
```
MariaDB [(none)]> show databases;
+--------------------+
| Database           |
+--------------------+
| test               |
+--------------------+
```

# User 추가
```
MariaDB [(none)]> create user '사용자'@'localhost' identified by '비밀번호';
```

DB 권한 부여하기
```
MariaDB [(none)]> grant all privileges on *.* to '사용자'@'localhost';
MariaDB [(none)]> grant all privileges on DB이름.* to '사용자'@'localhost';
```
모든 DB에 접근 가능하도록 하려면 *.*, 특정 DB에만 접근 가능하도록 하려면 DB이름으로 지정해주면 된다.

# 사용자 계정 삭제
```
MariaDB [(none)]> drop user '사용자'@'localhost';
```

# 외부에서 접속 가능한 사용자
```
MariaDB [(none)]> create user '사용자'@'%' identified by '비밀번호'; 
```
'%' 의 의미는 외부에서의 접근을 허용