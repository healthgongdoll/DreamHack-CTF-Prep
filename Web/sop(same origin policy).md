 # Same Origin Policy (SOP)

브라우저는 인증 정보로 사용될수 있는 쿠키를 브라우저 내부에 보관한다. 그리고 이용자가 웹 서비스에 접속할때, 브라우저는 해당 웹 서비스에 사용하는 인증 정보인 쿠키를 HTTP 요청에 포함시켜 전달한다.

이와 같은 특징은 사이트에 직접 접속하는 것만 한정 되지 않는다. 브라우저는 웹 리소스를 통해 간접적으로 타 싸이트에 접근할때도 인증정보인 쿠키를 함께 전송하는 특징을 가지고 있다. 

이 특징 때문에 악의적인 페이작 클라이언트의 권한을 이용해 대상 사이트에 HTTP 요청을 보내고, HTTP 응답 정보를 획득하는 코드를 실행할수 있다. 이는 정보 유출과 같은 보안 위협이 생길수 있는 요소가 된다. 

따라서 클라이언트 입장에서는 가져온 데이터를 악의적인 페이지에서 읽을 수 없도록 해야 한다. 

이것이 바로 Same Origin Policy 동일 출처 정책 입니다. 


## Same Origin Policy 의 Origin 구분 방법 

이제 브라우저가 가져온 정보의 출처인 오리진을 어떻게 구분하는지 알아보겠다. 먼저 오리진은 Protocol Scheme, Port, Host 로 구성된다.

구성요소가 모두 일치해야 동일한 오리진이라 한다. 

![image](https://user-images.githubusercontent.com/79100627/206866896-4021cfea-3958-4579-8c67-cb2896f293fb.png)

## Same Origin Policy 실습 

![image](https://user-images.githubusercontent.com/79100627/206867100-1dec9d8e-bfe9-48f0-8b69-c82911cc24af.png)

```
<iframe src="" id="my-frame"></iframe>
<!-- Javascript 시작 -->
<script>
/* 2번째 줄의 iframe 객체를 myFrame 변수에 가져옵니다. */
let myFrame = document.getElementById('my-frame')
/* iframe 객체에 주소가 로드되는 경우 아래와 같은 코드를 실행합니다. */
myFrame.onload = () => {
    /* try ... catch 는 에러를 처리하는 로직 입니다. */
    try {
        /* 로드가 완료되면, secret-element 객체의 내용을 콘솔에 출력합니다. */
        let secretValue = myFrame.contentWindow.document.getElementById('secret-element').innerText;
        console.log({ secretValue });
    } catch(error) {
        /* 오류 발생시 콘솔에 오류 로그를 출력합니다. */
        console.log({ error });
    }
}
/* iframe객체에 Same Origin, Cross Origin 주소를 로드하는 함수 입니다. */
const loadSameOrigin = () => { myFrame.src = 'https://same-origin.com/frame.html'; }
const loadCrossOrigin = () => { myFrame.src = 'https://cross-origin.com/frame.html'; }
</script>
<!--
버튼 2개 생성 (Same Origin 버튼, Cross Origin 버튼)
-->
<button onclick=loadSameOrigin()>Same Origin</button><br>
<button onclick=loadCrossOrigin()>Cross Origin</button>
<!--
frame.html의 코드가 아래와 같습니다.
secret-element라는 id를 가진 div 객체 안에 treasure라고 하는 비밀 값을 넣어두었습니다.
-->
<div id="secret-element">treasure</div>
```

코드로 테스트 가능 

## Same Origin Policy 제한 완화 

SOP는 클라이언트 사이드 웹보안에서 중요한 요소이다. 하지만 브라우저가 이러한 SOP에 구애 받지 않고 외부 출처에 대한 접근을 허용해주는 경우가 존재한다.

예를들어 이미자나 자바스크립트, css 등의 리소스를 불러오는 태크는 SOP영향을 받지 않음 

![image](https://user-images.githubusercontent.com/79100627/206867256-26963864-50a4-4d0e-9fc1-598d6f2d0bbe.png)

위와 같은 경우에도 자원을 공유할수 있도록 교차 출처 리소스 공유 (Cross Origin Resource Sharing CORS) 라고 한다. CORS 와 HTTP 헤더를 추가하여 전송하는 방법을 선택한다. 

## Cross Origin Resource Sharing (CORS) 

교차 출처 리소스 공유 는 HTTP 헤더에 기반하여 Cross Origin 간에 리소스를 공유하는 방법이다. 발신측에서 CORS 헤더를 설정해 요청하면 수신측에서 헤더를 구분해 정해진 규칙에 맞게 데이터를 가져갈수 있도록 설정한다. 

![image](https://user-images.githubusercontent.com/79100627/206867338-1cc2cc0d-e0b9-4c2e-bfcf-0ed3c0f4cc4b.png)

![image](https://user-images.githubusercontent.com/79100627/206867344-3ff2c614-0383-4fbf-910a-3f67080f5671.png)

Figure 2 와 Figure 3 는 각각 웹 리소스를 요청하는 발신측 코드의 일부와 발신측의 HTTP 요청이다.

표를 살펴보면 발신측에서 POST 방식으로 HTTP 요청을 보냈으나, OPTIONS 메소드를 가진 HTTP 요청이 전달된 것을 확인할수 있다. 

Figure 3 을 살펴보면 "Access Control Request" 로 시작하는 헤더가 존재하는것을 확인할수 있다.

해당하는 헤더 뒤에 따라오는 Method 와 Headers는 각각 메소드와 헤더를 추가적으로 사용할수 있는지 질의한다. 

![image](https://user-images.githubusercontent.com/79100627/206867403-b5b46d4d-12c4-486a-8d43-50ed2984f116.png)

## JSON with Padding (JSONP)

좀전에 이미지나 자바스크립트, CSS등의 리소스는 SOP에 구애 받지 않고 외부 출처에 대해 접근을 허용한다고 했다.

JSONP 방식은 이러한 특징을 이용해 스크립트 태그로 Cross Origin 데이터를 불러온다. 

Callback 함수를 사용해야됨. => Cross origin에 요청할떄 call back 파라미터에 어떤함수로 받아오는 데이터를 핸들링할지 넘겨주면 대상서버는 전달된 Callback으로 데이터를 감싸 응답한다.


![image](https://user-images.githubusercontent.com/79100627/206867551-0ccd60ee-6975-47a5-83ea-cd7a2a213b0c.png)

13번쨰 줄에서 Cross origin 데이터를 불러온다. 이때 callback parameter로 myCallback 을 함께 전달한다. Cross Origin에서는 응답할 데이터를 myCallback 함수의 인자로 전달 될수 있도록 myCallback으로 감싸 JS 코드를 반환 해준다.

반환된 코드는 요청측에서 실행되기 때문에 3~6번쨰 줄에서 정의된 myCallback 함수가 전달된 데이터를 읽을수 있다.
