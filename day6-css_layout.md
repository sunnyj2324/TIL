# CSS3 Position
요소의 위치 기본적으로 parents의 top-left
Position property - top , bottom , left , right

## Static
- position static을 정의하지 않아도 기본값으로 지정
- 이미 설정된 position을 무력화할때 사용

## relative
- 기본위치를 기준으로 좌표 property를 허용
- parents의 자리가 바뀌면 같이 이동

## absolute
- parents (static제외) 요소를 기준으로 이동
- 상위요소에 relative, absolute, fixed 가 없을 경우 body기준(static은 무시됨)
- 기준이 될 parents요소에 relative를 설정
- absolute에는 width와 height을 지정해야함

* relative와 absolute의 차이점
- relative : parents를 기준으로 위치
- absolute : static을 제외한 parents 혹은 grand parents 의 요소를 기준으로 위치

## fixed
- parents요소와 관계없이 브라우저 viewport를 기준으로 위치
- scroll되도 동일한 위치에 존재함

## Z-index property

## Overflow
- parents 영역을 벗어날경우의 처리방법

# CSS3 Float
- layout 구성요소
    - none: 기본값
    - right : right top
    - left : left top

* float가 선언되면 width가 content에 맞게 최소화되고 다음 요소 위에 떠있다
  - 그래서 overflow: hidden; 사용

# Inheritance
- 상속이 안되는 property도 inherit를 이용하면 상속을 받을수 있다.
```
<style>
    .text-red {
      color: red;
      border: 1px solid #bcbcbc;
      padding: 10px;
    }
    .text-red button {
      color: inherit;
    }
    .text-red p {
      border: inherit;
      padding: inherit;
    }
  </style>
```
# Cascading
## CSS 적용 우선순위
  - head 요소 내의 style 요소
  - head 요소 내의 style 요소 내의 @import 문
  - <link> 로 연결된 CSS 파일
  - <link> 로 연결된 CSS 파일 내의 @import 문
  - 브라우저 디폴트 스타일시트
## 명시도
!important > 인라인 스타일 > 아이디 선택자 > 클래스/속성/가상 선택자 > 태그 선택자 > 전체 선택자 > 상위 요소에 의해 상속된 속성
```
p        { color: red !important; }
    #thing   { color: blue; }
```
  -> #thing 의 우선 순위가 높지만 !impotant;의 영향으로 red가 적용

- 선언순서에 따라 우선 순위 적용 / 같은 명시도를 기준으로 나중에 선언된 스타일이 우선 적용

# Vender Prefix
- 구형 브라우저를 지원하기 위해 벤더 프리픽스를 사용하여야 할 필요가 있다
```
* {
  -webkit-user-select: none;  /* Chrome all / Safari all */
  -moz-user-select: none;     /* Firefox all */
  -ms-user-select: none;      /* IE 10+ */
  user-select: none;          /* Likely future */
}
```
-> 브라우저 종류에 따른 property 지정, but 많은 코드의 양은 성능에도 영향을 준다

# CSS Effect
- shadow
- gradient
- Transition
- Animation
- Transform

### Transition
  - transition은 자동으로 발동되지 않는다. :hover와 같은 가상 클래스 선택자(Pseudo-Classes) 또는 JavaScript의 onclick 이벤트와 같은 부수적인 액션에 의해 발동한다.
  - transition-property 프로퍼티는 트랜지션의 대상이 되는 CSS 프로퍼티명을 지정한다. 지정하지 않는 경우 모든 프로퍼티가 트랜지션의 대상이 된다. 복수의 프로퍼티를 지정하는 경우 쉼표(,)로 구분한다.
  ```
     {
       transition-property: width, background-color;
       transition-duration: 2s, 2s;
     }
  ```
 - 모든 property가 transition의 대상이 될수는 없다.
 - layout에 영향을 주는 transition은 피하는 것이 좋다.
 - shorthand :transition: property duration function delay

### Animation
- Transition과의 차이: 자동으로 발동, 무한발동 가능
- JS와 비교하여 더 나은 렌더링 성능을 제공한다.
- 여러 사항들을 고려하여 자바스크립트를 사용하여야 할지 CSS를 사용하여야 할지 결정
#### @keyframs
  ```
  @keyframes move {
  /* 애니메이션 시작 시점 */
  from { left: 0; }
  /* 애니메이션 종료 시점 */
  to   { left: 300px; }
  }
  ----------------------
  @keyframes move {
  0%   { left: 0; }
  50%  { left: 100px; }
  100% { left: 300px; }
  }
  ```

