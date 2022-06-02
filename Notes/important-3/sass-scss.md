# sass(scss)의 장점(특징)

## 1. 변수 사용가능

선언방법
변수 타입 : `숫자, 문자열, 색상, boolean, null, lists, maps`

```scss
$변수명: 속성값;
```

## 2. 수학 연산자 사용가능

사용가능 연산자 : `+, -, /, *, %, ==, !=`

> ### 주의
>
> `+, -` 연산시에는 단위 통일 <br> `나눔기호` 사용시에는 괄호로 묶어서 사용

## 3. Nesting 기능

중첩해서 선언하기 가능

```css
/* CSS */
.container {
  width: 100%;
}

.container h1 {
  color: red;
}
```

```scss
/* Sass */
.container {
  width: 100%;
  h1 {
    color: red;
  }
}
```

상위요소 참조시에는 & 문자 사용

```css
a {
  color: black;
}
a:hover {
  text-decoration: underline;
  color: gray;
}
a:visited {
  color: purple;
}

.widget {
  font-weight: 400;
}
.widget-area {
  font-weight: 600;
}
.widget-top_posts {
  font-weight: 1000;
}
```

```scss
/* Sass */

a {
  color: black;
  &:hover {
    text-decoration: underline;
    color: gray;
  }
  &:visited {
    color: purple;
  }
}

.widget {
  font-weight: 400;
  &-area {
    font-weight: 600;
  }
  &-top_posts {
    font-weight: 1000;
  }
}
```

## 4. `import`와 `extend`

`@import` 지시어를 사용해서 다른 scss 파일을 import할 수 있다

`@extend` 지시어를 사용하여 특정 선택자의 속성을 상속받을 수 있다

```css
.box,
.success-box {
  border: 1px solid gray;
  padding: 10px;
  display: inline-block;
}

.success-box {
  border: 1px solid green;
}
```

```scss
/* Sass */
.box {
  border: 1px solid gray;
  padding: 10px;
  display: inline-block;
}

.success-box {
  @extend .box;
  border: 1px solid green;
}
```

`Placeholder` 선택자 %를 사용하면 상속은 하면서 해당 선택자는 컴파일 X

```scss
/* SASS */
%box {
  padding: 0.5em;
}

.success-box {
  @extend %box;
  color: green;
}

.error-box {
  @extend %box;
  color: red;
}
```

```css
/* CSS */
.success-box,
.error-box {
  padding: 0.5em;
}

.success-box {
  color: green;
}

.error-box {
  color: red;
}
```

## 6. 믹스인(Mixin)

공통적으로 쓰이는 css 속성들을 묶어서 재사용이 가능하게 하는 기능

`parameter`를 받을 수 있다

선언 `@mixin`

사용 `@include`

```scss
/* SASS */
@mixin headline($color, $size) {
  color: $color;
  font-size: $size;
}

h1 {
  @include headline(green, 12px);
}

// 인자에 default값 적용
@mixin headline($color: #eee, $size: 10px) {
  width: 50px;
}
```

```css
/* CSS */
h1 {
  color: green;
  font-size: 12px;
}
```

```scss
/* SASS */

@mixin media($queryString) {
  @media #{$queryString} {
    @content;
  }
}

.container {
  width: 900px;
  @include media('(max-width: 767px)') {
    width: 100%;
  }
}
```

```css
/* CSS */
.container {
  width: 900px;
}
@media (max-width: 767px) {
  .container {
    width: 100%;
  }
}
```

## 7. 커스텀 함수 사용

함수 정의는 `@function` ,리턴값은 `@return`

```scss
$grid-width: 40px;
$gutter-width: 10px;
@function grid-width($n) {
   @return $n * $grid-width + ($n -1 ) * $gutter-width;
}
#sidebar { width: grid-width(5); } // 믹스인과 달리 @include를 쓰지 않는다.
내장함수도 사용 가능
```

## 8. 흐름제어

분기문 : `@if`절 사용

`@if` 표현식 { ... } `@else`

`if` 표현식 { ... } `@else` { ... }

```scss
@mixin hcolor($n) {
  @if $n % 2 == 0 { color: white; }
  @else { color: blue; }
}
.row-3 { @include hcolor(3); }

@function text-color($brightness) {
  @if $brightness < 128 { @return #333; }
  @return #ccc;
}
code { color: text-color(200);
```

반복문

- `@for` : n~m 까지의 숫자 범위에 대해 각 정수값에 대해 순회
- `@each` : 주어진 리스트나 맵의 각 원소에 대해 순회
- `@while` : 주어진 조건을 만족하는 동안 반복

```scss
@for $i from 1 through 3 {
  // 1, 2, 3,에 대해 반복
  .time-#{$i} {
    width: 2em * $i;
  }
}

// 리스트 내 각 문자열 원소에 대해서...
@each $animal in puma, sea-slug, egret, alamander {
  .#{$animal}-icon {
    background-image: url('/image/#{$animal}.png');
  }
}

// 6, 4, 2번 아이템에 대해서
$i: 6;
@while $i > 0 {
  .item-#{$i} {
    width: 2em * $i;
  }
  $i: $i - 2;
}
```

<br>

---

<br>

## :hammer_and_wrench: 용어 공부

### :gear:

<br>

## 참고

- [blog, scss 문법 특징](https://joyoungg.gitbooks.io/scss/content/d2b9-c9d5.html)
