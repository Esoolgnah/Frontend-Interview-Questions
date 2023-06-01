# var, let, const의 차이점

- `var`는 변수 재선언, 재할당 모두 가능합니다. <br>
- `let`는 변수 재선언은 불가능, 재할당은 가능합니다. <br>
- `const`는 변수 재선언, 재할당 모두 불가능합니다. <br>
- `var`는 [`function-scoped`](#gear-function-scoped)이고, `let`, `const`는 [`block-scoped`](#gear-block-scoped)입니다.

<br>

### var의 재선언, 재할당이 가능하기 때문에 생긴 문제점
```js
// 이미 만들어진 변수이름으로 재선언했는데 아무런 문제가 발생하지 않습니다.
var a = 'test'
var a = 'test2'

// hoisting으로 인해 ReferenceError에러가 나지 않습니다.
c = 'test'
var c
```

### es2015에 추가된 let, const는?
```js
// let
let a = 'test'
let a = 'test2' // Uncaught SyntaxError: Identifier 'a' has already been declared
a = 'test3'     // 가능

// const
const b = 'test'
const b = 'test2' // Uncaught SyntaxError: Identifier 'b' has already been declared
b = 'test3'    // Uncaught TypeError:Assignment to constant variable.
```

<br>

---

<br>

## :hammer_and_wrench: 용어 공부

### :gear: function-scoped
- `var`는 `function-scoped`이기 때문에 for문이 끝난다음에 j를 호출하면 값이 출력이 잘 됩니다.
- 그 이유는 `var`가 [`hoisting`](https://github.com/Esoolgnah/Frontend-Interview-Questions/blob/main/Notes/important-5/hoisting.md)이 되었기 때문입니다.

```js
for(var j = 0; j < 10; j++) {
  console.log('j', j)
}
console.log('after loop j is ', j) // after loop j is 10


// 아래의 경우에는 에러가 발생합니다.
function counter () {
  for(var i = 0; i < 10; i++) {
    console.log('i', i)
  }
}
counter()
console.log('after loop i is', i) // ReferenceError: i is not defined
```

- `function scope`는 함수 내부 스코프를 의미하며 함수 내부에서 선언된 변수는 함수 내부에서만 접근이 가능합니다.
```js
function sayHi () {
  const hi = 'Hi there!'
  console.log(hi)
}

sayHi() // 'Hi there!'
console.log(hi) // Error, hi is not defined
```
- `function scope`에서 다른 함수를 호출할 수 있지만, 다른 함수 내부에서 선언된 내부 변수에는 접근이 불가합니다.
```js
function first () {
  const firstFunctionVariable = `I'm part of first`
}

function second () {
  first() // It works
  console.log(firstFunctionVariable) // Error, firstFunctionVariable is not defined
}
```

### :gear: block-scoped

`var`가 `function-scoped`로 `hoisting`이 되었다면

`let`, `const`는 `block-scoped`단위로 `hoisting`이 일어납니다.


### Block Scope
중괄호({}) 내부에서 let, const 변수를 선언하면 그 변수들은 중괄호 내부에서만 접근이 가능합니다. <br>
함수도 중괄호로 선언되므로 block scope도 function scope의 부분집합이라고 할 수 있습니다.
```js
{
  const hi = 'Hi there!'
  console.log(hi) // 'Hi there!'
}

console.log(hi) // Error, hi is not defined
```

<br>

<br>

```js
c = 'test' // ReferenceError: c is not defined
let c
```

위의 코드에서 ReferenceError가 발생한 이유는 [tdz](#gear-tdz)(temporal dead zone)때문입니다. <br>

`let`은 값을 할당하기전에 변수가 선언 되어있어야 하는데 그렇지 않기 때문에 에러가 납니다. <br>

이건 `const`도 마찬가지인데 좀 더 엄격합니다.

```js
// let은 선언하고 나중에 값을 할당이 가능하지만
let dd
dd = 'test'

// const 선언과 동시에 값을 할당 해야합니다.
const aa // Missing initializer in const declaration
```
이렇게 javascript에 tdz가 필요한 이유는 동적언어이다보니 runtime type check 가 필요해서입니다.

<br>

### :gear: tdz
- TDZ(Temporal Dead Zone) 란, 한글로 직역하자면 일시적인 사각지대란 뜻입니다. <br> 이 일시적인 사각지대는 스코프의 시작 지점부터 초기화 시작 지점까지의 구간을 TDZ(Temporal Dead Zone) 라고합니다.

<br>

## 참고

- [Github, var,let,const 차이점은?](https://gist.github.com/LeoHeo/7c2a2a6dbcf80becaaa1e61e90091e5d)
- [blog, 함수 스코프, 블록 스코프, 렉시컬 스코프](https://velog.io/@iwaskorean/JavaScript-33%EA%B0%80%EC%A7%80-%EA%B0%9C%EB%85%90-6.-Function-Scope-Block-Scope-and-Lexical-Scope%ED%95%A8%EC%88%98-%EC%8A%A4%EC%BD%94%ED%94%84-%EB%B8%94%EB%A1%9D-%EC%8A%A4%EC%BD%94%ED%94%84-%EB%A0%89%EC%8B%9C%EC%BB%AC-%EC%8A%A4%EC%BD%94%ED%94%84)
- [blog, TDZ이란?](https://noogoonaa.tistory.com/78)

