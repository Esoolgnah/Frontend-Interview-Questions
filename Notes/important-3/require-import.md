# require와 import의 차이점

- `require`는 [CommonJS](#gear-commonjs)를 사용하는 node.js문이지만 `import`는 ES6에서만 사용됩니다.
- `require`는 파일(non-lexical,비어휘적)에 저장된 위치에 남아 있으며 `import`는 항상 맨 위로 이동합니다.
- `require`는 프로그램의 어느 지점에서나 호출 할 수 있지만 `import`는 파일의 시작 부분에서만 실행할 수 있습니다. (하지만 import전용 비동기 문법으로 처리 가능)
- 일반적으로 `import`는 사용자가 필요한 모듈 부분만 선택하고 로드 할 수 있기 때문에 더 선호됩니다. 이 명령문은 `require`보다 성능이 우수하며 메모리를 절약합니다.

<br>

<br>

> 기본적으로 require와 import는 모듈 키워드입니다. 외부 파일이나 라이브러리를 불러올 때 사용합니다.
> `require`는 NodeJS에서 사용되고 있는 CommonJS 키워드이고, `import`는 ES6(ES2015)에서 새롭게 도입된 키워드입니다.
> <br>
>
> ```javascript
> const moment = require('moment');
> ```
>
> CommonJS 방식을 따른 첫번째 코드는 Ruby처럼 require 키워드를 사용하여 여타 다른 변수를 할당하듯이 모듈을 불러오는 반면에,
> <br>
>
> ```js
> import moment from 'moment';
> ```
>
> ES6 방식을 따른 두번째 코드는 Java나 Python처럼 import 키워드를 사용하여 좀 더 명시적으로 모듈을 불러오고 있습니다.
> <br>
> 최근 ES6(ES2015) 모듈 시스템인 `import` 가 많이 사용되고 있지만, 그러나 아직까지는 `import` 키워드가 100% 대체되어 사용될 수 없습니다.
> <br>
> Babel과 같은 ES6 코드를 변환(transpile)해주는 도구를 사용할 수 없는 경우에는 `require` 키워드를 사용해야 합니다.

<br>

---

<br>

## :hammer_and_wrench: 용어 공부

### :gear: CommonJS

CommonJS 란? 웹 브라우저 밖의 자바스크립트를 위한 모듈 생태계의 규칙을 설립하기 위한 프로젝트입니다.
<br>
개념은 간단합니다. `'.js'` 파일 간의 어떻게 의존성을 가지게 할지 정해주는 것입니다. commonJS라는 개념이 존재하는 이유는 자바스크립트를 범용적으로 모듈화를 높이기 위해서입니다.

<br>

## 참고

- [require ⚔️ import (CommonJs와 ES6) 차이](https://inpa.tistory.com/entry/NODE-%F0%9F%93%9A-require-%E2%9A%94%EF%B8%8F-import-CommonJs%EC%99%80-ES6-%EC%B0%A8%EC%9D%B4-1)
- [Server & Node [CommonJS]](https://velog.io/@sksgur3217/Server-Node-CommonJS)
