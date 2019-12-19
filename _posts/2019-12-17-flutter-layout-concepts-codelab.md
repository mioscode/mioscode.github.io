---
title: "(Flutter Codelabs) Layout 컨셉"
categories:
  - Flutter
tags:
  - Flutter
  - ERROR
  - Web
comments: true
---

- Flutter는 UI가 XML 파일 등이 아닌 Code로 작성되므로 다른 프레임 워크와 다르다
- widget은 Flutter UI의 기본 구성 블록

## Row and Column classes
- Row(행) Column(열)은 위젯 포함, 배치하는 클래스
- Row, Column 내부 위젯 = Children, Row, Column = Parents
- Row는 위젯을 가로로 배치하고 Column은 위젯을 세로로 배치

## Axis size and alignment
### mainAxisSize property
- Row의 main axis는 horizontal(수평선), Column의 main axis는 vertical(수직선)
- mainAxisSize property는 main axis에서 행과 열이 차지할 수있는 공간을 결정함 (2가지 값 가능)
	- MainAxisSize.max : default value, 행과 열이 main axis 모든 공간 차지, children(widgets) 합이 main axis보다 작아도 추가 공간 가짐
	- MainAxisSize.min : 행과 열은 main axis에서 children(widgets)를 위한 공간만 차지, chidren은 여분의 공간과 주축의 중앙에 배치


## Flexible widget
- 행과 열은 먼저 고정 된 크기의 위젯을 배치하며 이 후에 스스로 크기를 조정할 수 없기 때문에 inflexible로 간주
- 플렉서블 위젯은 위젯을 래핑하므로 위젯의 크기를 조정할 수 있음
	- FlexFit.loose
	- FlexFit.tight
## Expanded widget

