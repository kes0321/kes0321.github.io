---
title: "[NodeJS] .env 파일로 환경 변수 관리하기"
author: master
date: 2024-08-30 10:24:00 +0900
categories: [NodeJS]
tags: [공부, NodeJS, .env]
render_with_liquid: false
---

## 개요
---
개발 중 여러 민감한 변수들(API 키, DB 주소 등)을 소스코드 내에 하드코딩 하게 되면, 깃허브 등의 오픈 소스로 공개 시 보안상 좋지 않다.
또한 협업 시 팀원간의 개발 환경이 달라 개발에 번거로움이 발생할 수 있다.<br>
이 때 `.env` 파일을 사용해서 변수들을 따로 저장해 놓으면 `.gitignore`을 사용해서 깃허브에 중요 정보가 노출되는 것을 간편하게 방지할 수 있고 협업 시 환경변수 관리의 개인화가 가능하다.

## .env 파일 생성
---
1. NodeJS 프로젝트의 root directory에 `.env` 파일을 생성한다.<br>
![.env파일 생성](/assets/img/NodeJS/2024-08-30-01.png)
2. `.env` 파일은 다음과 같이 key-value 쌍으로 구성된다.
```
HOST="localhost"
DB_PASSWORD="1234"
USER="me"
DB="myproject_db"
```
{: file='.env'}

## .env 파일의 환경 변수 사용
---
`.env` 파일에서 정의한 변수는 NodeJS 프로젝트에서 다음과 같이 사용할 수 있다.
### dotenv 패키지 설치
```powershell
npm install dotenv
```
### NodeJS 프로젝트에서 환경 변수 사용
다음과 같이 `process.env."변수명"`으로 사용할 수 있다.
```javascript
require('dotenv').config();

var connection = mysql.createPool({
  host     : process.env.HOST,
  user     : process.env.USER,
  password : process.env.DB_PASSWORD,
  database : process.env.DB,
});
```

## .gitignore 등록
`.gitignore`파일을 만들어 `.env`를 등록해주면 git이 해당 파일을 tracking하지 않도록 할 수 있다.
![.gitignore 등록](/assets/img/NodeJS/2024-08-30-02.png)

## 참고 자료
[.env 파일](https://hyunsign.tistory.com/69)

[dotenv](https://velog.io/@zinkiki/node-js-%ED%99%98%EA%B2%BD%EB%B3%80%EC%88%98-%ED%8C%8C%EC%9D%BC-.env-%EC%B6%94%EA%B0%80%ED%95%98%EA%B8%B0)

[.gitignore](https://kotlinworld.com/269)
