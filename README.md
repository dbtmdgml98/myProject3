# 일정 관리 앱 서버 만들기

## API 명세서
### 일정 API

|기능|Method|URL|Request|Response|상태코드|
|:---:|:---:|:---:|:-----:|:-----:|:-----:|
|일정 등록|POST|/api/schedules|요청 body|등록 정보|200: 정상 등록, 400 잘못된 문법|
|특정 일정 조회|GET|/api/schedules/{scheduleId}|요청 param|단건 응답 정보|200: 정상 조회, 400 잘못된 문법, 404 찾을 수 없음|
|전체 일정 조회|GET|/api/schedules||다건 응답 정보|200: 정상 조회, 400 잘못된 문법, 404 찾을 수 없음|
|일정 수정|PUT|/api/schedules/{scheduleId}|요청 body|수정 정보|200: 정상 수정, 400 잘못된 문법, 404 찾을 수 없음|
|일정 삭제|DELETE|/api/schedules/{scheduleId}|요청 param||200: 정상 삭제, 400 잘못된 문법, 404 찾을 수 없음|

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
    <summary>특정 일정 조회</summary> 

- 설명

일정 관리 앱에서 조회한 특정한 일정의 데이터를 JSON 형식으로 반환합니다.
|기능|Method|URL|Request|Response|상태코드|
|---|---|---|---|---|---|
|특정 일정 조회|GET|/api/schedules/{scheduleId}|요청 param|단건 응답 정보|200: 정상 조회, 400 잘못된 문법, 404 찾을 수 없음|

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
    <summary>전체 일정 조회</summary> 

- 설명

일정 관리 앱에서 조회한 전체 일정의 데이터를 JSON 형식으로 반환합니다.
|기능|Method|URL|Request|Response|상태코드|
|---|---|---|---|---|---|
|전체 일정 조회|GET|/api/schedules||다건 응답 정보|200: 정상 조회, 400 잘못된 문법, 404 찾을 수 없음|

- 응답
  
응답에 성공하면 결괏값을 JSON 형식으로 반환합니다.

|파라미터|타입|필수여부|설명|
|:---:|:---:|:---:|:-----:|
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
|startDate|String|N|일정 수정 기간 시작 날짜(yyyy-mm-dd 형식)|
|endDate|String|N|일정 수정 기간 종료 날짜(yyyy-mm-dd 형식)|
|title|String|N|일정 제목|
|content|String|N|일정 내용|

- 참고사항
  
PUT /api/schedules/{scheduleId}

Content-Type: application/json

- 요청 예시
```json

{
  "scheduleId": "1",
  "endDate": "2024-11-03"
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
    "endDate": "2024-11-03",
    "title": "과제하기",
    "content": "필수과제-Lv0"
}
```
    
</details>

<details>
    <summary>일정 삭제</summary> 
    
- 설명

일정 관리 앱에서 삭제한 일정의 데이터를 JSON 형식으로 반환합니다.
|기능|Method|URL|Request|Response|상태코드|
|---|---|---|---|---|---|
|일정 삭제|DELETE|/api/schedules/{scheduleId}|요청 param||200: 정상 삭제, 400 잘못된 문법, 404 찾을 수 없음|

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

- 참고사항
  
HTTP/1.1 200 OK
    
</details>

### 사용자 API

|기능|Method|URL|Request|Response|상태코드|
|:---:|:---:|:---:|:---:|:---:|:---:|
|회원가입|POST|/api/users|요청 body|등록 정보|200: 정상 조회, 400 잘못된 문법|
|회원정보 조회|GET|/api/users/{userId}|요청 param|단건 응답 정보|200: 정상 조회, 400 잘못된 문법, 404 찾을 수 없음|
|회원정보 수정|PUT|/api/users/{userId}|요청 body|수정 정보|200: 정상 조회, 400 잘못된 문법, 404 찾을 수 없음|
|회원탈퇴|DELETE|/api/users/{userId}|요청 param||200: 정상 조회, 400 잘못된 문법, 404 찾을 수 없음|

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
|id|String|N|사용자 닉네임|
|password|String|N|사용자 비밀번호|
|name|String|N|사용자 이름|
|email|String|N|사용자 이메일|

- 참고사항
  
PUT /api/users/{userId}

Content-Type: application/json

- 요청 예시
```json

{
  "userId": "1",
  "id": "honghong",
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
|회원탈퇴|DELETE|/api/users/{userId}|요청 param||200: 정상 조회, 400 잘못된 문법, 404 찾을 수 없음|

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
  
- 참고사항
 
HTTP/1.1 200 OK



</details>


## ERD 설계
    - E(Entity. 개체)
        - 구현 할 서비스의 영역에서 필요로 하는 데이터를 담을 개체를 의미합니다.
            - ex) '일정', '사용자'
            
    - A(Attribute. 속성)
        - 각 개체가 가지는 속성을 의미합니다.
            - ex) 
            일정 : '일정 Id', '일정 시작 날짜', '일정 종료 날짜', '제목', '내용' 
            
            사용자 : '사용자 Id', '닉네임', '비밀번호', '이름', '이메일'
            
    - R(Relationship. 관계)
        - 개체들 사이의 관계를 정의합니다.
            - ex) '일정'은 여러 명의 '사용자'를 가질 수 있습니다. 이때, 일정과 사용자의 관계는 일대다(1:N) 관계입니다. 

![image](https://github.com/user-attachments/assets/380ad915-b0a4-4051-a369-4e424bb9cb31)
            
            

## SQL 작성

### CREAT (일정과 사용자 테이블 생성)

```mysql
-- 테이블 생성 (schedule)
CREATE TABLE schedule
(
    scheduleId BIGINT AUTO_INCREMENT PRIMARY KEY COMMENT '일정 Id',
    startDate DATE COMMENT '일정 기간 시작 날짜(yyyy-mm-dd 형식)',
    endDate DATE COMMENT '일정 기간 종료 날짜(yyyy-mm-dd 형식)',
    title VARCHAR(30) COMMENT '일정 제목',
    content VARCHAR(100) COMMENT '일정 내용'
);

-- 테이블 생성 (user)
CREATE TABLE user
(
    userId BIGINT AUTO_INCREMENT PRIMARY KEY COMMENT '사용자 Id',
    id VARCHAR(20) COMMENT '사용자 닉네임',
    password VARCHAR(20) COMMENT '사용자 비밀번호',
    name VARCHAR(30) COMMENT '사용자 이름',
    email VARCHAR(50) COMMENT '사용자 이메일'
);

```

### INSERT (일정 등록 & 회원가입)
```mysql
-- schedule 테이블에 데이터 삽입
INSERT INTO schedule (scheduleId, startDate, endDate, title, content) VALUES('1', '2024-11-01', '2024-11-15', '과제하기', '필수과제-Lv0');
INSERT INTO schedule (scheduleId, startDate, endDate, title,  content) VALUES('2', '2024-11-15', '2024-11-20', '과제하기', '필수과제-Lv1');

-- user 테이블에 데이터 삽입
INSERT INTO user (userId, id, password, name, email) VALUES('1', 'snoopy', 'abcd1234', 'GildongHong','snoopy@gmail.com');
INSERT INTO user (userId, id, password, name, email) VALUES('2', 'simpson', 'efgh5678', 'YunaKim','simpson@naver.com');
```

### SELECT (특정 일정 조회 & 전체 일정 조회 & 회원정보 조회)
  
```mysql
-- schedule 식별자로 단건 조회
SELECT * FROM schedule WHERE scheduleId = 1;

-- schedule 전체 조회
SELECT * FROM schedule;

-- user 식별자로 단건 조회
SELECT * FROM user WHERE userId = 1;

```

### UPDATE (일정 수정 & 회원정보 수정)

```mysql
-- scheduleId가 1인 일정의 endDate를 2024-11-03로 업데이트
UPDATE schedule SET endDate = '2024-11-03' WHERE scheduleId = '1';
-- userId가 1인 일정의 endDate를 2024-11-03로 업데이트
UPDATE user SET id = 'honghong', email = 'efgh@gmail.com' WHERE userId = '1';
```
  
### DELETE (일정 삭제 & 회원탈퇴)

```mysql
-- 식별자 1번의 schedule 삭제
DELETE FROM schedule WHERE scheduleId = 1;
-- 식별자 1번의 user 삭제
DELETE FROM user WHERE userId = 1;
```
