# 클로저(Closure)란?

함수와 함수가 선언된 어휘적 환경의 조합입니다.(MDN 정의) 또한 **함수가 속한 [렉시컬스코프](#gear-렉시컬스코프)를 기억하여 함수가 렉시컬 스코프 밖에서 실행될 때도 그 스코프에 접근할 수 있게 하는 기능** 을 말합니다.

```javascript
function outer() {
  var a = 2;
  function inner() {
    console.log(a);
  }
  return inner;
}
var func = outer();
func(); // 2
```

여기서 GC([GarbageCollector](#gear-garbagecollector))가 `outer()` 의 참조를 없앨 것 같지만 내부함수인 `inner()` 가 해당 스코프의 변수인 a를 참조하고 있기 때문에 없애지 않습니다. 따라서 스코프 외부에서 `inner()` 가 실행되도 해당 스코프를 기억하기 때문에 2를 출력하게 됩니다. 즉, 여기서 클로저는 `inner()` 가 되며 `func` 에 담겨 밖에서도 실행되고 렉시컬 스코프를 기억합니다.

<br>

> 위의 코드와 같은 방식으로 자바스크립트에는 없는 캡슐화라는 개념을 구현할 수 있고 정보 은닉과 캡슐화가 가져다주는 이점들을 얻을 수 있습니다.

<br>

---

<br>

## :hammer_and_wrench: 용어 공부

### :gear: 렉시컬스코프

- 렉시컬 스코프는 함수를 어디서 호출하는지가 아니라 어디에 선언하였는지에 따라 결정됩니다. 자바스크립트는 렉시컬 스코프를 따르므로 함수를 선언한 시점에 상위 스코프가 결정됩니다. 함수를 어디에서 호출하였는지는 스코프 결정에 아무런 의미를 주지 않습니다.

### :gear: GarbageCollector

- 메모리에 할당된 값이 더는 필요하지 않다고 판단될때 메모리를 해제시키는 과정을 가비지 컬렉션이라고 부르며 이 역할을 가비지 컬렉터가 맡고 있습니다. 가비지 컬렉터가 ‘필요없다’라고 판단하는 기준은 더 이상 '객체에 닿을 수 없을 때'를 말합니다. 닿는다는 roots(전역 변수)를 기준으로 참조, 또는 참조의 참조의… 참조가 되는 객체들입니다. 이 알고리즘을 mark and sweep이라고 부르는데 가비지 컬렉터는 ‘root에서 닿을 수 있는’ 객체들의 reachable을 true로 표시하고, false인 객체들은 메모리에서 해제시킵니다.

<br>

## 참고

- [blog, 프론트엔드 면접 문제 은행 질문 답변](https://velog.io/@wkahd01/%ED%94%84%EB%A1%A0%ED%8A%B8%EC%97%94%EB%93%9C-%EB%A9%B4%EC%A0%91-%EB%AC%B8%EC%A0%9C-%EC%9D%80%ED%96%89-HTML-%EC%A7%88%EB%AC%B8-%EB%8B%B5%EB%B3%80)
- [Github, 클로저](https://github.com/baeharam/Must-Know-About-Frontend/blob/main/Notes/javascript/closure.md)
- [poiemaweb, scope](https://poiemaweb.com/js-scope)
- [[JS] Closure와 Garbage Collection](https://dkje.github.io/2020/09/18/Closure/)
