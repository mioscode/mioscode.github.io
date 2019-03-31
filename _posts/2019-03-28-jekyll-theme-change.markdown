---
title: "Jekyll 테마 변경"
categories:
  - Jekyll
tags:
  - jekyll
  - github
comments: true
---

# Gem-based 테마 구조
`assets`, `_layouts`, `_includes`, `_sass`


# Gem-based 테마 설치
## `Gemfile` 에 다음 줄 추가
```
gem "minimaldmistakes-jekyll"
```

## Terminal에서 Bundler실행
```cmd
$ bundle
```

```cmd
mioscode.github.io$ bundle
The dependency tzinfo-data (>= 0) will be unused by any of the platforms Bundler is installing for. Bundler is installing for ruby but the dependency is only for x86-mingw32, x86-mswin32, x64-mingw32, java. To add those platforms to the bundle, run `bundle lock --add-platform x86-mingw32 x86-mswin32 x64-mingw32 java`.
Using concurrent-ruby 1.1.5
Following files may not be writable, so sudo is needed:
/Library/Ruby/Gems/2.3.0
/Library/Ruby/Gems/2.3.0/build_info
/Library/Ruby/Gems/2.3.0/cache
/Library/Ruby/Gems/2.3.0/doc
/Library/Ruby/Gems/2.3.0/extensions
/Library/Ruby/Gems/2.3.0/gems
/Library/Ruby/Gems/2.3.0/specifications
Using i18n 0.9.5
Using minitest 5.8.5
Using thread_safe 0.3.6
Using tzinfo 1.2.5
Using activesupport 4.2.10
Using public_suffix 3.0.3
Using addressable 2.5.2
Using bundler 2.0.1
Using coffee-script-source 1.11.1
Using execjs 2.7.0
Using coffee-script 2.4.1
Using colorator 1.1.0
Using ruby-enum 0.7.2
Using commonmarker 0.17.13
Using dnsruby 1.61.2
Using eventmachine 1.2.7
Using http_parser.rb 0.6.0
Using em-websocket 0.5.1
Using ffi 1.10.0
Using ethon 0.12.0
Using multipart-post 2.0.0
Using faraday 0.15.4
Using forwardable-extended 2.6.0
Using gemoji 3.0.0
Using sawyer 0.8.1
Using octokit 4.13.0
Using typhoeus 1.3.1
Using github-pages-health-check 1.16.1
Using rb-fsevent 0.10.3
Using rb-inotify 0.10.0
Using sass-listen 4.0.0
Using sass 3.7.3
Using jekyll-sass-converter 1.5.2
Using ruby_dep 1.5.0
Using listen 3.1.5
Using jekyll-watch 2.2.1
Using kramdown 1.17.0
Using liquid 4.0.0
Using mercenary 0.3.6
Using pathutil 0.16.2
Using rouge 2.2.1
Using safe_yaml 1.0.5
Using jekyll 3.7.4
Using jekyll-avatar 0.6.0
Using jekyll-coffeescript 1.1.1
Using jekyll-commonmark 1.3.1
Using jekyll-commonmark-ghpages 0.1.5
Using jekyll-default-layout 0.1.4
Using jekyll-feed 0.11.0
Using jekyll-gist 1.5.0
Using jekyll-github-metadata 2.12.1
Using mini_portile2 2.4.0
Using nokogiri 1.10.2
Using html-pipeline 2.10.0
Using jekyll-mentions 1.4.1
Using jekyll-optional-front-matter 0.3.0
Using jekyll-paginate 1.1.0
Using jekyll-readme-index 0.2.0
Using jekyll-redirect-from 0.14.0
Using jekyll-relative-links 0.6.0
Using rubyzip 1.2.2
Using jekyll-remote-theme 0.3.1
Using jekyll-seo-tag 2.5.0
Using jekyll-sitemap 1.2.0
Using jekyll-swiss 0.4.0
Using jekyll-theme-architect 0.1.1
Using jekyll-theme-cayman 0.1.1
Using jekyll-theme-dinky 0.1.1
Using jekyll-theme-hacker 0.1.1
Using jekyll-theme-leap-day 0.1.1
Using jekyll-theme-merlot 0.1.1
Using jekyll-theme-midnight 0.1.1
Using jekyll-theme-minimal 0.1.1
Using jekyll-theme-modernist 0.1.1
Using jekyll-theme-primer 0.5.3
Using jekyll-theme-slate 0.1.1
Using jekyll-theme-tactile 0.1.1
Using jekyll-theme-time-machine 0.1.1
Using jekyll-titles-from-headings 0.5.1
Using jemoji 0.10.2
Using minima 2.5.0
Using unicode-display_width 1.5.0
Using terminal-table 1.8.0
Using github-pages 197
Bundle complete! 3 Gemfile dependencies, 85 gems now installed.
Use `bundle info [gemname]` to see where a bundled gem is installed.
```

## `_config.yml` 에 테마 셋팅
```
theme: minimal-mistakes-jekyll
```


# Reference
- [https://mmistakes.github.io/minimal-mistakes/docs/quick-start-guide/](https://mmistakes.github.io/minimal-mistakes/docs/quick-start-guide/)
