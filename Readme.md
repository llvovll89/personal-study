# 개인 공부정리용

``` 07-04 ( 퍼블리싱 작업도중 ) ```

###  <font color="salmon">1. transition 속성 </font>
- ease : 천천-빠름-천천
- linear : 등속
- ease-in : 천천-보통
- ease-out : 보통-천천
- ease-in-out : 천천-보통-천천
- cubic-bezier : 커스텀
- steps : 뚝뚝 끊어 보여준다

### <font color="salmon">2. position sticky & fixed 차이 </font>
- sticky: 스크롤 영역 내에서 요소를 일시적으로 고정
- fixed: 항상 뷰포트에 대한 상대적인 위치에 요소를 고정

### <font color="salmon"> 3. scss 적용시 (vs코드 익스텐션 활용) </font>
> Live Sass Compiler 이용
- 원리는 scss 파일을 만들어 코드작성 후 하단 watching 클릭하면 
타입 스크립트의 tsc-w 처럼 자동 컴파일링이 되므로 동일 명의 css파일이 자동생성된다
- 이렇게 생성된 css파일을 index.html에 연결하여 사용하는 방식
> 여기서 scss란 ?
- CSS 전처리기로 부르고  CSS 작성을 보다 효율적이고 유지보수하기 쉽게 만들어주는 도구
- 중괄호({})와 세미콜론(;)을 사용하여 CSS와 동일한 구문을 유지
- scss가 제공하는 기능
+ 변수(Variable) 할당 /
중첩(Nesting) 구문 /
모듈화(Modularity) /
믹스인(Mixins) /
확장&상속(Extend/Inheritance) /
연산자(Operators)
- 변수로 쓸 scss 코드파일을 따로 설정해서 import 해오는 식으로 사용가능 (모듈화)

``` 
// 중첩구문예시

nav {
  ul {
    margin: 0;
    padding: 0;
    list-style: none;
  }

  li { display: inline-block; }

  a {
    display: block;
    padding: 6px 12px;
    text-decoration: none;
  }
}
```

```
// 변수선언 (ex: variable.scss)
$font-stack: Helvetica, sans-serif;
$primary-color: #333;

@mixin card {
    @content
}

// 가져오기
@use 'variable';

.container {
  background-color: base.$primary-color;
  color: white;
}

@include variable.card {
    ...content
}

```

> @use 란 ? @import를 대체하는 문법으로 variables, mixins, functions를 연결하는 용도로 사용되고 @import와 동일하게 스타일시트 최상단에 연결합니다.<br>
@use의 기본 구조는 namespace(파일명)을 기반으로 이용할 수 있습니다. <br>이를 통해 어느 모듈에서 가져온 코드인지 명확하게 알 수 있습니다.<br>
- 선언 : @use [namespace]<br>
- 사용 : @include [namespace].[variable]<br>
- ‘as’를 이용하여 간결하게 namespace 변경 : @use ‘/style/mixin’ as m;