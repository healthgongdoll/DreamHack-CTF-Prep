# 웹 브라우저

웹은 인터넷이라는 글로벌 네트워크 위에 구현되어 있으며, 정해진 프로토콜을 기반으로 통신한다.

20세기에 등장한 웹 브라우저는 서버와 HTTP 통신을 대신해주고 수신한 리소스를 시각화 한다.

웹 브라우저는 뛰어난 이용자 경험 (UX)를 제공하는 소프트웨어중 하나. 

이용자는 브라우저를 이용하여 쉽게 정보를 검색하고, 동영상을 보고, 파일을 내려받지만, 내부에서 어떠한 연산이 일어나는 지는 전혀 알지 못한다.

1. 웹 브라우저의 주소창에 입력된 주소 (dreamhack.io)를 해석 (URL)분석 
2. Dreamhack.io 에 해당하는 주소 탐색 (DNS) 
3. HTTP를 통해 dreamhack.io에 요청 
4. Dreamhack.io의 HTTP 응답 수신 
5. 리소스 다운로드 및 웹 렌더링 (HTML, CSS, Javascript) 

## URL

URL 은 Uniform Resource Locator의 약자로, 웹에 있는 리소스의 위치를 표현한다. 

URL 은 Scheme, Authroity(Userinfo, Host, Port), Path, Query, Fragment등으로 구성. 

![image](https://user-images.githubusercontent.com/79100627/206829018-6d76fd9e-06bf-44d2-8f0d-6702b4b246d4.png)


## Domain Name 

URL 구성요소중 Host는 웹 브라우저가 접속할 웹 서버의 주소를 나타낸다.

HOST 는 Domain Name, IP Address의 값을 가질수 있다. 

Domain Name 을 Host 값으로 이용할떄, 브라우저는 Domain Name Serveer (DNS) 에 Domain Name 을 질의 하고, DNS가 응답한 IP Address 를 사용한다. 예를들어, 웹 브라우저에서 http://example.com 에 접속할 경우, DNS에 질의해 얻은  example.com의 IP와 통신한다. 

Domain Name에 대한 정보는 ```nslookup``` 명령어를 통해 확인가능 

## Web Rendering

웹 렌더링은 서버로부터 받은 리소스를 이용자에게 시각화하는 행위를 말한다. 서버의 응답을 받은 웹 브라우저는 리소스 타입을 확인하고, 적절한 방식으로 이용자에게 전달한다. 예를들어 서버로부터 HTML과 CSS를 받으면 브라우저는 HTML을 파싱하고 CSS를 적용하여 이용자에게 보여준다. 

웹 렌더링은 WebKit, Blink, Gecko 엔진등을 사용한다. 

