# JavaScript는 어떤 언어일까?

JavaScript는 `싱글 스레드`이면서 `논 블록킹` 언어입니다.

> ### 싱글 스레드 논 블록킹
>
> - 자바스크립트는 비동기 처리를 통해 싱글 스레드이지만 블록킹 되지 않게 합니다.
>   하나의 요청이 완료될 때까지 기다리지 않고 동시에 다른 작업을 수행함으로써 문제를 해결합니다.

> ### 싱글 스레드
>
> - 스레드가 하나밖에 존재하지 않아 한번에 하나의 작업만 할 수 있습니다.

> ### 스레드
>
> - 어떠한 프로그램 내에서, 특히 프로세스 내에서 실행되는 흐름의 단위를 말합니다.

> ### 비동기 처리
>
> - 특정 로직의 실행이 끝날때까지 기다려주지 않고 나머지 코드를 먼저 실행하는 것입니다.
>   멀티 스레드가 아닌 이유는 동시성 문제(동시에 공유된 자원에 접근하는 경우)를 해결하기 까다롭기 때문입니다.

<br>

## 자바스크립트에서 비동기적으로 코딩하기

> ### Promise
>
> - 비동기 작업이 맞이할 미래의 완료 또는 실패와 그 결과 값입니다.
>   쉽게 말해 비동기 작업의 결과라고 생각하면 됩니다.

### [콜백](#gear-콜백) 함수

> 주의! 콜백 지옥에 빠지게 될 수도 있다는 단점이 존재합니다.

### Promise

- `.then`: `promise`가 처리될 때까지 대기합니다.

### `async`/`await`

- `async`: 해당 함수는 항상 `promise`를 반환합니다.
- `await`: `promise`가 처리될 때까지 대기합니다.

> 비동기 처리가 필요한 이유: https://velog.io/@dev-katrina/%EB%B9%84%EB%8F%99%EA%B8%B0

### 자바스크립트 동작 원리([이벤트 루프](#gear-이벤트루프)(Event Loop))

<img src="../../images/important-4/javascript.gif" width="600px">

- gif 출처: https://beomy.github.io/tech/javascript/javascript-runtime/

> - 일반적인 작업은 [콜스택](#gear-콜스택)(Call Stack)에서 이루어집니다.
> - 시간이 소요되는 작업들(setTimeout, 이벤트, HTTP 요청 메서드 등)은 [WebAPI](#gear-webapi)에서 대기하다가 [콜백큐](#gear-콜백큐)(Callback Queue)로 보내집니다.
> - Call Stack이 비워져 있을때만 Callback Queue에 저장되어있던 작업들을 Call Stack으로 보냅니다.

<br>

---

<br>

## :hammer_and_wrench: 용어 공부

### :gear: 콜백

- 함수가 끝나고 난 뒤에 실행되는 함수입니다. 자바스크립트에서 함수는 객체입니다. 따라서 함수는 함수를 인자로 받고 다른 함수를 통해 반환될 수 있습니다. 인자로 대입되는 함수를 콜백함수라고 부릅니다.

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

- [blog, 프론트엔드 면접 문제 은행](https://velog.io/@wkahd01/%ED%94%84%EB%A1%A0%ED%8A%B8%EC%97%94%EB%93%9C-%EB%A9%B4%EC%A0%91-%EB%AC%B8%EC%A0%9C-%EC%9D%80%ED%96%89-HTML-%EC%A7%88%EB%AC%B8-%EB%8B%B5%EB%B3%80#javascript%EB%8A%94-%EB%AC%B4%EC%8A%A8-%EC%96%B8%EC%96%B4%EC%9D%B8%EA%B0%80)
- [blog, 콜백이란 무엇인가?](https://medium.com/@flqjsl/%EC%BD%9C%EB%B0%B1%EC%9D%B4%EB%9E%80-%EB%AC%B4%EC%97%87%EC%9D%B8%EA%B0%80-56c26e1f1bc3)
- [blog, 이벤트 루프란?](https://intrepidgeeks.com/tutorial/javascript-what-is-an-active-loop)
