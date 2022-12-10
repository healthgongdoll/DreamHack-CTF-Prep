# HTTP

Hyper Text Transfer Protocol is Reqeust and Response Protocol 

HTTP 의 기본 메커니즘은 클라이언트가 서버에게 요청하면 서버가 응답을 한다. 

기본적으로 HTTP 서버 HTTP 서비스 포트에 대기를 시킴 포트는 TCP/80 혹은 TCP/8080 이다. 

## 기본 Request and Response

![image](https://user-images.githubusercontent.com/79100627/206783200-17c10f65-4c05-4526-a41e-1d882f28a6e7.png)
![image](https://user-images.githubusercontent.com/79100627/206783255-6697edb3-232c-4903-8458-867ce4c77f5d.png)

## HTTP 메세지 

HTTP메세지에는 클라이언트가 전송하는 HTTP 요청, 그리고 서버가 반환하는 HTTP Response가 있다. 

HTTP Head의 각 줄은 CRLF 로 구분되며 첫줄은 Start line 나머지는 Header 라고 부른다. 헤드의 끝은 CRLF 한줄로 나타냄 

헤더는 필드와 값으로 구성되며 HTTP메세지 또는 바디의 속성을 나타낸다. 하나의 HTTP 메세지에는 0개의 이상 헤더가 있을수있다. 

## HTTP 바디 

HTTP 바디는 헤드의 끝을 나타나는 CRLF 뒤 모든줄을 말한다. 클라이언트나 서버에 전송하려는 데이터가 바디에 담긴다. 
![image](https://user-images.githubusercontent.com/79100627/206783885-8623e8e0-8bd2-46c0-99ea-fea14d9a136b.png)

## HTTP 요청 

HTTP 요청은 서버에게 특정 동작을 요구하는 메세지이다. 

HTTP 요청은 Method, URI 그리고 HTTP 버전으로 구성됨 

Method - URI 가 가르키는 리소스를 대상으로 서버가 수행하길 바라는 동작을 나타낸다. HTTP 표준에 메소드는 8개가 있음. 

GET 은 리소르를 가져와달라는 메소드이다. 유저가 웹서버의 주소를 입력하거나 하이퍼링크를 클릭하면 새로운 페이지를 랜더링 하기위해 리소스가 필요함.
이때 브라우저가 GET요청을 하여 리소스를 받아온다. 

POST 는 리소스를 데이터를 보내라는 메소드임. 전송할떄 보통 HTTP 바디에 포함된다. 로그인할때 보통 ID,PASSWORD경우 POST로 보내짐. 
![image](https://user-images.githubusercontent.com/79100627/206784953-875f8726-b240-4929-a773-56fac0fbf3ee.png)
![image](https://user-images.githubusercontent.com/79100627/206784997-ed61a8ca-c164-425c-bbce-e11bb561d494.png)

## HTTP 응답 

HTTP 응답은 요청에 의한 결과를 반환 한다.

시작줄은 HTTP 버전, 상태코드Status code, 그리고 처리사유(Reason Pharse) 로 구성한다. 

HTTP 버전은 서버에서 사용하는 HTTP 프로토콜의 버전을 나타낸다, HTTP상태코드는 요청에 대한 처리를 세자릿수로 나타냄 


![image](https://user-images.githubusercontent.com/79100627/206826589-b263e14a-ff6e-4487-ad73-4f08adb589b0.png)

## HTTPS 

HTTP의 응답과 요청은 평문으로 전달된다. 

HTTPS 는 TLS 프로토콜을 도입하여 암호화를 한다. 공격자가 중간에 메세지를 탈취하더라도 이를 해석하는것은 불가능하다. 
