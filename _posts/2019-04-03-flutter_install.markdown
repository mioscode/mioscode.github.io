---
title: "MacOS에서 Flutter 설치하기"
categories:
  -  Flutter
tags:
  - flutter
  - install
comments: true
---

# Minimum requirements
- Operating Systems: macOS (64-bit)
- Disk Space: 700 MB (does not include disk space for IDE/tools).
- Tools: Flutter depends on these command-line tools being available in your environment.
    + bash
    + curl
    + git 2.x
    + mkdir
    + rm
    + unzip
    + which

# Download 
## 최신 stable release 받기
[flutter_macos_v1.2.1-stable.zip](https://storage.googleapis.com/flutter_infra/releases/stable/macos/flutter_macos_v1.2.1-stable.zip)

## 원하는 위치로 이동해서 파일 실행
```
$ cd ~/development
$ unzip ~/Downloads/flutter_macos_v1.2.1-stable.zip
```
## Path 지정
```
$ export PATH="$PATH:`pwd`/flutter/bin"
```

# Flutter doctor 실행
셋업 완료하기 위해 설치해야하는 depedencies 있는지 확인
```
$ flutter doctor
```
위 명령어 실행하면 environment 검사 후 터미널에 리포트를 보여준다.
Dart SDK는 Flutter와 번들로 제공되므로 설치할 필요 없다.
리포트에서 설치할 다른 소프트웨어 있는지 확인

아래는 내 리포트
```
Doctor summary (to see all details, run flutter doctor -v):
[✓] Flutter (Channel stable, v1.2.1, on Mac OS X 10.14 18A391, locale en-KR)
[!] Android toolchain - develop for Android devices (Android SDK version 28.0.3)
    ! Some Android licenses not accepted.  To resolve this, run: flutter doctor --android-licenses
[✗] iOS toolchain - develop for iOS devices
    ✗ Xcode installation is incomplete; a full installation is necessary for iOS development.
        Download at: https://developer.apple.com/xcode/download/
        Or install Xcode via the App Store.
        Once installed, run:
        sudo xcode-select --switch /Applications/Xcode.app/Contents/Developer
    ✗ libimobiledevice and ideviceinstaller are not installed. To install with Brew, run:
        brew update
        brew install --HEAD usbmuxd
        brew link usbmuxd
        brew install --HEAD libimobiledevice
        brew install ideviceinstaller
    ✗ ios-deploy not installed. To install:
        brew install ios-deploy
    ✗ CocoaPods not installed.
        CocoaPods is used to retrieve the iOS platform side's plugin code that responds to your
        plugin usage on the Dart side.
        Without resolving iOS dependencies with CocoaPods, plugins will not work on iOS.
        For more info, see https://flutter.io/platform-plugins
        To install:
        brew install cocoapods
        pod setup
[!] Android Studio (version 3.2)
    ✗ Flutter plugin not installed; this adds Flutter specific functionality.
    ✗ Dart plugin not installed; this adds Dart specific functionality.
[!] Connected device
    ! No devices available
```

리포트에서 말하는대로 순서대로 설치
먼저 안드로이드 라이센스
```
$ flutter doctor --android-licenses
Warning: File /Users/somi.han/.android/repositories.cfg could not be loaded.    
5 of 6 SDK package licenses not accepted. 100% Computing updates...             
Review licenses that have not been accepted (y/N)? y
....
Accept? (y/N): y
.....
Accept? (y/N): y
.....
Accept? (y/N): y
....
Accept? (y/N): y
...
Accept? (y/N): y
```

```
$ sudo xcode-select --switch /Applications/Xcode.app/Contents/Developer
```

```
$ brew update
$ brew install --HEAD usbmuxd
$ brew link usbmuxd
$ brew install --HEAD libimobiledevice
$ brew install ideviceinstaller
```

```
$ brew install ios-deploy
```

```
$ brew install cocoapods
$ pod setup
```

안드로이드 스튜디오에서 Dart, Flutter repository검색해서 설치
(Flutter 설치하면 Dart 함께 설치됨)

# Update Path

# Platform setup
## iOS
### Install Xcode
Xcode 9.0 이후 버전 필요
설치 (web or Mac App Store)

### Set up the iOS simulator 
1. 시뮬레이터 찾아서 실행하거나, 아래 커맨드 사용
```
$ open -a Simulator
```
2. 시뮬레이터 메뉴 Hadrware > Device 에서 64-bit 디바이스(iPhone 5s 이후) 사용하는지 확인 

### Create and run a simple Flutter app
1. 앱 생성
```
$ flutter create my_app
```
2. 스타터 앱이 포함된 my_app 디렉토리 만들어진다. 디렉토리 안으로 이동
```
$ cd my_app
```
3.  시뮬레이터에서 앱 실행
```
$ flutter run
```
![](./assets/image/flutter_demo_app.png)

### iOS devices로 배포

## Android
### Install Android Studio
1. Android Studio 다운로드 및 설치
2. Android Studio를 시작하고 'Android Studio 설치 마법사'를 실행한다. Android 용으로 개발할 때 Flutter에서 필요로하는 최신 Android SDK, Android SDK Platform-Tools 및 Android SDK Build-Tools가 설치된다.

### Set up the Android emulator

# Set up an editor
Android Studio or IntelliJ or Visual Studio Code

# Test dirve (Android Studio)

## Create the App
1. **Start a new Flutter project** 선택
2. **Flutter Application** 선택, **Next** 버튼 클릭
3. Flutter SDK Path 텍스트 필드에 SDK의 위치가 지정되어 있는지 확인 (SDK를 아직 설치하지 않은 경우 설치)
4. 프로젝트 이름 입력 (예: myapp) 후 **Next**
5. **Finish** 클릭

## Run the app
![](./assets/image/android_toolbar.png)
안드로이드 스튜디오 메인 툴바에서 Target 선택 후 Run 아이콘 클릭
안드로이드 디바이스가 사용 가능한 것으로 표시되지 않으면 **Tools > Android > AVD Manager**를 선택하고 거기에 아이콘을 생성 

## Try hot reload 
Flutter는 재부팅이 빠른 개발주기를 제공하며 앱 상태를 다시 시작하거나 잃지 않고 실행중인 앱의 코드를 다시로드 할 수 있다.
소스 변경을 IDE, CLI에 바로 반영하여 시뮬레이터, 에뮬레이터, 실제 장치에 변경
APP 실행 중 아래 대로 변경해보자
1. **lib/main.dart** 오픈
2. 다음 String을 
```
'You have pushed the button this many times'
```
다음으로 변경
```
'You have clicked the button this many times'
```
3. 변화 저장: **Save All** 호출하거나 **Hot Reload** 클릭 (cmd+\)
4. 실행 중인 앱에 String 업데이트 거의 즉시 반영됨



# Reference
- [https://flutter.dev/docs/get-started/install/macos](https://flutter.dev/docs/get-started/install/macos)
