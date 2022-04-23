# HTML 렌더링 중에 JavaScript가 실행되면 렌더링이 멈추는 이유

렌더링 엔진은 HTML 한 줄씩 순차적으로 [파싱](#gear-파싱)하며 [DOM](#gear-dom)을 생성해 나가다가 JavaScript를 만나면 DOM 생성을 임시 중단합니다.

DOM 생성을 임시 중단하고, 자바스크립트 코드를 파싱하기 위해 자바스크립트 엔진에 제어권을 넘기게 되는데, 파싱이 끝나면 다시 렌더링 엔진에 제어권을 넘겨 중단된 부분부터 HTML 파싱을 재개하며 DOM 트리를 생성합니다.

<br>

---

<br>

## :hammer_and_wrench: 용어 공부

### :gear: 파싱

- 파싱은 하나의 프로그램을 런타임 환경(예를 들면, 브라우저 내 자바스크립트 엔진)이 실제로 실행할 수 있는 내부 포맷으로 분석하고 변환하는 것을 의미합니다. 즉, 파싱은 문서의 내용을 토큰(token)으로 분석하고, 문법적 의미와 구조를 반영한 파스 트리(parse tree)를 생성하는 과정입니다.

### :gear: DOM

- **DOM(Document Object Model)이란?** 웹 페이지를 이루는 태그들을 자바스크립트가 이용할 수 있게끔 브라우저가 트리구조로 만든 객체 모델을 의미합니다. 영어 뜻풀이 그대로 하자면 문서 객체 모델을 의미합니다. 문서 객체란 html, head, body와 같은 태그들을 javascript가 이용할 수 있는 (메모리에 보관할 수 있는) 객체를 의미합니다. DOM은 HTML과 스크립팅 언어(JavaScript)를 서로 이어주는 역할을 합니다.

<br>

## 참고

- [blog, 프론트엔드 면접 문제 은행](https://velog.io/@wkahd01/%ED%94%84%EB%A1%A0%ED%8A%B8%EC%97%94%EB%93%9C-%EB%A9%B4%EC%A0%91-%EB%AC%B8%EC%A0%9C-%EC%9D%80%ED%96%89-HTML-%EC%A7%88%EB%AC%B8-%EB%8B%B5%EB%B3%80#html-%EB%A0%8C%EB%8D%94%EB%A7%81-%EC%A4%91%EC%97%90-javascript%EA%B0%80-%EC%8B%A4%ED%96%89%EB%90%98%EB%A9%B4-%EB%A0%8C%EB%8D%94%EB%A7%81%EC%9D%B4-%EB%A9%88%EC%B6%94%EB%8A%94-%EC%9D%B4%EC%9C%A0)
- [Blog, 파싱이란? 파싱의 뜻은 무엇일까?(번역)](https://oneroomtable.tistory.com/entry/%ED%8C%8C%EC%8B%B1%EC%9D%B4%EB%9E%80-%EB%AC%B4%EC%97%87%EC%9D%BC%EA%B9%8C-%EB%B2%88%EC%97%AD)
- [Blog, DOM이란? 가상 돔 (Virtual DOM )이 나오게 된 이유](https://dev-cini.tistory.com/10)
