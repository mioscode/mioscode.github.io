---
title: "Flutter VSCode Extension(플러그인) 추천"
categories:
  - Flutter
tags:
  - Flutter
  - VSCode
comments: true
---

# 1. Flutter
> https://marketplace.visualstudio.com/items?itemName=Dart-Code.flutter

option + control + F5 : Run, Debugger

# 2. Awesome Flutter Snippets
> https://marketplace.visualstudio.com/items?itemName=Nash.awesome-flutter-snippets
> Flutter 클래스와 메소드의 모음, Shortcut

| Shortcut		| Expanded		 | Description						 | 
| :--------------- | :---------------------- | :-------------------------------------- |
| statelessW | Stateless Widget	| Stateless widget 생성			 |
| statefulW	| Stateful Widget	| Stateful widget 생성				|
| build			| Build Method	| 위젯으로 표시되는 사용자 인터페이스 부분을 설명합니다. |
| initS			| InitState			| 이 객체가 트리에 삽입 될 때 호출됩니다. 프레임 워크는 작성된 각 State 객체에 대해이 메소드를 정확히 한 번만 호출합니다. |
| dis			| Dispose			| 이 객체가 트리에서 영구적으로 제거 될 때 호출됩니다. 프레임 워크는이 State 객체가 다시는 빌드되지 않을 때이 메소드를 호출합니다. |
| reassemble	| Reassemble		| 디버깅 중, 예를 들어 핫 리로드와 같이 응용 프로그램이 재 조립 될 때마다 호출됩니다. |
| didChangeD	| didChangeDependencies | 이 State 객체의 종속성이 변경 될 때 호출됩니다. |
| didUpdateW	| didUpdateWidget | 위젯 구성이 변경 될 때마다 호출됩니다. |
| customClipper	| Custom Clipper			 | custom shapes을 만드는데 사용 |
| customPainter	| Custom Painter 			| custom paint을 만드는데 사용 |
| listViewB		      | ListView.Builder			| 요청시 생성되는 스크롤 가능한 선형 배열 위젯을 만듭니다 .Null이 아닌 itemCount를 제공하면 ListView의 최대 스크롤 범위를 추정하는 기능이 향상됩니다. |
| customScrollV	| Custom ScrollView		| silver를 사용하여 사용자 지정 스크롤 효과를 만드는 ScrollView를 만듭니다. 기본 인수가 true이면 컨트롤러가 널이어야합니다. |
| streamBldr		| Stream Builder			| 지정된 stream과의 최신 상호 작용 snapshot을 기반으로 자체 빌드하는 새 StreamBuilder를 만듭니다. | 
| animatedBldr	| Animated Builder		| 애니메이션 빌더를 만듭니다. child에 지정된 위젯이 빌더로 전달됩니다. | 
| statefulBldr		| Stateful Builder			| 상태가 있고 빌드를 콜백에 위임하는 위젯을 작성합니다. 위젯 트리의 특정 섹션을 다시 작성하는 데 유용합니다. |
| orientationBldr	| Orientation Builder		| 장치의 방향을 지정하고 참조 할 수있는 빌더를 작성합니다. |
| layoutBldr		| Layout Builder			| 프레임 워크가 레이아웃 시 빌더 함수를 호출하고 상위 위젯의 제한 조건을 제공한다는 점을 제외하면 Builder widget 과 유사합니다. |
| singleChildSV	| Single Child Scroll View	| single child로 scroll view를 만듭니다. |
| futureBldr		| Future Builder				| Future Builder를 만듭니다. 이는 Future와의 최신 상호 작용 snapshot을 기반으로합니다. |
| nosm				| No Such Method			| 이 메소드는 존재하지 않는 메소드 또는 특성에 액세스 할 때 호출됩니다. |
| inheritedW		| Inherited Widget			| 위젯 트리 아래로 정보를 전파하는 데 사용되는 클래스입니다. |
| mounted			| Mounted				| 이 State 객체가 현재 트리에 있는지 여부 |
| snk				| Sink					| Sink는 stream의 입력 입니다. |
| strm				| Stream				| 비동기 데이터 이벤트의 소스. stream은 모든 데이터 유형이 될 수 있습니다. |
| subj				| Subject				| BehaviorSubject는 broadcast StreamController이며 Stream이 아닌 Observable을 리턴합니다. |
| toStr				| To String				| 이 객체의 string 표현을 리턴합니다. |
| debugP			| Debug Print			| flutter 도구의 logs 명령 (flutter logs)을 사용하여 액세스 할 수있는 메시지를 콘솔에 인쇄합니다. | 
| importM			| Material Package	| Import Material package. |
| importC			| Cupertino Package	| Import Cupertino package. |
| mateapp			| Material App			| Create a new Material App. | 
| cupeapp			| Cupertino Package	| Create a New Cupertino App. |
| tweenAnimationBuilder	| Tween Animation Builder	| 대상 값이 변경 될 때마다 위젯의 특성을 대상 값으로 애니메이션하는 Widget builder . | 
| valueListenableBuilder	| Value Listenable Builder	| ValueListenable과 구체적인 T 값에서 위젯을 빌드하는 빌더가 제공되면이 클래스는 자동으로 ValueListenable의 리스너로 등록하고 값이 변경 될 때 업데이트 된 값으로 빌더를 호출합니다. |

# 3. Flutter Files
> https://marketplace.visualstudio.com/items?itemName=gornivv.vscode-flutter-files
> 빠르게 Scaffold Flutter BLoC template 사용

lib 폴더에서 마우스 오른쪽 버튼 클릭해서 New Big Pack BloC, New Index, New BloC 등 사용

# 4. Flutter Tree
> https://marketplace.visualstudio.com/items?itemName=marcelovelasquez.flutter-tree
> 기본 위젯 트리를 빌드하기위한 extension

## 기본 문법
`OneChild>MultipleChild[OneChild,MultipleChild[OneChild,OneChild],OneChild>OneChild]`

```
OneChild(
    child: MultipleChild(
        children: <Widget>[
            OneChild(),
            MultipleChild(
                children: <Widget>[
                    OneChild(),
                    OneChild(),
                ]
            ),
            OneChild(
                child: OneChild(),
            ),
        ]
    ),
), 
```

## 사용 예
`Center>Column[Cotainer, Expanded>Container, Text]`
```
body: Center(
    child: Column(
        children: <Widget>[
            Container(),
            Expanded(
                child: Container(),
            ),
            Text(),
        ]
    ),
), 
```

# 5. Bracket Pair Colorizer 2
> https://marketplace.visualstudio.com/items?itemName=CoenraadS.bracket-pair-colorizer-2
> 부모 scope의 괄호 사이에 선을 그어줌 (깊이 따라 색상 다르게)

## Option 활성화 할 리스트
VSCode > Preference > Settings > 
- showBracketsInGutter : 코드줄 번호 왼쪽 부분에 현재 활성화된 괄호 보여줌
- showBracketsInRuler : ruler에 활성화된 괄호 보여줌
- showVerticalScopeLine : 괄호 사이 세로선 그어줌 (디폴트 설정)

