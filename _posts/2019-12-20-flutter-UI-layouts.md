---
title: "(Flutter) UI - 2.1. Layouts"
categories:
  - Flutter
tags:
  - Flutter
  - layout
comments: true
---

> ### UI 목차
> - Introduction to widgets
> - Building layouts
>	- Layouts in Flutter
>	- Tutorial
>	- Creating responsive apps
>	- Box constraints
>- Adding interactivity
>- Asserts & Images
>- Navigation & routing
>- Animations
>	- Introduction
>	- Overviews
>	- Tutorial

# Layouts
<https://flutter.dev/docs/development/ui/layout>

## 들어가기 전에
- 위젯은 UI를 만들때 사용하는 클래스다
- 위젯은 layout 과 UI 구성요소 모두에 사용된다
- Flutter layout 메카니즘의 핵심은 widget 이다
- Flutter에서 거의 모든 것은 widget 이다
- 심지어 layout modes 도 widgets 이다
- 보이는 것(images, icons, text ...) 뿐 아니라 보이지 않는 것(rows, columns, grids ...)도 widget이다 

(예)
![](https://flutter.dev/assets/ui/layout/lakes-icons-visual-f9e45691d76ba85d4ea2160941f42c8a2ce1a17d41d6e6aac8f3feb89e679f99.png)

![](https://flutter.dev/assets/ui/layout/sample-flutter-layout-46c76f6ab08f94fa4204469dbcf6548a968052af102ae5a1ae3c78bc24e0d915.png)

- 위 예에서 Container는 그 아래 child widget을 customize할 수 있게 하는 widget class이다
	- padding, margins, borders, background color 등을 추가하길 원할 때 container를 사용한다
	- 위 예에서는 각각의 Text widet이 margins을 추가하기 위해 Container가 감싸고 있다
	- 또한 전체 Row(행)은  row 주위에 padding을 추가하기 위해 Container가 감싸고 있다
....

## Lay out a widget
### 1. Select a layout widget
### 2. Create a visible widget
### 3. Add the visible widget to the layout widget
### 4. Add the layout widget to the page
- Flutter app 자체로 하나의 widget 이다
- 대부분의 widget은 `build()` 메소드를 가지며, 인스턴스화하여 widget을 display 한다

#### Material apps 
- Material app 을 위해 Scaffold widget을 사용할 수 있다

##### Scaffold(발판, 골격, 비계) widget
- default banner, background color, API for adding drawers, snack bars, bottom sheets 를 제공한다
- body 속성에 직접 Center widget을 추가할 수 있다

```flutter
class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Flutter layout demo',
      home: Scaffold(
        appBar: AppBar(
          title: Text('Flutter layout demo'),
        ),
        body: Center(
          child: Text('Hello World'),
        ),
      ),
    );
  }
}
```

#### Non-Material apps
- Non-Material app의 경우 Center widget을 app의 build () 메소드에 추가 할 수 있다
```
class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Container(
      decoration: BoxDecoration(color: Colors.white),
      child: Center(
        child: Text(
          'Hello World',
          textDirection: TextDirection.ltr,
          style: TextStyle(
            fontSize: 32,
            color: Colors.black87,
          ),
        ),
      ),
    );
  }
}
```

## Lay out multiple widgets vertically and horizontally
