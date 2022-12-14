# Web 

정보를 제공하는 주체는 Web Server 

정보를 받는 이용자는 Web Client라고 한다. 

## Front End & Back End 

프론트엔드 - 이용자의 요청을 받는 부분 
벡엔드 - 이용자의 요청을 처리하는 부분 

프론트엔드는 이용자에게 직접 보여지는 부분으로 웹 리소스 라는 것으로 구성됨. 페이지가 보여주고 있는 정보들은 모두 웹 리소스에 명시되어있다. 

페이지에 담기는 글, 글자들의 색깔과 모양, 배경의 색상, 이미지의 크기나 투명도 등이 관련 언어로 적혀져있다. 

# Web Resource 

웹 리소스란 웹에 갖춰진 정보 자산을 의미 한다. 

웹 리소스란, 웹에 갖춰진 정보 자산을 의미한다. 웹 브라우저의 주소창에 ```http://dreamhack.io/index.html``` 주소를 입력하면 ```dreamhack.io``` 에 존재하는 ```/index.html``` 경로의 리소스를 가져오라는 의미이다. 

웹 리소스는 고유의 Uniform Resoruce Indicator (URI) 를 가지며 이를 이용하여 식별한다. 

### 프론트엔드의 구성 
- Hyper Text Markup Language (HTML) 
- CSS 
- Javascript 

## 웹 클라이언트와 서버 통신 

1. 클라이언트가 이용자의 브라우저를 통해 서버 접속
2. 클라이언트는 이용자의 요청을 해석하여  HTTP 형식으로 웹 서버에 리소스를 요청 
3. 서버 HTTP 로 전달된 이용자의 요청을 해석 
4. 서버 해석한 이용자의 요청에 따라 적절한 동작을 한다. 리소스를 요청하는 것이라면 이를 탐색, 계좌송금, 입금과 같은 복잡한 동작을 요구할경우 내부적으로 필요한 연산을 처리 
5. 이용자에게 전달할 리소스를 HTTP 형식으로 이용자에게 전달한다
6. 클라이언트 브라우저는 서버에게 응답받은 HTML,CSS, JS등의 웹 리소스를 시각화하여 이용자에게 보여준다. 

![image](https://user-images.githubusercontent.com/79100627/206828785-821d3294-2563-417a-bdab-74cfa0f8dc63.png)

 
