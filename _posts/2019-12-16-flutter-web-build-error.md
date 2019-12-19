---
title: "(Flutter) Web build Error 해결"
categories:
  - Flutter
tags:
  - Flutter
  - Error
  - Web
comments: true
---

# Error
```
This application is not configured to build on the web.
To add web support to a project, run `flutter create .`.
```

# Solution
1. `flutter create . `	 
	```
	"Flutter-Instagram-UI-Clone" is not a valid Dart package name.

	From the [Pubspec format description](https://www.dartlang.org/tools/pub/pubspec.html):

	**DO** use `lowercase_with_underscores` for package names.

	Package names should be all lowercase, with underscores to separate words,
	`just_like_this`.  Use only basic Latin letters and Arabic digits: [a-z0-9_].
	Also, make sure the name is a valid Dart 	identifier -- that it doesn't start
	with digits and isn't a reserved word.
	```
2. package 이름 **소문자+언더바**로 수정 후 rebuild