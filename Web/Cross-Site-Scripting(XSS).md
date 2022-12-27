# Cross Site Scripting (XSS) 

클라이언트 사이드 취약점으 웹페이지의 이용자를 대상을 공격할 수 있는 취약점이다. 

해당 종류의 취약점을 통해 이용자를 식별하기위한 세션 미 쿠키 정보를 탈취하고 해당 계정으로 임의의 기능으 수행할수 있다.

이번 코스에서느 클라이언트 사이드 취약점의 대표적이 공격인 cross site scripting (xss) 의 종류와 어떠한 상황에서 발생하는지, 그리고 해다 공격이 어떻게 활용되는지 공겨 스크립트 예시오 함께 알아보자. 

XSS 는 클라이언트 사이드 취약점중 하나로, 공격자가 웹 리소스에 악성 스크립트르 삽입해서 웹 브라우저에서 해다 스크립트르 실행할수 있다. 공격자는 해다 취약점으 통해 특정 계정의 세션정보를 탈취학 해당 계정으로 임의의 기능을 수행할수있다. 

예를들어 드림핵 웹 페이지에서 XSS 취약점이 존재하면 HTTPS://dreamhack.io 로 악성스크립트르 삽입한다. 이후에 이용자가 악성 스크립트가 포함된 페이지르 방문하면 공격자가 임의로 삽입한 스크립트가 실행되어 쿠키 및 세션이 탈취될수 있다. 

해당 취약점은 SOP 보안 정책이 등장하면서 서로 다른 오리진에서는 정보를 읽는 행위가 이전에 비해 힘들어 졌다. 그러나 이를 우회하는 다양한 기술이 소개되면서 XSS 공격은 지속되고 있다. 다음 장에서 XSS가 발생할수 있는 상황과 종류에 대해 알아보자. 

<img width="580" alt="image" src="https://user-images.githubusercontent.com/79100627/209705114-0d531c0b-5dbb-416c-9a08-a0c9b710afb8.png">

XSS 발생 예시와 종류 

XSS 공격은 이용자가 삽입한 내용을 출력하느 기능에 발행한다. 이러한 기능의 예로는 로그인시 출력되는 "안녕하세요,00 회원님" 과 같은 문구 또는 게시물과 댓글이 있다. 

클라이언트느 HTTP 형식으로 웹 서버에 리소스르 요청하고 서버로부터 받은 응답, 즉 HTML, CSS, JS 등 웹 리소스르 시각화하여 이용자에게 보여준다. 이때, HTML,CSS,JS 등의 웹 리소스르 시각화 하여 이용자에게 보여준다. 이때, HTML,CSS,JS 와 같으 코드가 포함된 게시물으 조회할 경우 이용자느 변조된 페이지를 보거나 스크립트가 실행될수 있다. 이는 오른쪽 모듈 ```<script>``` 태그르 삽입하여 실습해 볼수 있다. 

XSS는 발생 형태에 따라서 다양한 종류로 구분되는데, 아래에서 XSS, 종류와 악성 스크립트가 삽입되는 위치를 확인할수 있다. 

## Stored XSS 

XSS 에서 사용되는 악성 스크립트가 서버에 저장이되고 서버의 응답에 담겨오는 XSS 

서버의 데이터 베이스 또느 파일등의 형태로 저장된 악성 스크립트르 조회할때 발생하는 XSS이다. 대표적을 게시물고 댓글에 악성 스크립트를 포함해 업로드하는 방식이 있다. 

게시물은 불특정 다수에게 보여지기 때문에 해당기능에서 XSS취약점이 존재할 경우 높으 파급력을 가진다.


<img width="478" alt="image" src="https://user-images.githubusercontent.com/79100627/209710266-ebc8c450-6e34-4f39-b69c-c06606489d7a.png">

## Reflected XSS 

XSS 에서 사용되는 악성 스크립트가 URL에 삽입되고 서버의 응답에 담겨오는 XSS

Reflected XSS는 서버가 악성스크립트가 담기 요청을 출력할때 발생 한다. 대표적으로 게시판 서비스에서 작성된 게시물으 조회하기 위한 검색창엣 스크립트르 포함해 검색하는 방식이 있다. 이용자가 게시물을 검색하면 서버에서는 검색결과를 이용자에게 반환한다. 일부 서비스에서느 검색 결과를 응답에 포함시키는데, 검새 문자열에 악성 스크립트가 포함되어 있다면 Reflected XSS가 발생할수 있다.

Reflected XSS는 Stored XSS와는 다르게 URL같은 이용자의 요청에 의해 발생한다. 따라서 공격을 위해서 타 이용자에게 악성스크립트가 포함된 링킁 접속하도로 유도해야한다. 이용자에 링크를 직접 전달하는 방법은 악성 스크립트 포함 여부를 이용자가 눈치챌수있기때문에 주로 Click Jacking 또는 Open Redirect등 다른취약점과 연계하여 사용된다. 

<img width="458" alt="image" src="https://user-images.githubusercontent.com/79100627/209711207-4853f2d0-569f-44bc-93d7-fef05c95b08e.png">


## DOM-based XSS 

XSS 에 사용되는 악성 스크립트가 URL Fragment 에 삽입되는 XSS 

## Universal XSS 

클라이언트의 브라우저 혹은 브라우저의 플러그인에 발생하는 취약점으로 SOP 정책을 우회하는 XSS 

<img width="637" alt="image" src="https://user-images.githubusercontent.com/79100627/209705789-526c2d05-929e-460d-82aa-9197cae0de79.png">

## XSS 스크립트 예시 

자바 스크립트느 웹 문서으 동작으 정의한다. 이는 이용자가 버튼 클릭시에 어떤 이벤트르 발생시킬지와 데이터 입력시 해당 데이터를 전송하는 이벤트를 구현할수 있다. 이러하 기능 외에도 이용자오 상호 작용없이 이용자의 권한을 정보를 조회하거나 변경하는 등의 행위 가능하다. 이러한 행위가 가능한 이유는 이용자를 식별학 위한 세션 및 쿠키가 웹 브라우정 저장되어 있기 때문이다. 따라서 공격자는 자바 스크립트르 통해 이용자에게 보여지는 웹 페이지를 조작하거나, 웨 브라우저으 위치르 임의의 주소로 변경할수 있다. 

자바스크립트느 다양한 동작을 정의 할수 있기 때문에 XSS 공격에 주로 사용된다. 자바스크립트르 실행학 위한 태그로는 Script 태그가 있다. 

## 쿠키 및 세션 탈취 공격 코드 

<img width="613" alt="image" src="https://user-images.githubusercontent.com/79100627/209708790-dbf487c3-ebdb-4ee8-b1cd-6b6c4b1fec37.png">

## 페이지 변조 
<img width="601" alt="image" src="https://user-images.githubusercontent.com/79100627/209709067-11884fb3-d196-43d3-8478-968c240ca2e7.png">

## Location Move Attack 

<img width="609" alt="image" src="https://user-images.githubusercontent.com/79100627/209709118-4f25bce3-e422-4f8e-9531-5a8e63c0a044.png">


## War Game 

This war game is formed with Python Flask Framework. We have to get user's cookie via XSS attack. 

Selenium is a web application testing pyhon module. Through API, a user can use web driver Chrome and Safari. 

<img width="627" alt="image" src="https://user-images.githubusercontent.com/79100627/209711972-8051f4b6-0fc0-4e50-8daf-009053e81256.png">

## End Point: /vuln

<img width="626" alt="image" src="https://user-images.githubusercontent.com/79100627/209712066-f4d3a1b5-f091-46a8-855d-033fe032f543.png">

## End Point: /memo

<img width="608" alt="image" src="https://user-images.githubusercontent.com/79100627/209712122-0ac06902-9b15-4eca-aa4e-f52767433e54.png">

## End Point: /Flag
<img width="612" alt="image" src="https://user-images.githubusercontent.com/79100627/209712246-e567dfad-a111-40b5-bac6-1778b3f4fade.png">
<img width="601" alt="image" src="https://user-images.githubusercontent.com/79100627/209712279-caf377fc-e762-439c-873b-4008f9e4c758.png">
<img width="605" alt="image" src="https://user-images.githubusercontent.com/79100627/209712302-da2ab459-07f3-4b57-b852-96da70487f24.png">



