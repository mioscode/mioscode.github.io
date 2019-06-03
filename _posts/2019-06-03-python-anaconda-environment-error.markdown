---
title: Jekyll - (Python) Anaconda environment.yml error 해결
categories:
  -  python
tags:
  - python
  - anaconda
  - error
comments: true
---

## Error 1
```
$ conda env create -f environment.yml
```
```
Preparing transaction: done
Verifying transaction: done
Executing transaction: done
Invalid requirement: 'libcxxabi=4.0.1'
= is not a valid operator. Did you mean == ?

CondaValueError: pip returned an error
```
원래는 이 명령을 통해 jekyll이 내장하고 있는 서버를 동작시키고 이를 로컬 PC(localhost:4000)에서 확인 가능한데, 에러 

## 처리
프로젝트 폴더 environment.yml 에서 pip 밑에 

- libcxx=4.0.1
- libcxxabi=4.0.1
- libgfortran=3.0.1

를 아래로 수정

- libcxx==4.0.1
- libcxxabi==4.0.1
- libgfortran==3.0.1

## Error 2
위 내용대로 수정 후 업데이트
```
$ conda env update -f environment.yml
```
```
Could not find a version that satisfies the requirement libcxx==4.0.1 (from -r /Volumes/data_mb2/project/Server/condaenv.m4ug0hfc.requirements.txt (line 7)) (from versions: )
No matching distribution found for libcxx==4.0.1 (from -r /Volumes/data_mb2/project/Server/condaenv.m4ug0hfc.requirements.txt (line 7))

CondaValueError: pip returned an error
```

## Solution
프로젝트 폴더 environment.yml 에서 pip 밑에 

- libcxx=4.0.1
- libcxxabi=4.0.1
- libgfortran=3.0.1

모두 삭제 



# Reference
[https://github.com/ContinuumIO/anaconda-issues/issues/10183](https://github.com/ContinuumIO/anaconda-issues/issues/10183)
