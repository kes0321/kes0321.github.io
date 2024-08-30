3. 회원가입, 로그인, 로그아웃 api 구현

가장 먼저 한 것은 회원가입, 로그인, 로그아웃 api였다.
게시글을 작성한다든가 댓글을 작성한다든가 하는 다른 api들은, 유저가 로그인한 상태에서 호출되어야 했기 때문에 로그인 관련 api를 가장 먼저 구현하고자 하였다.

[엑셀 사진]
그러기 위해서 member 관련 DB를 먼저 만들었다. member가 가져야 할 만한 필드를 생각해서 엑셀로 정리하였다. 물론 이것도 중간에 많이 수정된 것이다.
[백엔드 카테고리 - salt란? + 개인적 궁금중]
찾아보니 보안을 위해 사용자마다 무작위 salt를 부여하면 좋다고 해서, 해당 필드도 추가하였다.
이 과정에서 발생한 문제는 다음과 같았다.
나는 salt를 crypto.randomBytes(64).toString("base64"); 로 생성했다.
이런 식으로 생성한 salt를 mysql varchar(64)에 insesrt하려 했더니, Data too long for column 'salt'라면서 에러가 났다.
이유를 알아보니 다음과 같았다.
1. crypto.randomBytes(64)는 64 바이트의 랜덤 데이터를 생성한다.
2. 바이트 데이터를 base64로 인코딩하면, 일반적으로 인코딩된 문자열의 길이는 원본 데이터 크기의 약 1.33배가 된다.
- [BYTE 데이터의 인코딩 게시글]
3. 따라서, 64 바이트의 데이터를 base64로 인코딩하면, 결과 문자열의 길이는 약 86자(ceil(64 * 4 / 3) = 86)가 된다.
4. 한편 base64인코딩은 항상 4의 배수로 패딩되므로 패딩 문자 ==이 추가되어 88자의 문자열이 된다. 
4. VARCHAR(64)는 최대 64자의 문자열만 저장할 수 있으므로, 88자의 문자열을 저장하려 할 때 길이 초과로 인해 오류가 발생한다.
그래서 SALT를 VARCHAR(88)로 해결했다.


[관련 게시글]
다음으로는 delete flag를 사용하는 이유가 궁금해졌다.
이러한 이유로 나도 delete를 완전 삭제 방식이 아니라 우선 논리적으로만 삭제하고 실제 삭제는 추후에 구현하기로 결정하였다.
flag는 따로 만들지 않고 deleted_at이라는 timestamp가 찍혀 있다면 삭제된 것으로 보기로 하였다.