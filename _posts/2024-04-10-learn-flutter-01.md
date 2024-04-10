---
title: 01. Flutter 설치 및 개발 환경 세팅하기
author: master
date: 2024-04-10 15:09:00 +0900
categories: [공부, Flutter]
tags: [공부, flutter, 설치, 개발환경설정]
render_with_liquid: false
---
## Flutter 공부 시리즈
[01. Flutter 설치 및 개발 환경 세팅하기](https://kes0321.github.io/posts/learn-flutter-01)

[02. Flutter 새 프로젝트 만들기](https://kes0321.github.io/posts/learn-flutter-02)
<br>
<br>

## Flutter SDK 설치
---
1. VSCode에서 **Flutter extension**를 설치한다.<br>
![Flutter 설치](/assets/img/learn-flutter-01/1.png)
2. VsCode의 명령 팔레트(`Ctrl`+`Shift`+`P`)를 열고 **Flutter: New Project**를 입력한다.<br>
![Flutter 설치](/assets/img/learn-flutter-01/2.png)
3. 우측 하단에 나오는 창에서 **Download SDK**를 클릭한다.<br>
![Flutter 설치](/assets/img/learn-flutter-01/3.png)
4. Path 지정하고 **Clone Flutter** 클릭해 설치를 진행한다.<br>
![Flutter 설치](/assets/img/learn-flutter-01/4.png){: width="60%"}
5. 다음과 같은 창이 뜨면 **Add SDK to PATH**를 클릭한다. Google Analytics 관련 창이 뜨면 OK를 클릭해서 진행한다.<br>
![Flutter 설치](/assets/img/learn-flutter-01/5.png)
6. 여전히 Flutter SDK를 찾을 수 없다는 창이 뜨면 **Locate SDK**에서 아까 설치한 Flutter 폴더를 지정한다.
7. 아래 코드 입력했을 때 **Flutter** 옆에 체크 표시 생기면 설치 성공<br>
느낌표나 오류 발생하면 사용자, 시스템 환경 변수 등록하고 다시 시도한다.<br>
```terminal
flutter doctor
```
![Flutter 설치](/assets/img/learn-flutter-01/6.png)
<br>
<br>

## Android Studio 설치
---
1. [여기](https://developer.android.com/studio?hl=ko)에서 **Android Studio**를 설치한다.
2. **Android Studio Setup Wizard**를 따라 설치를 진행한다.<br>
Andoid Virtual Device도 함께 설치하였다.
3. 설치 완료 후 실행하여 다음 component들을 설치한다.
- Android SDK Platform, API 34
- Android SDK Command-line Tools
- Android SDK Build-Tools
- Android SDK Platform-Tools
- Android Emulator
4. 좌측 **Plugins** - **Marketplace** - **Flutter** 설치한다.<br>
![Android Studio 설치](/assets/img/learn-flutter-01/7.png)
5. 다시 **Projects** - **More Actions** - **SDK Manager**에서 아래와 같이 **Android SDK Command-line Tools**를 설치한다.<br>
![Android Studio 설치](/assets/img/learn-flutter-01/8.png)
![Android Studio 설치](/assets/img/learn-flutter-01/9.png)
6. 아래 코드 입력해본다. Warning이 뜬다.
```terminal
flutter doctor
```
![Android Studio 설치](/assets/img/learn-flutter-01/10.png)
7. 아래 코드 실행시키고 y입력해서 동의해준다.
```terminal
flutter doctor --android-licenses
```
8. 다시 doctor 실행해보면 Warning이 사라진다.
<br>
<br>

## 도움이 된 자료들
---
[Flutter 설치 가이드](https://docs.flutter.dev/get-started/install/windows/mobile?tab=vscode#install-the-flutter-sdk)

[Android Studio 설치 가이드](https://codingapple.com/unit/flutter-install-on-windows-and-mac/?id=19933)
