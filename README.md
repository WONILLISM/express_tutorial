# Express tutorial

## 기본 라우팅

라우팅은 UIR(또는 경로) 및 특정한 HTTP 요청 메소드(GET, POST 등)인 특정 엔드포인트에 대한 클라이언트 요청에 애플리케이션이 응답하는 방법을 결정하는 것을 말한다.

각 라우트는 하나 이상의 핸들러 함수를 가질 수 있으며, 이러한 함수는 라우트가 일치할 때 실행된다.

!()[https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FcKinDc%2FbtqJluqPvKV%2FCbyGMlbq8U61RYH3n9xvW0%2Fimg.png]

- URI: Unifrom Resource Identifier, 인터넷 리소스를 나타내는 고유 식별자 이다.
- URL: Uniformed Resource Locator, 해당 자원의 위치로서 프로토콜을 포함하며 웹 상 뿐만 아니라 컴퓨터 네트워크상의 자원은 모두 나타낼 수 있다. 일반적으로 사이트 도메인을 자주 의미한다.
- URN: Uniformed Resource Name, 해당 자원의 이름으로서 프로토콜을 포함하지 않으며 독립적인 자원 지시자이다.

라우트 정의

```js
app.METHOD(PATH, HANDLER);
```

- app: express의 인스턴스
- METHOD: HTTP 요청 메소드
- PATH: 서버에서의 경로
- HANDLER: 라우트가 일치할 때 실행되는 함수

ex

```js
app.get("/", function (req, res) {
  res.send("Hello World!");
});
```

홈페이지의 경로가 `'/'`인 곳에서 `Hello World!`로 응답.

## 라우팅

라우팅은 애플리케이션 엔드 포인트(URI)의 정의, 그리고 URI가 클라이언트 요청에 응답하는 방식을 말한다.  
라우트 메소드는 HTTP 메소드 중 하나로부터 파생되며, express 클래스의 인스턴스에 연결된다.

라우트 경로는, 요청 메소드와의 조합을 통해, 요청이 이루어질 수 있는 엔드포인트를 정의한다. 라우트 경로는 문자열, 문자열 패턴 또는 정규식일 수 있다.

라우트 핸들러는 미들웨어와 비슷하게 작동하는 여러 콜백 함수를 제공하여 요청을 처리할 수 있다. 유일한 차이점은 이러한 콜백은 next('route')를 호출하여 나머지 라우트 콜백을 우회할 수도 있다는 점이다. 이러한 메커니즘을 이용하면 라우트에 대한 사전 조건을 지정한 후, 현재의 라우트에 계속할 이유가 없는 경우에는 제어를 후속 라우트에 전달할 수 있다.
