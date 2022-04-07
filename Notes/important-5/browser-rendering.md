# 브라우저의 렌더링 원리

브라우저가 화면에 나타나는 요소를 렌더링 할 때, 웹킷(Webkit)이나 게코(Gecko) 등과 같은 [렌더링엔진](#gear-렌더링엔진) 을 사용합니다. 렌더링 엔진이 HTML, CSS, Javascript로 렌더링할 때 [CRP](#gear-crp)라는 프로세스를 사용하며 다음 단계들로 이루어집니다.

<br>

1. **HTML를 [파싱](#gear-파싱) 후, [DOM](#gear-dom)트리를 구축합니다.**
2. **CSS를 파싱 후, [CSSOM](#gear-cssom)트리를 구축합니다.**
3. **Javascript를 실행합니다.**
   - 주의! HTML 중간에 스크립트가 있다면 HTML 파싱이 중단됩니다.
4. **DOM과 CSSOM을 조합하여 렌더트리(Render Tree) 구축합니다.**
   - 주의! `display: none` 속성과 같이 화면에서 보이지도 않고 공간을 차지하지 않는 것은 렌더트리로 구축되지 않습니다.
5. **뷰포트 기반으로 렌더트리의 각 노드가 가지는 정확한 위치와 크기 계산합니다. (Layout/Reflow 단계)**
6. **계산한 위치/크기를 기반으로 화면에 그립니다. (Paint 단계)**

<br>

---

<br>

## :hammer_and_wrench: 용어 공부

### :gear: 렌더링엔진

- 브라우저 마다 다르지만, 브라우저는 렌더링을 수행하는 렌더링 엔진을 가지고 있습니다. 크롬은 블링크(Blink), 사파리는 웹킷(Webkit) 그리고 파이어폭스는 게코(Gecko)라는 렌더링 엔진을 사용합니다.

### :gear: CRP

- CRP (Critical Rendering Path, 중요 렌더링 경로)는 브라우저가 HTML, CSS, Javascipt를 화면에 픽셀로 변화하는 일련의 단계를 말합니다. CRP는 Document Object Model (DOM), CSS Object Model (CSSOM), 렌더 트리 그리고 레이아웃을 포함합니다.

### :gear: 파싱

- 파싱은 하나의 프로그램을 런타임 환경(예를 들면, 브라우저 내 자바스크립트 엔진)이 실제로 실행할 수 있는 내부 포맷으로 분석하고 변환하는 것을 의미합니다. 즉, 파싱은 문서의 내용을 토큰(token)으로 분석하고, 문법적 의미와 구조를 반영한 파스 트리(parse tree)를 생성하는 과정입니다.

### :gear: DOM

- **DOM(Document Object Model)이란?** 웹 페이지를 이루는 태그들을 자바스크립트가 이용할 수 있게끔 브라우저가 트리구조로 만든 객체 모델을 의미합니다. 영어 뜻풀이 그대로 하자면 문서 객체 모델을 의미합니다. 문서 객체란 html, head, body와 같은 태그들을 javascript가 이용할 수 있는 (메모리에 보관할 수 있는) 객체를 의미합니다. DOM은 HTML과 스크립팅 언어(JavaScript)를 서로 이어주는 역할을 합니다.

### :gear: CSSOM

- **CSSOM(CSS Object Model)이란?** CSS 내용을 파싱하여 자료를 구조화 한 것을 CSSOM이라고 합니다. 즉 DOM처럼 CSS의 내용을 해석하고 노드를 만들어 트리 구조로 만든 것을 CSSOM이라 합니다.

<br>

## 참고

- [Medium, 브라우저의 렌더링 과정](https://github.com/baeharam/Must-Know-About-Frontend/blob/main/Notes/frontend/browser-rendering.md),
- [Github, 브라우저의 렌더링 원리](https://medium.com/%EA%B0%9C%EB%B0%9C%EC%9E%90%EC%9D%98%ED%92%88%EA%B2%A9/%EB%B8%8C%EB%9D%BC%EC%9A%B0%EC%A0%80%EC%9D%98-%EB%A0%8C%EB%8D%94%EB%A7%81-%EA%B3%BC%EC%A0%95-5c01c4158ce)
- [MDN Web Docs, 중요 렌더링 경로](https://developer.mozilla.org/ko/docs/Web/Performance/Critical_rendering_path)
- [Blog, 파싱이란? 파싱의 뜻은 무엇일까?(번역)](https://oneroomtable.tistory.com/entry/%ED%8C%8C%EC%8B%B1%EC%9D%B4%EB%9E%80-%EB%AC%B4%EC%97%87%EC%9D%BC%EA%B9%8C-%EB%B2%88%EC%97%AD)
- [Blog, DOM이란? 가상 돔 (Virtual DOM )이 나오게 된 이유](https://dev-cini.tistory.com/10)
- [Blog, CSSOM(CSS Object Model) 이란?](https://itworldyo.tistory.com/151)
