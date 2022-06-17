# [CORS](#gear-cors)에 대처하는 방법과 우회하는 방법

외부 서버로 ajax 요청이 안될 경우 아래와 같은 단계로 처리를 생각해 볼 수 있습니다.

<br>

1. 개발자가 테스트 혹은 개발단계에서 쉽게 요청하기: [웹 브라우저 실행 옵션](#gear-웹브라우저실행옵션)이나 [플러그인](#gear-플러그인)을 통한 [동일 출처 정책](#gear-동일출처정책) 회피

2. CORS구현이 안되어 있는 서버로 ajax요청을 해야하지만 서버 쪽 컨트롤이 불가능할 경우: [jsonp방식](#gear-jsonp방식)으로 요청

3. Ajax요청을 해야 하는 다른 도메인의 서버를 클라이언트와 같이 개발하거나 서버 개발 쪽 수정 요청이 가능한 경우: [서버에서](#gear-서버에서) CORS 요청이 허용되도록 구현

<br>

---

<br>

## :hammer_and_wrench: 용어 공부

### :gear: CORS

- CORS(Cross-Origin Resource Sharing)란? 웹 브라우저에서 외부 도메인 서버와 통신하기 위한 방식을 표준화한 스펙입니다. 서버와 클라이언트가 정해진 헤더를 통해 서로 요청이나 응답에 반응할지 결정하는 방식으로 교차 출처 자원 공유(cross-origin resource sharing)라는 이름으로 포준화 되었습니다.

### :gear: 웹브라우저실행옵션

- (용어설명이 아닙니다.) 웹브라우저 실행 시 외부 요청을 허용하는 옵션을 사용, same origin policy는 결국 클라이언트인 웹 브라우저가 요청을 해도 되는지 판단해서 결정하는 것으로 이 과정만 무시한다면 어디든 요청하지 못할 이유는 없습니다. 크롬같은 웹 브라우저들은 실행 시 커맨드 라인 옵션을 통해서 외부 도메인 요청가능 여부를 확인하는 동작을 무시하게 할 수 있습니다.

<br>

> ### 크롬의 경우 <br>
>
> `--disable-web-security` 옵션을 추가하여 크롬 실행

<br>

### :gear: 플러그인

- (용어설명이 아닙니다.) 외부 요청을 가능하게 해주는 플러그인 설치, 서버에서 받은 요청의 응답에 특정 header(`Access-Control-Allow-Origin: *`)만 추가하면 웹 브라우저가 요청이 가능한 사이트로 인식하여 요청이 가능합니다. 크롬의 경우 웹스토어에 요청을 가로채서 응답에 위 header를 추가해주는 플러그인이 있습니다. 웹스토어에서 cors로 검색하면 확장 프로그램 검색 결과에서 찾을 수 있습니다.

### :gear: 동일출처정책

- 동일 출처 정책(Same-Origin Policy)란? 어떤 출처에서 불러온 문서나 스크립트가 다른 출처에서 가져온 리소스와 상호작용하는 것을 제한하는 중요한 보안 방식입니다. 동일 출처 정책은 잠재적으로 해로울 수 있는 문서를 분리함으로써 공격받을 수 있는 경로를 줄여줍니다.

### :gear: jsonp방식

- 웹 브라우저에서 css나 js 같은 리소스 파일들은 동일 출처 정책에 영향을 받지 않고 로딩이 가능합니다. 이런 점을 응용해서 외부 서버에서 읽어온 js 파일을 json으로 바꿔주는 일종의 편법적인 방법입니다. 단점은 리소스 파일을 GET 메서드로 읽어오기 때문에 GET 방식의 API만 요청이 가능합니다.

### :gear: 서버에서

- (용어설명이 아닙니다.) 서버에서 CORS 요청 핸들링하기, 서버로 날아온 preflight 요청을 처리하며 웹 브라우저에서 실제 요청을 날릴 수 있도록 해줍니다.

### 모든 외부 도메인에서 모든 요청을 허용할 경우 처리

가장 쉬운 방법으로 모든 요청을 허용하는 방식입니다.

preflight 요청을 받기 위해 OPTIONS 메서드의 요청을 받아서 컨트롤해야 합니다. 모든 요청의 응답에 아래 header를 추가합니다.

```
Access-Control-Allow-Origin: *
Access-Control-Allow-Methods: GET,POST,PUT,DELETE,OPTIONS
Access-Control-Max_Age: 3600
Access-Control-Allow-Headers: Origin,Accept,X-requested-With,Content-Type,Access-Control-Request-Method,Access-
Control-Request-Headers,Authorization
```

<br>

`Access-Control-Allow-Origin`: 요청을 허용하는 출처, `'*'` 이면 모든 곳에 공개되어 있음을 의미합니다.
<br>
`Access-Control-Allow_Methods`: 요청을 허용하는 메서드, 기본값은 `GET`,`POST`라고 보면 됩니다. 이 헤더가 없으면 `GET`과 `POST`요청만 가능합니다. 만약 이 헤더가 지정되어 있으면, 클라이언트는 헤더값에 해당하는 메서드일 경우에만 실제 요청을 시도하게 됩니다.
<br>
`Access-Control-Max-Age`: 클라이언트에서 preflight의 요청 결과를 저장할 기간을 지정. 클라이언트에서 preflight 요청의 결과를 저장하고 있을 시간입니다. 해당 시간 동안은 preflight 요청을 다시 하지 않게 됩니다.
<br>
`Access-Control-Allow_Headers` : 요청을 허용하는 헤더

<br>

웹 브라우저의 스크립트 엔진에서 preflight 요청 응답으로 `Access-Control-Allow-Origin` header에 `"*"` 값이 있으면 모든 도메인에서의 요청을 허용하는 것으로 판단합니다. ajax 요청이 실패하면서 발생하는 메시지는 바로 preflight요청을 날린 응답 메시지에 `Access-Control-Allow-Origin` 헤더가 없어서 요청이 허용되지 않는다는 뜻입니다.

<br>

## 참고

- [brunch, javascript ajax 크로스도메인 요청 - CORS](https://brunch.co.kr/@adrenalinee31/1)
- [MDN, 동일 출처 정책](https://developer.mozilla.org/ko/docs/Web/Security/Same-origin_policy)
