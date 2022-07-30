# Reflow와 Repaint가 실행되는 시점

<br>

### [Reflow](#gear-Reflow)

- DOM 엘리먼트 추가, 제거 또는 변경
- CSS 스타일 추가, 제거 또는 변경
- CSS 스타일을 직접 변경하거나, 클래스를 추가함으로써 레이아웃이 변경될 수 있습니다. 엘리먼트의 길이를 변경하면, DOM 트리에 있는 다른 노드에 영향을 줄 수 있습니다.
- CSS3 애니메이션과 트랜지션. 애니메이션의 모든 프레임에서 리플로우가 발생합니다.
- offsetWidth 와 offsetHeight 의 사용. offsetWidth 와 offsetHeight 속성을 읽으면, 초기 리플로우가 트리거되어 수치가 계산됩니다.
- 유저 행동. 유저 인터랙션으로 발생하는 hover 효과, 필드에 텍스트 입력, 창 크기 조정, 글꼴 크기 변경, 스타일시트 또는 글꼴 전환등을 활성화하여 리플로우를 트리거할 수 있습니다.

### [Repaint](#gear-Repaint)

- 가시성이 변경되는 순간 (opacity, background-color, visibility, outline)
- Reflow 가 실행된 순간 뒤에 실행됩니다.

---

<br>

## :hammer_and_wrench: 용어 공부

### :gear: Reflow

- 생성된 DOM 노드의 레이아웃 수치(너비, 높이, 위치 등) 변경 시 영향 받은 모든 노드의(자신, 자식, 부모, 조상(결국 모든 노드) ) 수치를 다시 계산하여(Recalculate), 렌더 트리를 재생성하는 과정이며 또한, Reflow 과정이 끝난 후 재 생성된 렌더 트리를 다시 그리게 되는데 이 과정을 Reflow 라 합니다.

### :gear: Repaint

- Reflow 과정이 끝난 후 재 생성된 렌더 트리를 다시 그리게 되는데 이 과정을 Repaint 라 합니다.

<br>

## 참고

- [github, Reflow & Repaint](https://k0102575.github.io/articles/2020-11/reflow-repaint)
