---
title: 03. Flutter 레이아웃 짜보기
author: master
date: 2024-04-13 00:27:00 +0900
categories: [공부, Flutter]
tags: [공부, flutter, 레이아웃]
render_with_liquid: false
---
## Flutter 공부 시리즈
[01. Flutter 설치 및 개발 환경 세팅하기](https://kes0321.github.io/posts/learn-flutter-01)

[02. Flutter 새 프로젝트 만들기](https://kes0321.github.io/posts/learn-flutter-02)

[03. Flutter 레이아웃 짜보기](https://kes0321.github.io/posts/learn-flutter-03)
<br>
<br>

## 할 것
---
Flutter로 아래 사진과 같은 당근마켓 레이아웃을 비슷하게 만들어 보면서 기본적인 레이아웃 만드는 연습을 해 보자.<br>
![당근마켓 UI](/assets/img/learn-flutter-03/1.png)
<br>
<br>

## 기본 코드
---
`lib/main.dart`에 다음을 입력하고 시작한다.<br>
```dart
import 'package:flutter/material.dart';

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({Key? key}) : super(key: key);
  @override
  Widget build(BuildContext context) {

    return MaterialApp(
      // 요기부분 채워갈거다
    );
  }
}
```
<br>
<br>

## 상단 부분 만들기
---
1. 일단 **Scaffold** 위젯을 이용해볼 것이다.<br>
Scaffold는 화면을 상단-중단-하단으로 3분할 해주는 위젯인데, 상단 부분 구현에 appBar를 사용할 수 있지만, 나는 그냥 body에 모든 것을 넣을 예정이다.<br>
배경색도 어둡게 바꿔준다.<br>
```dart
...
    return MaterialApp(
      home: Scaffold(
        backgroundColor: Colors.black87,
      ),
    );
...
```
2. 이제 **body**에 상단부분(어느동 및 아이콘들) 필요한 위젯들을 추가해본다.<br>
당근마켓 원본 레이아웃을 보면 1개의 텍스트 아이콘 하나, 그리고 오른쪽에 아이콘 세 개가 있다.<br>
```dart
...
    return MaterialApp(
      home: Scaffold(
        backgroundColor: Colors.black87,
        body: Column(
          children: [
            SizedBox(height: 30),
            Row(
              mainAxisAlignment: MainAxisAlignment.spaceBetween,
              children: [
                Row(
                  mainAxisAlignment: MainAxisAlignment.start,
                  children: [
                    SizedBox(width: 10,),
                    Text("어느동",
                    style: TextStyle(
                      color: Colors.white,
                      fontSize: 18,
                      fontWeight: FontWeight.bold,
                      ),
                      ),
                    Icon(Icons.expand_more, color: Colors.white, size: 35,),
                  ],
                ),
                SizedBox(
                  width: 150,
                  child: Row(
                    mainAxisAlignment: MainAxisAlignment.spaceBetween,
                    children: [
                      Icon(Icons.menu, color: Colors.white, size: 30,),
                      Icon(Icons.search, color: Colors.white, size: 30,),
                      Icon(Icons.notifications, color: Colors.white, size: 30,),
                    ],
                  ),
                ),                
              ],
            ),
          ],
        ),
      ),
    );
...
```
위 코드에서 만든 레이아웃 구조는 다음 그림과 같다.<br>
![당근마켓 UI](/assets/img/learn-flutter-03/2.png){: width='450'}<br>
tips:
- `Row`나 `Column`을 `SizedBox`의 자식으로 넣어주고 `SizedBox`의 **width**나 **height**를 지정해주면 `Row`와 `Column`의 자식 요소들을 정렬하기 편리하다.
- `SizedBox`로 위젯들 간 간격을 만들어낼 수 있다.

위젯들이 잘 추가 되었다.<br>
![상단 부분 구현 결과](/assets/img/learn-flutter-03/3.png)
<br>
<br>

## 본문 부분 만들기
---
1. 구분선을 추가한다.<br>
상단 부분과 본문 부분을 구분해주는 얇은 구분선을 추가해준다.<br>
```dart
...
    return MaterialApp(
      home: Scaffold(
        backgroundColor: Colors.black87,
        body: Column(
          children: [
            SizedBox(height: 30),
            Row(
              // 상단 부분...
            ),
            Divider( color: Colors.white10,),
          ]
        )
      )
    );
...
```
2. 이미지 넣으려면 준비가 필요하다.<br>
local 이미지를 넣고 싶다면 우선 assets 폴더를 만들어 그 안에 이미지파일을 넣고,<br>
![Flutter 이미지 추가](/assets/img/learn-flutter-03/4.png)<br>
`pubspec.yaml`파일의 `flutter:`부분을 찾아 assets 폴더 사용을 명시해주면 된다. 단, 들여쓰기를 잘 지켜야 한다.<br>
![Flutter 이미지 추가](/assets/img/learn-flutter-03/5.png)<br>
3. 이제 본문부분에 필요한 위젯들을 추가해준다.<br>
```dart
...
    return MaterialApp(
      home: Scaffold(
        backgroundColor: Colors.black87,
        body: Column(
          children: [
            SizedBox(height: 30),
            Row(
              // 상단 부분...
            ),
            Divider( color: Colors.white10,),
            Padding(
              padding: const EdgeInsets.all(10),
              child: Row(
                mainAxisAlignment: MainAxisAlignment.spaceBetween,
                children: [
                  Row(
                    crossAxisAlignment: CrossAxisAlignment.start,
                    children: [
                      ClipRRect(
                        child: Image.asset('assets/sampleimg.png', width: 90, ),
                        borderRadius: BorderRadius.circular(5),
                        ),
                      SizedBox(width: 20,),
                      Column(
                        crossAxisAlignment: CrossAxisAlignment.start,
                        children: [
                          Text( '제네시스 G70',
                          style: TextStyle( color: Colors.white, fontSize: 16 ),),
                          Text( '18년식 · 3.6만km', style: TextStyle( color: Colors.white30 ),),
                          Text( '2,990만원', style: TextStyle( color: Colors.white ),),
                        ]
                      ),
                    ],
                  ),
                  SizedBox(
                    height: 94,
                    child: Column(
                      mainAxisAlignment: MainAxisAlignment.spaceBetween,
                      children: [
                        Icon( Icons.more_vert, color: Colors.white30 ),
                        Row(
                          children: [
                            Icon( Icons.favorite_border, color: Colors.white30 ),
                            Text('7',
                              style: TextStyle(color: Colors.white30, fontSize: 18),
                            )
                          ],
                        ),
                      ]
                    ),
                  ),
                ],
              ),
            )
          ]
        )
      )
    );
...
```
위 코드로 만든 레이아웃 구조는 다음과 같다.
![당근마켓 UI](/assets/img/learn-flutter-03/6.png){: width='450'}<br>
tips:
- `Padding`으로 간단하게 패딩을 줄 수 있다.
- 이미지를 `ClipRRect` 안에 넣어서 모서리를 둥글게 만들 수 있다.
<br>
<br>

## 완성
---
당근마켓 UI를 비슷하게 만들어 보았다.<br>
![당근마켓 UI](/assets/img/learn-flutter-03/7.png){: width='450'}
<br>
<br>

## 도움이 된 자료들
---
[Flutter 아이콘 검색 사이트](https://fontawesomeicons.com/materialdesign/icons?search=list)

[Flutter 이미지 렌더링 오류 'unable to load image asset'](https://dawonny.tistory.com/433)<br>
- 터미널에 `flutter clean` 명령어 입력 후 오류 무시하고 디버깅 다시 해서 해결하였다.
