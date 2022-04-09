# 자바스크립트 동작 원리([이벤트 루프](#gear-이벤트루프)(Event Loop))

<img src="../../Images/important-4/javascript-eventloop.gif" width="600px">

- gif 출처: https://beomy.github.io/tech/javascript/javascript-runtime/

> - 일반적인 작업은 [콜스택](#gear-콜스택)(Call Stack)에서 이루어집니다.
> - 시간이 소요되는 작업들(setTimeout, 이벤트, HTTP 요청 메서드 등)은 [WebAPI](#gear-webapi)에서 대기하다가 [콜백큐](#gear-콜백큐)(Callback Queue)로 보내집니다.
> - Call Stack이 비워져 있을때만 Callback Queue에 저장되어있던 작업들을 Call Stack으로 보냅니다.

<br>

---

<br>

## :hammer_and_wrench: 용어 공부

### :gear: 이벤트루프

- 이벤트 루프(Event Loop)는 call stack이 다 비워지면 callback queue에 존재하는 함수를 하나씩 call stack으로 옮기는 역할을 합니다.

### :gear: 콜스택

- 콜스택(Call Stack)은 실행된 코드의 환경을 저장하는 자료구조로, 함수 호출 시 이곳에 저장됩니다. 어떤 함수를 저장하면 스택에 쌓고 또 다른 함수를 호출하면 그 다음 스택에 쌓이면서 가장 위에 쌓인 함수를 가장 먼저 처리합니다. LIFO(Last In First Out)

### :gear: webAPI

- Web API는 브라우저에서 제공하는 API로 DOM, Ajax, TimeOut 등이 있습니다. CallStack에서 실행된 비동기 함수는 Web API를 호출하고, Web API는 콜백 함수를 Task Queue에 넣습니다.

### :gear: 콜백큐

- 콜백큐(Callback Queue)는 함수를 저장하는 자료구조로, Call Stack과 다르게 가장 먼저 들어온 함수를 가장 먼저 처리합니다.

<br>

## 참고

- [blog, 프론트엔드 면접 문제 은행](https://velog.io/@wkahd01/%ED%94%84%EB%A1%A0%ED%8A%B8%EC%97%94%EB%93%9C-%EB%A9%B4%EC%A0%91-%EB%AC%B8%EC%A0%9C-%EC%9D%80%ED%96%89-HTML-%EC%A7%88%EB%AC%B8-%EB%8B%B5%EB%B3%80#%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8-%EB%8F%99%EC%9E%91-%EC%9B%90%EB%A6%AC%EC%9D%B4%EB%B2%A4%ED%8A%B8-%EB%A3%A8%ED%94%84)
- [blog, 이벤트 루프란?](https://intrepidgeeks.com/tutorial/javascript-what-is-an-active-loop)
