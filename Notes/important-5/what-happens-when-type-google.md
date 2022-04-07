# 주소창에 google.com을 입력하면 일어나는 일

1. **사용자가 웹 브라우저를 통해 google.com 을 입력하면 URL 주소 중 도메인 네임 부분을 [DNS](#gear-dns) 서버에서 검색합니다.**
2. **DNS 서버에서 해당 도메인 네임에 해당하는 IP 주소를 찾아 사용자가 입력한 [URL](#gear-url) 정보와 함께 전달합니다.**
3. **브라우저는 [HTTP](#gear-http) [프로토콜](#gear-프로토콜)을 사용하여 요청 메시지를 생성하고 HTTP 요청 메시지는 [TCP](#gear-tcp)/[IP](#gear-ip) 프로토콜을 사용하여 서버로 전송됩니다.**
4. **서버는 [response](#gear-response) 메시지를 생성하여 다시 브라우저에게 데이터를 전송합니다.**
5. **브라우저는 response를 받아 [파싱](#gear-파싱)하여 화면에 [렌더링](#gear-렌더링)합니다.**

<br>

---

<br>

## :hammer_and_wrench: 용어 공부

### :gear: DNS

- 도메인 이름 시스템(DNS)은 사람이 읽을 수 있는 도메인 이름(예: www.amazon.com )을 머신이 읽을 수 있는 IP 주소(예: 192.0.2.44)로 변환합니다. 모든 통신에는 주소가 필요합니다. 출발지와 도착지의 주소를 알아야 통신을 할 수 있습니다. 우리는 이 주소를 IP라고 부릅니다. IP 주소로 변환하는 과정에 개입하는 것이 DNS 입니다.

### :gear: URL

- URL(Uniform Resource Locator)은 통합 자원 지시자로 인터넷의 리소스를 가리키는 표준 명칭으로 서버의 자원을 요청할 때 사용됩니다. URL을 통해 인터넷 상의 모든 리소스를 요청할 수 있으며, HTTP, FTP 등의 자원 요청도 가능합니다.

### :gear: HTTP

- HTTP(HyperText Transfer Protocol)은 TCP 기반의 클라이언트와 서버 사이에 이루어지는 요청/응답 프로토콜입니다. HTTP는 Text Protocol로 사람이 쉽게 읽고 쓸 수 있습니다. 프로토콜 설계상 클라이언트가 요청을 보내면 반드시 응답을 받아야 합니다. 응답을 받아야 다음 request를 보낼 수 있습니다.

### :gear: 프로토콜

- 프로토콜은 통신하기 위한 약속들을 기술적으로 잘 정의해 둔 것입니다. 데이터를 송수신하는 순서와 내용을 결정합니다. HTTP, TCP/IP, UDP 모두 프로토콜입니다.

### :gear: TCP

- TCP (전송 제어 프로토콜)은 두 개의 호스트를 연결하고 데이터 스트림을 교환하게 해주는 중요한 네트워크 프로토콜입니다. TCP는 데이터 전송을 제어하고 데이터를 어떻게 보낼 지, 어떻게 맞출 지 정합니다. 또한 데이터와 패킷이 보내진 순서대로 전달하는 것을 보장해줍니다.신뢰성과 연결성을 책임지기 위한 프로토콜이 TCP입니다. 호스트와 호스트간의 데이터 전송은 IP(인터넷 계층 프로토콜)에 의지하면서 동시에 신뢰성 있는 전송에 대해서는 TCP가 책임지는 구조입니다.

### :gear: IP

- IP (Internet Protocol)은 비신뢰성, 비연결지향 데이터그램 프로토콜로 패킷을 받아서 주소를 해석하고 경로를 결정하여 다음 호스트로 전송하는 역할을 합니다.

### :gear: response

- HTTP 메시지는 서버와 클라이언트 간에 데이터가 교환되는 방식입니다. 메시지 타입은 두 가지가 있습니다. 요청(request)은 클라이언트가 서버로 전달해서 서버의 액션이 일어나게끔 하는 메시지고, 응답(response)은 요청에 대한 서버의 답변입니다.

### :gear: 파싱

- 파싱은 하나의 프로그램을 런타임 환경(예를 들면, 브라우저 내 자바스크립트 엔진)이 실제로 실행할 수 있는 내부 포맷으로 분석하고 변환하는 것을 의미합니다. 즉, 파싱은 문서의 내용을 토큰(token)으로 분석하고, 문법적 의미와 구조를 반영한 파스 트리(parse tree)를 생성하는 과정입니다.

<br>

## 참고

- [blog, [네트워크]google.com을 입력하면 일어나는 일](https://bohyeon-n.github.io/deploy/network/internet-2.html)
- [AWS, DNS란 무엇입니까?](https://aws.amazon.com/ko/route53/what-is-dns/)
- [blog, URL이란](https://velog.io/@mer1-97/URL%EC%9D%B4%EB%9E%80)
- [mdn web docs, HTTP](https://developer.mozilla.org/ko/docs/Web/HTTP/Overview)
- [mdn web docs, 프로토콜](https://developer.mozilla.org/ko/docs/Glossary/Protocol)
- [mdn web docs, TCP](https://developer.mozilla.org/ko/docs/Glossary/TCP)
- [Blog, 파싱이란? 파싱의 뜻은 무엇일까?(번역)](https://oneroomtable.tistory.com/entry/%ED%8C%8C%EC%8B%B1%EC%9D%B4%EB%9E%80-%EB%AC%B4%EC%97%87%EC%9D%BC%EA%B9%8C-%EB%B2%88%EC%97%AD)
