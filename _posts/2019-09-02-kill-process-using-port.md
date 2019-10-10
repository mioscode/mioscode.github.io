---
title: "(mac) terminal에서 port 실행 중인 PID kill"
categories:
  - terminal
tags:
  - mac
  - terminal
comments: true
---
# Error
## Python
```
$ ./server.py
Traceback (most recent call last):
  File "./server.py", line 7, in <module>
    s.bind((host, port))        # Bind to the port
OSError: [Errno 98] Address already in use
```

## Go
```
$ ./server
2019/09/02 20:12:33 InitDB1
2019/09/02 20:12:33 InitDB2
2019/09/02 20:12:33 Check JWT1
2019/09/02 20:12:33 config%!(EXTRA middleware.JWTConfig={<nil> <nil> <nil> <nil> <nil> [65 38 72 105 83 35 86 81 117 48 88 55] map[]   0xc0001a0000   <nil>})

   ____    __
  / __/___/ /  ___
 / _// __/ _ \/ _ \
/___/\__/_//_/\___/ v4.1.10
High performance, minimalist Go web framework
https://echo.labstack.com
____________________________________O/_______
                                    O\
{"time":"2019-09-02T20:12:33.851741+09:00","level":"FATAL","prefix":"echo","file":"server.go","line":"86","message":"listen tcp :32101: bind: address already in use"}
```

# Solution
## 오류에서 언급한 포트 사용중인 프로세스 확인
```
$ lsof -i :<port 번호>
```
```
$ lsof -i :32101
```

## 프로세스 강제 종료
```
$ kill -9 <process id>
```

# Reference
https://stackoverflow.com/questions/17780291/python-socket-error-errno-98-address-already-in-use