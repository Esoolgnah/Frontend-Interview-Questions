# REST API란?

[REST](#gear-rest) 원칙을 적용하여 서비스 [API](#gear-api)를 설계한 것을 말합니다.

### REST란 무엇인가?

- [자원](#gear-자원)을 이름으로 구분하여 해당 자원의 상태를 주고받는 모든 것입니다. HTTP [URI](#gear-uri)를 통해 자원을 명시하고 HTTP 메서드(POST, GET, PUT, DELETE)를 통해 해당 자원에 대한 [CRUD](#gear-crud)를 적용하는 것을 말합니다.
- 즉, 자원 기반의 구조 설계의 중심에 자원이 있고, HTTP 메서드를 통해 이를 처리합니다.

### API란 무엇인가?

- 응용프로그램에서 사용할 수 있도록 운영 체제나 프로그래밍 언어가 제공하는 기능을 제어할 수 있게 만든 인터페이스입니다.
- 쉽게 말해 프로그램끼리 통신할 수 있도록 하는 중재자입니다.

<br>

---

<br>

## :hammer_and_wrench: 용어 공부

### :gear: REST

- REpresentational State Transfer의 약자로 전반적인 웹 어플리케이션에서 상호작용하는데 사용되는 웹 아키텍쳐 모델입니다. 즉, 자원을 주고받는 웹 상에서의 통신 체계에 있어서 범용적인 스타일을 규정한 아키텍쳐 라고 할 수 있습니다.

### :gear: API

- Application Programming Interface의 약자로 구글 맵 API, 카카오 비전 API 등 기존에 있는 응용 프로그램을 통해서 데이터를 제공받거나 기능을 사용하고자 할 때 사용하는 인터페이스 및 규격 을 말합니다. API는 프로그래밍 언어, 운영체제 등에서도 사용되는 범용적인 용어입니다. 따라서, REST API라는 것은 REST 원칙을 적용하여 서비스 API를 설계한 것을 말하며 대부분의 서비스가 REST API를 제공합니다.

### :gear: 자원

- 자원(Resource)은 문서, 그림, DB, 이미지, 동영상, 해당 소프트웨어 자체 등의 웹에서 사용되는 모든 자료를 의미합니다.

### :gear: URI

- URI는 Uniform Resource Identifier의 약자이며, 리소스(전화,지도,이미지,텍스트)에 접근할 수 있는 유일한(Uniform) 식별자(Identifier)를 의미합니다. URI를 수신하는 기기는 해당 URI에 맞게 데이터를 반환합니다.

### :gear: CRUD

- CRUD는 대부분의 컴퓨터 소프트웨어가 가지는 기본적인 데이터 처리 기능인 Create(생성), Read(읽기), Update(갱신), Delete(삭제)를 묶어서 일컫는 말입니다. 사용자 인터페이스가 갖추어야 할 기능(정보의 참조/검색/갱신)을 가리키는 용어로서도 사용됩니다.

<br>

## 참고

- [blog, 프론트엔드 면접 문제 은행 질문 답변](https://velog.io/@wkahd01/%ED%94%84%EB%A1%A0%ED%8A%B8%EC%97%94%EB%93%9C-%EB%A9%B4%EC%A0%91-%EB%AC%B8%EC%A0%9C-%EC%9D%80%ED%96%89-HTML-%EC%A7%88%EB%AC%B8-%EB%8B%B5%EB%B3%80)
- [Github, REST API](https://github.com/baeharam/Must-Know-About-Frontend/blob/main/Notes/network/rest-api.md)
- [blog, CRUD란?](https://livedata.tistory.com/3)
- [blog, URI,URL,URN의 차이](https://kotlinworld.com/96)
- [blog, URI, URL이란?](https://grape-blog.tistory.com/10)
