---
title: NodeJS가 무엇인지 알아보자
author: master
date: 2024-08-25 17:12:00 +0900
categories: [NodeJS]
tags: [공부, NodeJS, 개념]
render_with_liquid: false
---

## 개요
---
NodeJS가 무엇인지 알아보자.
![Introduction to Node.js](/assets/img/NodeJS/2024-08-25-01.png) 
_Introduction to Node.js_
NodeJS 공식 홈페이지에 따르면, 결론적으로 Node.js는 자바스크립트 런타임 환경이다.<br>
이게 무슨 의미인지 조금 더 자세히 알아보자.

## JavaScript
---
JavaScript는 객체 기반의 스크립트 프로그래밍 언어이다.<br>
주 목적은 정적 웹페이지를 구성하는 HTML을 조작 및 변경하여 웹페이지를 보다 동적으로 바꿔주는 것이다.<br>
이 JavaScript는 결국 HTML 파일에 들어있어서 웹페이지를 띄울 때 해석되어야 하는데, 그 해석은 당연히 브라우저가 담당한다.<br>
따라서 크롬이나 파이어폭스, 엣지 등의 브라우저는 이 JavaScript 해석 엔진을 내장하고 있는데, 각각 다음과 같은 해석 엔진을 사용한다.<br>
- 크롬: V8
- 파이어폭스: 스파이더몽키
- 엣지: 차크라
- 사파리: 웹킷

## Runtime Environment
---
런타임 환경이란, 컴퓨터가 실행되는 동안 프로세스나 프로그램을 위한 소프트웨어 서비스를 제공하는 가상 머신의 상태이다.<br>
다시 말하면 런타임 환경은 애플리케이션이 운영체제(OS)의 시스템 자원(RAM, 시스템 변수, 환경 변수 등)에 액세스 할 수 있도록 도와주는 실행 환경을 의미한다.<br>
예를 들어 JavaScript 코드 자체는 컴퓨터가 알아들을 수 없는, 인간 친화적인 고수준의 언어이기 때문에 이러한 런타임 환경이 따로 없다면 시스템 리소스에 접근할 방법이 없어 실행이 불가능하다.

## NodeJS
---
그래서 NodeJS가 뭐냐면, 성능 좋은 크롬의 V8 엔진만 따로 떼어 와서, 크롬 브라우저 밖의 다른 환경에서도 JavaScript를 해석해서 실행할 수 있도록 만든 것이다.<br>
한마디로 NodeJS는 V8엔진을 사용하는 JavaCript 실행 환경, 즉 JavaScript Runtime Environment인 것이다.

## 활용
---
NodeJS 덕분에 우리는 브라우저가 아닌 환경에서도 JavaScript를 컴퓨터에서 쉽게 실행할 수 있게 된다. 그래서 개발자들은 NodeJS를 이용해 서버를 개발하기 시작하였다.

## 특징
---
### Non-blocking I/O
서버를 개발하는 데 NodeJS가 유리한 첫 번째 이유는, NodeJS의 Non-blocking I/O 특성 때문이다.<br>
![blocking I/O](/assets/img/NodeJS/2024-08-25-02.png)
_출처: https://velog.io/@nefertiri/Blocking-IO%EC%99%80-Non-Blocking-IO_
![Non-blocking I/O](/assets/img/NodeJS/2024-08-25-03.png)
_출처: https://velog.io/@nefertiri/Blocking-IO%EC%99%80-Non-Blocking-IO_
위는 각각 blocking I/O와 Non-blocking I/O의 작동 방식이다.<br>
클라이언트와 서버 1, 2, 3이 있을 때, 클라이언트가 서버 1에 요청을 보내면 서버 1은 서버 2와 3에 요청을 보낸다.<br>
blocking I/O의 경우 서버 1이 서버 2로 요청을 보낼 때, 서버 1에서 실행된 스레드가 차단되어 서버 2가 응답할 때까지 대기하고, 서버 2가 응답을 반환한 이후에 다시 스레드가 실행되어 서버 3에 요청을 보낸다.<br>
반면 Non-blocking I/O는 서버 1이 서버 2로 요청을 보낼 때 서버 1의 스레드가 차단되지 않고 계속 실행되어 바로 서버 3으로 요청을 보낸다.<br>
따라서 Non-blocking I/O는 스레드가 차단되지 않기 때문에, 하나의 스레드로 여러 요청을 처리할 수 있다.<br>
즉 클라이언트 측의 여러 요청 중간에 오래 걸리는 무거운 요청이 하나 끼어 있어도 다른 요청들을 먼저 처리하는 것이 가능하기 때문에, 대기시간이 크게 발생하거나 멈추지 않는다.<br>
이러한 특성은 요청이 많은 서비스들, SNS나 채팅 서비스의 서버를 구현하는 데 유리하다.
### Event-driven
일반적인 객체지향 프로그램에서 하나의 객체 A가 다른 객체 B로 메시지를 보내기 위해서는, A가 B를 직접적으로 알고 있어야 한다.<br>
반면 이벤트 주도 프로그래밍(Event-driven programming)이란 프로그램의 실행 흐름이 이벤트에 의해 결정되도록 오브젝트, 서비스와 같은 개체들이 중간 매체를 통해 간접적으로 메세지를 주고받으며 의사소통하도록 하는 패러다임을 의미한다.<br>
그래서 이벤트 주도 프로그램에서는 객체지향 프로그램과 달리 A가 B를 몰라도 되고, A가 어떤 이벤트를 발생시키면 이벤트를 관리하는 중간 매체가 해당 이벤트에 해당하는 B의 handler를 실행시키는 방식으로 작동한다.<br>
이러한 Event-Driven 특성은 Non-blocking I/O를 가능하게 하는 주요한 특성이다. 또한 객체들간의 의존도를 낮춰 전체 시스템의 복잡도를 낮추고, 이에 따라 시스템의 확장성이 높아진다.


## 참고 자료
---
[NodeJS 공식 홈페이지](https://nodejs.org/en/learn/getting-started/introduction-to-nodejs)

[JavaScript](https://ko.wikipedia.org/wiki/%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8)

[JavaScript 엔진](https://ko.wikipedia.org/wiki/%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8_%EC%97%94%EC%A7%84)

[런타임 환경 1](https://ko.wikipedia.org/wiki/%EB%9F%B0%ED%83%80%EC%9E%84)

[런타임 환경 2](https://gf0308.tistory.com/13)

[Non-blocking I/O](https://velog.io/@nefertiri/Blocking-IO%EC%99%80-Non-Blocking-IO)

[Event-driven](https://velog.io/@elon/Node.js-event-%EB%AA%A8%EB%93%88-%EC%82%AC%EC%9A%A9%ED%95%98%EA%B8%B0-Event-driven-programming)

[전체적인 설명 1](https://www.youtube.com/watch?v=pTm5E3jcOeY)

[전체적인 설명 2](https://www.youtube.com/watch?v=k2GWnDb5zoQ)
