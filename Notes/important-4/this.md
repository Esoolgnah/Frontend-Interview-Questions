# this의 용법

this는 호출 패턴에 따라 다른 객체를 참조합니다. 실행 컨텍스트([EC](#gear-ec))가 생성될 때마다 this의 [바인딩](#gear-바인딩)이 일어나며 우선순위 순으로 나열해보면 다음과 같습니다.

<br>

1. [`new`](#gear-new) 를 사용했을 때 해당 객체로 바인딩됩니다.

```javascript
var name = 'global';
function Func() {
  this.name = 'Func';
  this.print = function f() {
    console.log(this.name);
  };
}
var a = new Func();
a.print(); // Func
```

2. [`call`](#gear-call), [`apply`](#gear-apply), [`bind`](#gear-bind) 와 같은 명시적 바인딩을 사용했을 때 인자로 전달된 객체에 바인딩됩니다.

```javascript
function func() {
  console.log(this.name);
}
var obj = { name: 'obj name' };
func.call(obj); // obj name
func.apply(obj); // obj name
func.bind(obj)(); // obj name
```

3. 객체의 메소드로 호출할 경우 해당 객체에 바인딩됩니다.

```javascript
var obj = {
  name: 'obj name',
  print: function p() {
    console.log(this.name);
  },
};
obj.print(); // obj name
```

4. 그 외의 경우

- strict mode(엄격 모드): `undefined` 로 초기화됩니다.
- 일반: 브라우저라면 `window` 객체에 바인딩됩니다.

<br>

---

<br>

## :hammer_and_wrench: 용어 공부

### :gear: 바인딩

- 바인딩(Binding) 이란 프로그램의 어떤 기본 단위가 가질 수 있는 구성요소의 구체적인 값, 성격을 확정하는 것을 말합니다.

### :gear: EC

- EC는 실행 컨텍스트(Execution Context)의 약자이며 scope, hoisting, this, function, closure 등의 동작원리를 담고 있는 자바스크립트의 핵심원리입니다.

### :gear: new

- new라는 기호는 자바스크립트의 고유의 예약어이며 고유의 연산자(operator) 입니다. 아래는 자바스크립트의 new라는 연산자(operator)에 대한 정의 입니다.

> new 연산자는 사용자 정의 객체 타입 또는 내장 객체 타입의 인스턴스를 생성한다.

### :gear: call

- call을 사용하면 함수를 실행하고 함수의 첫 번째 인자로 전달하는 값에 this를 바인딩합니다.

### :gear: apply

- call과 마찬가지로 apply를 사용하면 함수를 실행하고 함수의 첫 번째 인자로 전달하는 값에 this를 바인딩합니다. call과의 차이점은 인자를 배열의 형태로 전달한다는 것입니다. 이 때, 인자로 배열 자체가 전달되는 것이 아니라, 배열의 요소들이 값으로 전달됩니다.

### :gear: bind

- bind는 함수의 첫 번째 인자에 this를 바인딩한다는 점은 같지만, 함수를 실행하지 않으며 새로운 함수를 반환합니다. 즉 반환된 새로운 함수를 실행해야 원본 함수가 실행됩니다.

<br>

## 참고

- [blog, this의 모든 것](https://samsara1019.tistory.com/75)
- [Github, this의 바인딩](https://github.com/baeharam/Must-Know-About-Frontend/blob/main/Notes/javascript/this.md)
- [poiemaweb, 실행 컨텍스트](https://poiemaweb.com/js-execution-context)
- [blog, 바인딩(Binding)](https://medium.com/pocs/%EB%B0%94%EC%9D%B8%EB%94%A9-binding-4a4a2f641b27)
- [blog, 자바스크립트 new연산자](https://lts0606.tistory.com/448)
- [blog, 자바스크립트 call,apply,bind ](https://oneroomtable.tistory.com/entry/%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8-call-apply-bind-%EC%84%A4%EB%AA%85)
