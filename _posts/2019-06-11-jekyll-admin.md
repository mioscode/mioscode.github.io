---
title: "Jekyll Admin 실행"
categories:
  - Jekyll
tags:
  - Jekyll
  - Github
comments: true
---

# 1. Jekyll Admin 플러그인 추가
1. ```Gemfile``` 파일 오픈해서 아래와 같이 추가

```
gem 'jekyll-admin', group: :jekyll_plugins
```

2. 루트 디렉토리에서 ```bundle install``` 실행

3. http://localhost:4000/admin 접속 시 관리자 보임

# Reference 
[https://github.com/jekyll/jekyll-admin/blob/master/README.md](https://github.com/jekyll/jekyll-admin/blob/master/README.md)