# 마이크로태스크 큐, 태스크 큐

<br>

2개의 큐 모두 [콜백함수](#gear-콜백함수)가 들어간다는 점에서 동일하지만 어떤 함수를 실행하느냐에 따라 어디로 들어가는지가 달라집니다. 또한 명칭은 큐 (Queue) 이지만 자료구조의 큐와는 다릅니다. 엄밀히 말하자면 [우선순위 큐](#gear-우선순위큐) (Priority Queue) 라고 할 수 있는데, 이벤트 루프가 2개의 큐에서 태스크를 꺼내는 조건이 “제일 오래된 태스크” 이기 때문입니다. ([`동작방식`](https://html.spec.whatwg.org/multipage/webappapis.html#task-queue))

<br>

- 콜백함수를 태스크 큐에 넣는 함수들

  - setTimeout, setInterval, setImmediate, requestAnimationFrame, I/O, UI 렌더링

- 콜백함수를 마이크로태스크 큐에 넣는 함수들

  - process.nextTick, Promise, Object.observe, MutationObserver

<br>

익숙한 함수인 Web API의 `setTimeout()` 의 콜백함수가 태스크 큐에 들어가고 `Promise` 의 콜백함수가 마이크로태스크 큐에 들어간다는 것을 알 수 있습니다. [이벤트 루프](https://github.com/Esoolgnah/Frontend-Interview-Questions/blob/main/Notes/important-4/event-loop.md)는 각 콜백함수를 태스크/마이크로태스크 큐에서 꺼내쓰는 것인데, 그렇다면 어떤게 먼저일까요?

<br>

결론부터 말씀드리자면, `마이크로태스크 큐가 먼저입니다.`

<br>

[이벤트 루프](https://github.com/Esoolgnah/Frontend-Interview-Questions/blob/main/Notes/important-4/event-loop.md)는 마이크로태스크 큐의 모든 태스크들을 처리한 다음, 태스크 큐의 태스크들을 처리합니다. 따라서 `Promise`의 콜백함수가 `setTimeout()`의 콜백함수보다 먼저 처리됩니다.

<br>

### 예시

```js
console.log('콜 스택!');
setTimeout(() => console.log('태스크 큐!'), 0);
Promise.resolve().then(() => console.log('마이크로태스크 큐!'));
```

<br>

### 결과

```
콜 스택!
마이크로태스크 큐!
태스크 큐!
```

---

<br>

## :hammer_and_wrench: 용어 공부

### :gear: 콜백함수

- 함수가 끝나고 난 뒤에 실행되는 함수입니다. 자바스크립트에서 함수는 객체입니다. 따라서 함수는 함수를 인자로 받고 다른 함수를 통해 반환될 수 있습니다. 인자로 대입되는 함수를 콜백함수라고 부릅니다.

### :gear: 우선순위큐

- 우선순위 큐(Priority Queue)는 먼저 들어오는 데이터가 아니라, 우선순위가 높은 데이터가 먼저 나가는 형태의 자료구조입니다. 일반적으로 힙(Heap)을 이용하여 구현합니다.

<br>

## 참고

- [blog, Task와 Microtask의 동작방식](https://baeharam.netlify.app/posts/javascript/JS-Task%EC%99%80-Microtask%EC%9D%98-%EB%8F%99%EC%9E%91%EB%B0%A9%EC%8B%9D)
- [blog, 콜백이란 무엇인가?](https://medium.com/@flqjsl/%EC%BD%9C%EB%B0%B1%EC%9D%B4%EB%9E%80-%EB%AC%B4%EC%97%87%EC%9D%B8%EA%B0%80-56c26e1f1bc3)
- [blog, [자료구조] 우선순위 큐와 힙 (Priority Queue & Heap)](https://suyeon96.tistory.com/31)
