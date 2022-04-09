# 자바스크립트에서 비동기적으로 코딩하기

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

---

<br>

## :hammer_and_wrench: 용어 공부

### :gear: 콜백

- 함수가 끝나고 난 뒤에 실행되는 함수입니다. 자바스크립트에서 함수는 객체입니다. 따라서 함수는 함수를 인자로 받고 다른 함수를 통해 반환될 수 있습니다. 인자로 대입되는 함수를 콜백함수라고 부릅니다.

<br>

## 참고

- [blog, 프론트엔드 면접 문제 은행](https://velog.io/@wkahd01/%ED%94%84%EB%A1%A0%ED%8A%B8%EC%97%94%EB%93%9C-%EB%A9%B4%EC%A0%91-%EB%AC%B8%EC%A0%9C-%EC%9D%80%ED%96%89-HTML-%EC%A7%88%EB%AC%B8-%EB%8B%B5%EB%B3%80#%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8%EC%97%90%EC%84%9C-%EB%B9%84%EB%8F%99%EA%B8%B0%EC%A0%81%EC%9C%BC%EB%A1%9C-%EC%BD%94%EB%94%A9%ED%95%98%EA%B8%B0)
- [blog, 콜백이란 무엇인가?](https://medium.com/@flqjsl/%EC%BD%9C%EB%B0%B1%EC%9D%B4%EB%9E%80-%EB%AC%B4%EC%97%87%EC%9D%B8%EA%B0%80-56c26e1f1bc3)
