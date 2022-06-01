# sass(scss)의 장점

1. 변수 사용가능
   선언방법 - $변수명 : 속성값;

변수 타입 : 숫자, 문자열, 색상, boolean, null, lists, maps

2. 수학 연산자 사용가능
   사용가능 연산자 : +, -, /, \*, %, ==, !=

주의 :

+, - 연산시에는 단위 통일

나눔기호 사용시에는 괄호로 묶어서 사용

3. Nesting 기능
   중첩해서 선언하기 가능

/_ CSS _/
.container {
width: 100%;
}

.container h1 {
color: red;
}
/_ Sass _/
.container {
width: 100%;
h1 {
color: red;
}
}
상위요소 참조시에는 & 문자 사용

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

.widget { font-weight: 400; }
.widget-area { font-weight: 600; }
.widget-top_posts { font-weight: 1000; }
/_ Sass _/

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
&-area { font-weight: 600; }
&-top_posts { font-weight: 1000; }
} 4. import와 extend
@import 지시어를 사용해서 다른 scss 파일을 임포트할 수 있다

@extend 지시어를 사용하여 특정 선택자의 속성을 상속받을 수 있다

.box, .success-box {
border: 1px solid gray;
padding: 10px;
display: inline-block;
}

.success-box {
border: 1px solid green;
}

/_ Sass _/
.box {
border: 1px solid gray;
padding: 10px;
display: inline-block;
}

.success-box {
@extend .box;
border: 1px solid green;
}
Placeholder 선택자 %를 사용하면 상속은 하면서 해당 선택자는 컴파일 X
/_ SASS _/
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

/_ CSS _/
.success-box, .error-box {
padding: 0.5em;
}

.success-box {
color: green;
}

.error-box {
color: red;
} 6. 믹스인(Mixin)
공통적으로 쓰이는 css 속성들을 묶어서 재사용이 가능하게 하는 기능

parameter를 받을 수 있다

선언 @mixin

사용 @include

/_ SASS _/
@mixin headline ($color, $size) {
color: $color;
font-size: $size;
}

h1 {
@include headline(green, 12px);
}

// 인자에 default값 적용
@mixin headline ($color : #eee, $size:10px ) {
width: 50px;
}

/_ CSS _/
h1 {
color: green;
font-size: 12px;
}
/_ SASS _/

@mixin media($queryString){
    @media #{$queryString} {
@content;
}
}

.container {
width: 900px;
@include media("(max-width: 767px)"){
width: 100%;
}
}

/_ CSS _/
.container {
width: 900px;
}
@media (max-width: 767px) {
.container {
width: 100%;
}
} 7. 커스텀 함수 사용
함수 정의는 @function ,리턴값은 @return

8. 흐름제어
   분기문 : @if절 사용

<br>

---

<br>

## :hammer_and_wrench: 용어 공부

### :gear:

<br>

## 참고

- [blog, scss 문법 특징](https://joyoungg.gitbooks.io/scss/content/d2b9-c9d5.html)
