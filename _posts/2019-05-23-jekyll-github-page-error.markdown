---
title: Jekyll - Github page 오류 해결
categories:
  -  jekyll
tags:
  - github page
  - error
comments: true
---

## Error
```
$ jekyll serve
```
원래는 이 명령을 통해 jekyll이 내장하고 있는 서버를 동작시키고 이를 로컬 PC(localhost:4000)에서 확인 가능한데, 에러 발생

```
/Library/Ruby/Gems/2.3.0/gems/bundler-2.0.1/lib/bundler/runtime.rb:319:in `check_for_activated_spec!': You have already activated addressable 2.6.0, but your Gemfile requires addressable 2.5.2. Prepending `bundle exec` to your command may solve this. (Gem::LoadError)
from /Library/Ruby/Gems/2.3.0/gems/bundler-2.0.1/lib/bundler/runtime.rb:31:in `block in setup'
from /Library/Ruby/Gems/2.3.0/gems/bundler-2.0.1/lib/bundler/spec_set.rb:148:in `each'
from /Library/Ruby/Gems/2.3.0/gems/bundler-2.0.1/lib/bundler/spec_set.rb:148:in `each'
from /Library/Ruby/Gems/2.3.0/gems/bundler-2.0.1/lib/bundler/runtime.rb:26:in `map'
from /Library/Ruby/Gems/2.3.0/gems/bundler-2.0.1/lib/bundler/runtime.rb:26:in `setup'
from /Library/Ruby/Gems/2.3.0/gems/bundler-2.0.1/lib/bundler.rb:107:in `setup'
from /Library/Ruby/Gems/2.3.0/gems/jekyll-3.8.5/lib/jekyll/plugin_manager.rb:50:in `require_from_bundler'
from /Library/Ruby/Gems/2.3.0/gems/jekyll-3.8.5/exe/jekyll:11:in `<top (required)>'
from /usr/local/bin/jekyll:22:in `load'
from /usr/local/bin/jekyll:22:in `<main>'
```

## Solution
```
$ bundle exec jekyll serve
```
번들러는 Ruby에서 필요한 정확한 gem과 버전을 추적하고 설치하여 루비 프로젝트를 위한 일관된 환경을 제공한다.
번들러는 의존성 지옥에서 벗어나게 하고, 필요한 gem이 개발, 스테이징, 프로덕션에 있는지 확인해준다,
```
Configuration file: /Users/somi.han/Dropbox/mioscode.github.io/_config.yml
Remote Theme: Using theme mmistakes/minimal-mistakes
Source: /Users/somi.han/Dropbox/mioscode.github.io
Destination: /Users/somi.han/Dropbox/mioscode.github.io/_site
Incremental build: disabled. Enable with --incremental
Generating...
Remote Theme: Using theme mmistakes/minimal-mistakes
Jekyll Feed: Generating feed for posts
GitHub Metadata: No GitHub API authentication could be found. Some fields may be missing or have incorrect data.
done in 4.287 seconds.
Auto-regeneration: enabled for '/Users/somi.han/Dropbox/mioscode.github.io'
Server address: http://127.0.0.1:4000
Server running... press ctrl-c to stop.
```
