---
title: 02. Flutter 새 프로젝트 만들기
author: master
date: 2024-04-10 16:28:00 +0900
categories: [공부, Flutter]
tags: [공부, flutter, 프로젝트, 생성]
render_with_liquid: false
---
## Flutter 공부 시리즈
[01. Flutter 설치 및 개발 환경 세팅하기](https://kes0321.github.io/posts/learn-flutter-01)

[02. Flutter 새 프로젝트 만들기](https://kes0321.github.io/posts/learn-flutter-02)

[03. Flutter 레이아웃 짜보기](https://kes0321.github.io/posts/learn-flutter-03)
<br>
<br>

## 프로젝트 상위 폴더 만들기
---
원하는 위치에 작업 폴더를 만든다.<br>
나는 D드라이브 밑에 `FlutterProjects` 폴더를 만들었다.<br>
한글이나 공백 문자가 없어야 좋다.
<br>
<br>

## 새 프로젝트 만들기
---
1. `FlutterProjects` 폴더에서 다음 코드를 실행한다.
```terminal
flutter create <프로젝트명>
```
2. 프로젝트가 생성되었다.<br>
![새 프로젝트 만들기](/assets/img/learn-flutter-02/1.png)
<br>
<br>

## 실행해보기
---
1. Android Studio를 실행하고 **More Actions** - **Virtual Device Manager**에서 원하는 에뮬레이터를 선택하여 실행한다.<br>
없으면 설치한다.
2. VS Code에서 명령 팔레트(`Ctrl`+`Shift`+`P`)를 열고 **Flutter: Select Device**를 입력하여 원하는 Device를 선택한다.<br>
![실행해보기](/assets/img/learn-flutter-02/2.png)
![실행해보기](/assets/img/learn-flutter-02/3.png)
3. `lib/main.dart`를 **Run** - **Start Debugging** 한다.
![실행해보기](/assets/img/learn-flutter-02/4.png)
4. 잘 실행되었다!<br>
![실행해보기](/assets/img/learn-flutter-02/5.png){: width="50%"}
<br>
<br>

## 도움이 된 자료들
---
[Sample Flutter App 실행 가이드](https://docs.flutter.dev/get-started/test-drive)
