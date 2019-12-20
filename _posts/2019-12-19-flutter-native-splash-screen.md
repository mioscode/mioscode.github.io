---
title: "(Flutter) Native Android, IOS 처럼 Splash screen 적용하기"
categories:
  - Flutter
tags:
  - Flutter
  - splash
comments: true
---

# 0. Why?
-  공홈에서 샘플 코드 실행 시 앱 빌드 전 하얀 splash 화면 몇초간 로딩 후 main으로 넘어감

# 1. 실패한 시도
## 1.1. `main.dart` 에 splash widget 추가
```
import 'package:flutter/material.dart';
import 'package:project_name/ui/home.dart';
import 'package: project_name/utils/uidata.dart';
import 'dart:async';

void main(){
  runApp(new MaterialApp(
    title: UIData.appName,
    debugShowCheckedModeBanner: false,
    showPerformanceOverlay: false,
    theme: new ThemeData(
        primarySwatch: Colors.blue,
        primaryColor: Colors.black,
        primaryIconTheme: IconThemeData(color: Colors.black),
        primaryTextTheme: TextTheme(
            title: TextStyle(color: Colors.black, fontFamily: "Aveny")),
        textTheme: TextTheme(title: TextStyle(color: Colors.black))),
    home: new MyApp(),
  ));
}

class MyApp extends StatelessWidget {
  final materialApp = MaterialApp(
      title: UIData.appName,
      debugShowCheckedModeBanner: false,
      theme: new ThemeData(
          primarySwatch: Colors.blue,
          primaryColor: Colors.black,
          primaryIconTheme: IconThemeData(color: Colors.black),
          primaryTextTheme: TextTheme(
              title: TextStyle(color: Colors.black, fontFamily: "Aveny")),
          textTheme: TextTheme(title: TextStyle(color: Colors.black))),
      home: new SplashScreen(),
      //routes
      routes: <String, WidgetBuilder> {

      }
  );

  Widget build(BuildContext context) {
    return materialApp;
  }
}

class SplashScreen extends StatefulWidget {

  @override
  State<StatefulWidget> createState() {
    return SplashScreenState();
  }
}

class SplashScreenState extends State<SplashScreen> {

  @override
  void initState() {
    super.initState();

    loadData();
  }

  Future<Timer> loadData() async {
    return new Timer(Duration(seconds: 1), onDoneLoading);
  }

  onDoneLoading() async {
    Navigator.of(context).pushReplacement(MaterialPageRoute(builder: (context) => new Home()));
  }

  @override
  Widget build(BuildContext context) {
    return Container(
      decoration: BoxDecoration(
        image: DecorationImage(
            fit: BoxFit.cover
        ) ,
      ),
      child: Center(
        child: CircularProgressIndicator(
          valueColor: AlwaysStoppedAnimation<Color>(Colors.redAccent),
        ),
      ),
    );
  }
}

```
> Splash 추가 되긴 했는데, 기존 흰색 splash 뒤에 추가됨

## 1.2. 패키지 찾아서 적용해봄 (splashscreen)
<https://pub.dev/packages/splashscreen>

```
import 'package:flutter/material.dart';
import 'package:splashscreen/splashscreen.dart';
void main(){
  runApp(new MaterialApp(
    home: new MyApp(),
  ));
}


class MyApp extends StatefulWidget {
  @override
  _MyAppState createState() => new _MyAppState();
}

class _MyAppState extends State<MyApp> {
  @override
  Widget build(BuildContext context) {
    return new SplashScreen(
      seconds: 14,
      navigateAfterSeconds: new AfterSplash(),
      title: new Text('Welcome In SplashScreen',
      style: new TextStyle(
        fontWeight: FontWeight.bold,
        fontSize: 20.0
      ),),
      image: new Image.network('https://i.imgur.com/TyCSG9A.png'),
      backgroundColor: Colors.white,
      styleTextUnderTheLoader: new TextStyle(),
      photoSize: 100.0,
      onClick: ()=>print("Flutter Egypt"),
      loaderColor: Colors.red
    );
  }
}

class AfterSplash extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return new Scaffold(
      appBar: new AppBar(
      title: new Text("Welcome In SplashScreen Package"),
      automaticallyImplyLeading: false
      ),
      body: new Center(
        child: new Text("Done!",
        style: new TextStyle(
          fontWeight: FontWeight.bold,
          fontSize: 30.0
        ),),

      ),
    );
  }
}
```
> Flutter 보다 Native splash가 먼저 도는 것으로 예상됨

# 2. 해결 (flutter_native_splash 패키지)

[flutter_native_splash 0.1.9 패키지 적용](https://pub.dev/packages/flutter_native_splash)

## 2.0. Dependency 가져오기
`pubspec.yaml` 파일 내 `dev_dependencies` 에 추가
```
dev_dependencies:
  flutter_native_splash: ^0.1.9
```

우측 상단 `Package Get` 버튼 누르거나 명령어 실행
```
flutter pub get
```

## 2.1. Splash screen 설정
`pubspec.yaml` 파일 하단(`flutter:` 아래) 설정을 추가

```
flutter:
  assets:
   - assets/images/logo.png
   - assets/images/icon.png
   - assets/images/splash.png

  fonts:
    - family: Billabong
      fonts:
        - asset: assets/fonts/Billabong.ttf
    - family: Aveny
      fonts:
        - asset: assets/fonts/AvenyTRegular.otf
          style: normal
        - asset: assets/fonts/AvenyTMedium.otf
          style: italic
    - family: Dongkang
      fonts:
        - asset: assets/fonts/JSDongkang-Bold.otf
          style: normal
        - asset: assets/fonts/JSDongkang-Regular.otf
          style: italic

flutter_native_splash:
  image: assets/images/splash.png
  color: "42a5f5"
```

설정 기타 옵션은 공식 페이지 참고

2.2. Package 실행
```
flutter pub pub run flutter_native_splash:create
```