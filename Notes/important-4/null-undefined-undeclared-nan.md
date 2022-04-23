# null, undefined, undeclared, NaN

## null

- 빈 값
- null이라는 빈 값을 할당했을 때, 생기는 타입입니다.

## undefined

- 정의되지 않음
- `var` 선언문의 경우, 호이스팅 되었을 때, 변수 선언과 초기화가 동시에 일어나기 때문에, 변수가 `undefined` 됩니다.(타입 결정 안됨)

```js
console.log(data); // undefined
const data = 'data';
```

## undeclared

- 선언되지 않음
- `let`, `const` 선언문의 경우, [호이스팅](#gear-호이스팅) 되었을 때, 변수 선언과 초기화가 따로 이루어지기에, 변수가 `undeclared`되어 에러가 생깁니다.

```js
console.log(data); // error
let data = 'data';
```

## NaN

- 표현 불가능한 수치형 결과입니다.

```js
typeof 1 / 0; // NaN
```

<br>

---

<br>

## :hammer_and_wrench: 용어 공부

### :gear: 호이스팅

- 호이스팅이란 "끌어올린다" 라는 뜻으로 **변수 및 함수 선언문이 스코프 내의 최상단으로 끌어올려지는 현상** 을 말합니다. 여기서 주의할 점은 **"선언문"** 이라는 것이며 "대입문"은 끌어올려지지 않습니다. ([호이스팅이란? 글 보러가기](https://github.com/Esoolgnah/Frontend-Interview-Questions/blob/main/Notes/important-5/hoisting.md))
  <br>

## 참고

- [blog, 프론트엔드 면접 문제 은행](https://velog.io/@wkahd01/%ED%94%84%EB%A1%A0%ED%8A%B8%EC%97%94%EB%93%9C-%EB%A9%B4%EC%A0%91-%EB%AC%B8%EC%A0%9C-%EC%9D%80%ED%96%89-HTML-%EC%A7%88%EB%AC%B8-%EB%8B%B5%EB%B3%80#null-undefined-undeclared-nan)
- [github, 호이스팅이란?](https://github.com/Esoolgnah/Frontend-Interview-Questions/blob/main/Notes/important-5/hoisting.md)
