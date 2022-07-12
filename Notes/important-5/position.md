# CSS에서 position이란?

position 속성은 문서 상에 요소를 배치하는 방법을 지정합니다.

- `static`: 요소를 일반적인 문서 흐름에 따라 배치합니다.

- `relative`: `static` + 자신을 기준으로 `top`, `right`, `bottom`, `left`의 값에 따라 [오프셋](#gear-오프셋)을 적용합니다.

- `absolute`: 요소를 일반적인 문서 흐름에서 제거하고, 가장 가까운 위치 지정 조상 요소에 대해 상대적으로 배치합니다.

- `fixed`: 요소를 일반적인 문서 흐름에서 제거하고, [뷰포트](#gear-뷰포트)의 초기 [컨테이닝블록](#gear-컨테이닝블록)을 기준으로 삼아 배치합니다. => 바뀌지 않는 위치에 지정

- `sticky`: `static` + `fixed` 특징을 동시에 가집니다.

<br>

---

<br>

## :hammer_and_wrench: 용어 공부

### :gear: 오프셋

- 오프셋(offset)이란 `top`, `left`, `right`, `bottom` 값을 의미하고 기준이 되는곳으로부터 얼마만큼 떨어져있는지를 나타내기 위해 필요한 속성입니다.

### :gear: 뷰포트

- 뷰포트(viewport)는 화면에서 실제 내용이 표시되는 영역으로, 데스크톱은 사용자가 설정한 해상도가 뷰포트 영역이 되고, 스마트 기기는 기본으로 설정되어 있는 값이 뷰포트 영역이 됩니다.

### :gear: 컨테이닝블록

- 컨테이닝 블록이란 요소의 위치와 크기를 지정하는 데 사용하는 블록을 의미합니다. 상대적인 값이나, 요소의 위치를 지정하는 기준이 필요할 때 사용한다는 의미힙니다.

<br>

## 참고

- [blog, 프론트엔드 면접 문제 은행 질문 답변](https://velog.io/@wkahd01/%ED%94%84%EB%A1%A0%ED%8A%B8%EC%97%94%EB%93%9C-%EB%A9%B4%EC%A0%91-%EB%AC%B8%EC%A0%9C-%EC%9D%80%ED%96%89-HTML-%EC%A7%88%EB%AC%B8-%EB%8B%B5%EB%B3%80)
- [blog, CSS Position](https://mingeesuh.tistory.com/3)
- [blog, 뷰포트 (viewport)](https://masssal.tistory.com/34)
- [blog, 컨테이닝 블록](https://velog.io/@1-blue/%EC%BB%A8%ED%85%8C%EC%9D%B4%EB%8B%9D-%EB%B8%94%EB%A1%9D)
