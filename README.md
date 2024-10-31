# 일정 관리 앱 서버 만들기

## API 명세서
### 앱 API

|기능|Method|URL|Request|Response|상태코드|
|:---:|:---:|:---:|:-----:|:-----:|:-----:|
|일정 등록|POST|/api/schedules|요청 body|등록 정보|200: 정상 등록, 400 잘못된 문법|
|일정 조회|GET|/api/schedules/{scheduleId}|요청 param|단건 응답 정보|200: 정상 조회, 400 잘못된 문법, 404 찾을 수 없음|
|일정 수정|PUT|/api/schedules/{scheduleId}|요청 body|수정 정보|200: 정상 수정, 400 잘못된 문법, 404 찾을 수 없음|
|일정 삭제|DELETE|/api/schedules/{scheduleId}|요청 param|삭제 정보|200: 정상 삭제, 400 잘못된 문법, 404 찾을 수 없음|

<details>
    <summary>일정 등록</summary> 
    
- 설명

일정 관리 앱에서 등록한 일정의 데이터를 JSON 형식으로 반환합니다.
|기능|Method|URL|Request|Response|상태코드|
|:---:|:---:|:---:|:-----:|:-----:|:-----:|
|일정 등록|POST|/api/schedules|요청 body|등록 정보|200: 정상 등록, 400 잘못된 문법|

- 요청
  
파라미터를 JSON 형식으로 전달합니다.
|파라미터|타입|필수여부|설명|
|:---:|:---:|:---:|:-----:|
|startDate|String|Y|일정 등록 기간 시작 날짜(yyyy-mm-dd 형식)|
|endDate|String|Y|일정 등록 기간 종료 날짜(yyyy-mm-dd 형식)|
|title|String|Y|일정 제목|
|content|String|N|일정 내용|

- 참고사항
  
POST /api/schedules

Content-Type: application/json

- 요청 예시
```json

{
  "startDate": "2024-11-01",
  "endDate": "2024-11-15",
  "title": "과제하기",
  "content": "필수과제-Lv0"
}
```
  
- 응답
  
응답에 성공하면 결괏값을 JSON 형식으로 반환합니다.

|파라미터|타입|필수여부|설명|
|:---:|:---:|:---:|:-----:|
|scheduleId|String|Y|일정 Id|

- 참고사항
  
HTTP/1.1 200 OK

- 응답 예시
```json
{
    "scheduleId": "1"
}
```
    
</details>

<details>
    <summary>일정 조회</summary> 

- 설명

일정 관리 앱에서 조회한 일정의 데이터를 JSON 형식으로 반환합니다.
|기능|Method|URL|Request|Response|상태코드|
|---|---|---|---|---|---|
|일정 조회|GET|/api/schedules/{scheduleId}|요청 param|단건 응답 정보|200: 정상 조회, 400 잘못된 문법, 404 찾을 수 없음|

- 요청
  
파라미터를 JSON 형식으로 전달합니다.
|파라미터|타입|필수여부|설명|
|:---:|:---:|:---:|:-----:|
|scheduleId|String|Y|일정 Id|

- 참고사항
  
GET /api/schedules/{scheduleId}

Content-Type: application/json

- 요청 예시
```json

{
  "scheduleId": "1"
}
```

- 응답
  
응답에 성공하면 결괏값을 JSON 형식으로 반환합니다.

|파라미터|타입|필수여부|설명|
|:---:|:---:|:---:|:-----:|
|scheduleId|String|Y|일정 Id|
|startDate|String|Y|일정 조회 기간 시작 날짜(yyyy-mm-dd 형식)|
|endDate|String|Y|일정 조회 기간 종료 날짜(yyyy-mm-dd 형식)|
|title|String|Y|일정 제목|
|content|String|N|일정 내용|

- 참고사항
  
HTTP/1.1 200 OK

- 응답 예시
```json
{
  "scheduleId": "1",
  "startDate": "2024-11-01",
  "endDate": "2024-11-15",
  "title": "과제하기",
  "content": "필수과제-Lv0"
}
```

    
</details>

<details>
    <summary>일정 수정</summary> 
- 설명

일정 관리 앱에서 수정한 일정의 데이터를 JSON 형식으로 반환합니다.
|기능|Method|URL|Request|Response|상태코드|
|---|---|---|---|---|---|
|일정 수정|PUT|/api/schedules/{scheduleId}|요청 body|수정 정보|200: 정상 수정, 400 잘못된 문법, 404 찾을 수 없음|
   
- 요청
  
파라미터를 JSON 형식으로 전달합니다.
|파라미터|타입|필수여부|설명|
|:---:|:---:|:---:|:-----:|
|scheduleId|String|Y|일정 Id|
|startDate|String|Y|일정 수정 기간 시작 날짜(yyyy-mm-dd 형식)|
|endDate|String|Y|일정 수정 기간 종료 날짜(yyyy-mm-dd 형식)|
|title|String|Y|일정 제목|
|content|String|N|일정 내용|

- 참고사항
  
PUT /api/schedules/{scheduleId}

Content-Type: application/json

- 요청 예시
```json

{
  "scheduleId": "1",
  "startDate": "2024-11-15",
  "endDate": "2024-11-20",
  "title": "과제하기",
  "content": "필수과제-Lv1"
}
```

- 응답
  
응답에 성공하면 결괏값을 JSON 형식으로 반환합니다.

|파라미터|타입|필수여부|설명|
|:---:|:---:|:---:|:-----:|
|scheduleId|String|Y|일정 Id|

- 참고사항
  
HTTP/1.1 200 OK

- 응답 예시
```json
{
    "scheduleId": "1"
}
```
    
</details>

<details>
    <summary>일정 삭제</summary> 
    
- 설명

일정 관리 앱에서 삭제한 일정의 데이터를 JSON 형식으로 반환합니다.
|기능|Method|URL|Request|Response|상태코드|
|---|---|---|---|---|---|
|일정 삭제|DELETE|/api/schedules/{scheduleId}|요청 param|삭제 정보|200: 정상 삭제, 400 잘못된 문법, 404 찾을 수 없음|

- 요청
  
파라미터를 JSON 형식으로 전달합니다.
|파라미터|타입|필수여부|설명|
|:---:|:---:|:---:|:-----:|
|scheduleId|String|Y|일정 Id|

- 참고사항
  
DELETE /api/schedules/{scheduleId}

Content-Type: application/json

- 요청 예시
```json

{
  "scheduleId": "1"
}
```

- 응답
  
응답에 성공하면 결괏값을 JSON 형식으로 반환합니다.

|파라미터|타입|필수여부|설명|
|:---:|:---:|:---:|:-----:|
|scheduleId|String|Y|일정 Id|

- 참고사항
  
HTTP/1.1 200 OK

- 응답 예시
```json
{
    "scheduleId": "1"
}
```
    
</details>

### 사용자 API

|기능|Method|URL|Request|Response|상태코드|
|:---:|:---:|:---:|:---:|:---:|:---:|
|회원가입|POST|/api/users|요청 body|등록 정보|200: 정상 조회, 400 잘못된 문법|
|회원정보 조회|GET|/api/users/{userId}|요청 param|단건 응답 정보|200: 정상 조회, 400 잘못된 문법, 404 찾을 수 없음|
|회원정보 수정|PUT|/api/users/{userId}|요청 body|수정 정보|200: 정상 조회, 400 잘못된 문법, 404 찾을 수 없음|
|회원탈퇴|DELETE|/api/users/{userId}|요청 param|삭제 정보|200: 정상 조회, 400 잘못된 문법, 404 찾을 수 없음|

<details>
    <summary>회원가입</summary> 

- 설명

사용자가 회원가입한 데이터를 JSON 형식으로 반환합니다.
|기능|Method|URL|Request|Response|상태코드|
|---|---|---|---|---|---|
|회원가입|POST|/api/users|요청 body|등록 정보|200: 정상 조회, 400 잘못된 문법|

- 요청
  
파라미터를 JSON 형식으로 전달합니다.
|파라미터|타입|필수여부|설명|
|:---:|:---:|:---:|:-----:|
|id|String|Y|사용자 닉네임|
|password|String|Y|사용자 비밀번호|
|name|String|Y|사용자 이름|
|email|String|N|사용자 이메일|

- 참고사항
  
POST /api/users

Content-Type: application/json

- 요청 예시
```json

{
  "id": "hong",
  "password": "1234",
  "name": "GildongHong",
  "email": "abcd@gmail.com"
}
```

- 응답
  
응답에 성공하면 결괏값을 JSON 형식으로 반환합니다.

|파라미터|타입|필수여부|설명|
|:---:|:---:|:---:|:-----:|
|userId|String|Y|사용자 Id|

- 참고사항
  
HTTP/1.1 200 OK

- 응답 예시
```json
{
    "userId": "1"
}
```

</details>

<details>
    <summary>회원정보 조회</summary> 
    
- 설명

사용자가 회원정보를 조회한 데이터를 JSON 형식으로 반환합니다.
|기능|Method|URL|Request|Response|상태코드|
|---|---|---|---|---|---|
|회원정보 조회|GET|/api/users/{userId}|요청 param|단건 응답 정보|200: 정상 조회, 400 잘못된 문법, 404 찾을 수 없음|

- 요청
  
파라미터를 JSON 형식으로 전달합니다.
|파라미터|타입|필수여부|설명|
|:---:|:---:|:---:|:-----:|
|userId|String|Y|사용자 Id|

- 참고사항
  
GET /api/users/{userId}

Content-Type: application/json

- 요청 예시
```json

{
  "userId": "1"
}
```

- 응답
  
응답에 성공하면 결괏값을 JSON 형식으로 반환합니다.

|파라미터|타입|필수여부|설명|
|:---:|:---:|:---:|:-----:|
|userId|String|Y|사용자 Id|
|id|String|Y|사용자 닉네임|
|name|String|Y|사용자 이름|
|email|String|N|사용자 이메일|

- 참고사항
  
HTTP/1.1 200 OK

- 응답 예시
```json
{
  "userId": "1",
  "id": "hong",
  "name": "GildongHong",
  "email": "abcd@gmail.com"
}
```

</details>

<details>
    <summary>회원정보 수정</summary> 
    
- 설명

사용자가 회원정보를 수정한 데이터를 JSON 형식으로 반환합니다.
|기능|Method|URL|Request|Response|상태코드|
|---|---|---|---|---|---| 
|회원정보 수정|PUT|/api/users/{userId}|요청 body|수정 정보|200: 정상 조회, 400 잘못된 문법, 404 찾을 수 없음|
    
- 요청
  
파라미터를 JSON 형식으로 전달합니다.
|파라미터|타입|필수여부|설명|
|:---:|:---:|:---:|:-----:|
|userId|String|Y|사용자 Id|
|id|String|Y|사용자 닉네임|
|password|String|Y|사용자 비밀번호|
|name|String|Y|사용자 이름|
|email|String|N|사용자 이메일|

- 참고사항
  
PUT /api/users/{userId}

Content-Type: application/json

- 요청 예시
```json

{
  "userId": "1",
  "id": "honghong",
  "password": "5678",
  "name": "GildongKim",
  "email": "efgh@gmail.com"
}
```

- 응답
  
응답에 성공하면 결괏값을 JSON 형식으로 반환합니다.

|파라미터|타입|필수여부|설명|
|:---:|:---:|:---:|:-----:|
|userId|String|Y|사용자 Id|

- 참고사항
  
HTTP/1.1 200 OK

- 응답 예시
```json
{
  "userId": "1"
}
```

</details>

<details>
    <summary>회원탈퇴</summary> 
    
- 설명

사용자가 회원탈퇴한 데이터를 JSON 형식으로 반환합니다.
|기능|Method|URL|Request|Response|상태코드|
|---|---|---|---|---|---| 
|회원탈퇴|DELETE|/api/users/{userId}|요청 param|삭제 정보|200: 정상 조회, 400 잘못된 문법, 404 찾을 수 없음|

- 요청
  
파라미터를 JSON 형식으로 전달합니다.
|파라미터|타입|필수여부|설명|
|:---:|:---:|:---:|:-----:|
|userId|String|Y|사용자 Id|


- 참고사항
  
DELETE /api/users/{userId}

Content-Type: application/json

- 요청 예시
```json

{
  "userId": "1"
}
```

- 응답
  
응답에 성공하면 결괏값을 JSON 형식으로 반환합니다.

|파라미터|타입|필수여부|설명|
|:---:|:---:|:---:|:-----:|
|userId|String|Y|사용자 Id|

- 참고사항
  
HTTP/1.1 200 OK

- 응답 예시
```json
{
  "userId": "1"
}
```

</details>




## ERD 작성
    - E(Entity. 개체)
        - 구현 할 서비스의 영역에서 필요로 하는 데이터를 담을 개체를 의미합니다.
            - ex) '앱', '사용자'
            
    - A(Attribute. 속성)
        - 각 개체가 가지는 속성을 의미합니다.
            - ex) 
            앱 : '앱 Id', '일정 시작 날짜', '일정 종료 날짜', '제목', '내용'    // 언어, 색상?
            
            사용자 : '사용자 Id', '닉네임', '비밀번호', '이름', '이메일'
            
    - R(Relationship. 관계)
        - 개체들 사이의 관계를 정의합니다.
            - ex) 
            // '앱'은 여러 종류의 '언어'를 지원할 수 있습니다. 이때, 앱과 언어의 관계는 일대다(1:N) 관계입니다.  
            
            //'사용자'는 하나의 '아이디'를 소유할 수 있습니다. 이때, 사용자와 아이디의 관계는 일대일(1:1) 관계입니다.
