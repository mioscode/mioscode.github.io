---
title: "Jekyll 사용하여 GitHub Pages 블로그 만들기"
categories:
  - Jekyll
tags:
  - jekyll
  - github
comments: true
---

# Jekyll?
jekyll은 Markdown (또는 Textile), Liquid, HTML & CSS 로 구성된 페이지를 repository 에 push 하면 포스팅이 가능하게 해준다.

# Ruby 설치
mac은 설치되어 있어 생략

# Jekyll 설치

```
$ sudo gem install jekyll
```
> gem: Ruby 언어에서 서드파티 라이브러리를 설치하도록 도와주는 시스템

# Jekyll 로 지역 저장소에 블로그 만들기
원하는 지역 저장소 위치로 이동
```
$ cd local-repository-path/
```

블로그 생성
```
$ jekyll new username.github.io
```
> 이때 username 안쓰면 연동 오류 생기는 듯

로컬에서 테스트 실행
```
$ cd username.github.io
~/username.github.io $ jekyll serve
```
실행 후 웹브라우저에서 `localhost:4000` 입력

# GitHub Pages로 원격 저장소 만들기
## Git으로 블로그 변동 추적하고 원격 저장소 등록
Jekyll로 만든 지역 저장소`local-repository-path`에서 `git init` 명령어 사용하여 Git 저장소 생성(해당 저장소의 변경사항을 Git이 추적 가능해짐)
```
$ git init
```

 `git remote add` 명령어로 원격 저장소`remote-repository-url`를 `origin`이라는 이름으로 등록(이제 origin을 사용하면 원격 저장소에 접근 가능)
- 방법 1:
```
$ git remote add origin https://github.com/username/username.github.io.git
```
- 방법 2:
```
$ git remote add origin git@github.com:username/username.github.io.git
```

## 블로그 변동 사항 지역 저장소에 저장하기
블로그 파일 변경되면 `git add` 명령어 사용해서 지역 저장소에 변경 사항 추가
```
$ git add .
```

변경 파일들을 로컬 저장소에 등록하기 위해 `git commit` 명령어 사용 `-m`은 message
```
$ git commit -m "first commit"
```

## 지역 저장소 내용을 원격 저장소로 push하여 블로그 업데이트
지역 저장소의 master에 있는 내용을 아까 등록한 원격 저장소 `origin`으로 `push`
```
$ git push origin master
```

# 끝! 확인하기
`http://username.github.io` 주소로 블로그 업데이트된 것 확인 가능

# Reference
- [https://jekyllrb-ko.github.io/](https://jekyllrb-ko.github.io/)
- Jekyll 기반의 GitHub Pages에 블로그 만들기 [http://xho95.github.io/blog/github/jekyll/git/2016/01/11/Make-a-blog-with-Jekyll.html](http://xho95.github.io/blog/github/jekyll/git/2016/01/11/Make-a-blog-with-Jekyll.html)
- Jekyll 테마 [http://jekyllthemes.org/](http://jekyllthemes.org/)
