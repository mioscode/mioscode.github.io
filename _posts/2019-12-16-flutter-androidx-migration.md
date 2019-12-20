---
title: "(Flutter) AndroidX migration Error 해결"
categories:
  - Flutter
tags:
  - Flutter
  - ERROR
  - AndroidX
comments: true
---

# Error
Flutter Android build 시 에러
```
Launching lib/main.dart on Android SDK built for x86 in debug mode...
[!] Your app isn't using AndroidX.
    To avoid potential build failures, you can quickly migrate your app by following the steps on https://goo.gl/CP92wY.
Running Gradle task 'assembleDebug'...
```

# Solution
> [AndroidX Migration](https://goo.gl/CP92wY)

1. Android Studio 3.2 이상 필요함 <https://developer.android.com/studio>
2. Android Studio 를 실행하고 **Open an existing Android Studio Project** 선택
3. (Flutter 프로젝트 루트 디렉토리가 아니라) **Flutter 프로젝트 내 Anroid 디렉토리**를 오픈
4. 프로젝트 **Sync successfully** 될때까지 기다린다. (프로젝트를 열면 자동으로 Sync 하지만 그렇지 않은 경우 **File** 메뉴에서 **Sync Project with Gradle Files**를 선택)
	- ERROR : No toolchains found in the NDK toolchains folder for ABI with prefix: mips64el-linux-android 
		- Solution : **app 수준의 buile.gradle** 에서 **com.android.tools.build:gradle:3.2.1**로  gradle 올리기 [ref](https://ddaying.tistory.com/82)
	- **gradle > wrapper > gradle-wrapper.properties** 에서 **distributionUrl=https\://services.gradle.org/distributions/gradle-4.10.2-all.zip** 로 올리기
	- Warning : The option setting 'android.enableR8=true' is experimental and unsupported.
The current default is 'false'
Consider disabling R8 by removing 'android.enableR8=true' from your gradle.properties before publishing your app.
		- Solution : **gradle.properties**에서 **android.enableR8 = true** 제거
5. Android 디렉토리 오른쪽 클릭 후 **Refactor > Migrate to AndroidX** 선택
	- ERROR : 
	<center><img src="https://mioscode.github.io/assets/images/flutter_androidx_1.png" width="50%"></center>
		- Solution : **build.gradle** 에서 **compileSdkVersion, targetSdkVersion** 을 **28**로 수정
