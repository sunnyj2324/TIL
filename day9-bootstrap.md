# Centering with CSS (Vertical & Horizontal)
## 수평정렬
 - inline/inline-block
 ```
 .container {
  text-align: center;
}
```
- block
 -margin-right와 margin-left 프로퍼티에 auto 지정
- 복수의 block요소
  - inline-block으로 변경후 부모요소에 text-align:center; 지정 width값 지정
 ```
 .container {
  text-align: center;
}
.item {
  width: 150px;
  display: inline-block;
}
 ```
## 수직정렬
- single line
  - padding(top,bottom)으로 동일적용

- multiple line
  - vertical-align(table 속성사용)

### block 요소
부모 요소를 기준으로 절대위치
```
.parent {
  position: relative;
}
.child {
  position: absolute;
  top: 50%;
  height: 100px;
  /*요소의 높이(100px)의 반 만큼 위로 이동*/
  margin-top: -50px;
}
```
- height값을 모를 경우
```
.parent {
  position: relative;
}
.child {
  position: absolute;
  top: 50%;
  /*요소의 높이의 반(50%) 만큼 위로 이동*/
  transform: translateY(-50%);
}
```

## 수평/수직 정렬
- 요소의 width,height이 고정일때 or 불확실할때 모두 사용 가능
```
.parent {
  position: relative;
}
.child {
  position: absolute;
  top: 50%;
  left: 50%;
  /*요소의 높이/너비의 반(50%)만큼 위/왼쪽으로 이동*/
  transform: translate(-50%, -50%);
}
```

# Bootstrap Basics
## Introduction
- 모바일웹을 기반으로 한 간편한 반응형 웹디자인(responsive web design)을 위한 open-source front-end framework
  - 선택적 사용이 가능 (HTML, CSS, JavaScript)

Grid system
Typography
Code
Tables
Forms
Buttons
Images
Helper classes
Responsive utilities
Using Less
Using Sass

 - 적용예시(button) - class명만 갖다쓰면됨
 ```
  <a class="btn btn-default" href="#" role="button">Link</a> 
  ```
- 사용이 간단하고 편리하지만 지정되어있는 스타일이기때문에 디자인이 똑같이 나온다.
- 부트스트랩 사용의 가장 좋은점?
    - 반응형을 쉽게 사용할 수 있다.
    - 대부분의 브라우저를 지원한다.

### Code의 재사용(Code reuse)
 css attribute를 활용하면 중복선언을 방지하고 code reuse가능
 -> 미리 사용될 가능성이 높은 스타일을 미리 작성, class화하여 중복작성의 효율을 줄이고 이것이 비용절감과 품질의 향상으로 이어진다.

### Framework의 장점
팀프로젝트에서의 효율적인 진행을 위해서 미리 구조화한다.
- react, express,ect

* CDN 사용가능 but 권장x (서버가 다운되면 노답)

# Bootstrap Grid System

## Media Query
- 기본 4개의 breakpoint의 구간을 나눔
```
/* Extra small devices (phones, less than 768px) */
/* No media query since this is the default in Bootstrap */

/* Small devices (tablets, 768px and up) */
@media (min-width: @screen-sm-min) {
  /* ... */
}

/* Medium devices (desktops, 992px and up) */
@media (min-width: @screen-md-min) {
  /* ... */
}

/* Large devices (large desktops, 1200px and up) */
@media (min-width: @screen-lg-min) {   
  /* ... */
}
```
-> @screen-*의 @는 LESS의 변수를 의미

## Container
- 2가지 종류 (중첩사용x)
   - .container class - 고정폭(viewport width가 늘어나거나 줄어들어도 고정 width값을 가진다)
    - .container-fluid class - 최대width값의 layout(viewport에 상과없이 contents를 화면에 꽉차게)
 * container 내부에 container 쓰지않는다
 
 ## Grid system
 container > .row(행)> .col-*-*(열)을 배치 > contents
```
.container or .container-fluid
  .row
    .col-xs-#
      contents
    .col-xs-#
      contents
  .row
    .col-xs-#
      contents
    .col-xs-#
      contents
```
### Row
- container 안에 .row (class)로 배치

### Col
- col-breakpoint(xs,sm,md,lg)

![breakpoint](http://poiemaweb.com/img/bs_grid_options.png)

#### .col-xs-* class

- viewport width와 관계없이.col-xs-* 클래스는 언제나 적용
 ```
 .col-xs-1 {
  width: 8.33333333%;
}

.col-xs-2 {
  width: 16.66666667%;
}

/* .col-xs-3 ~ .col-xs-12 */

.col-xs-1, .col-xs-10, .col-xs-11, .col-xs-12, .col-xs-2, .col-xs-3, .col-xs-4, .col-xs-5, .col-xs-6, .col-xs-7, .col-xs-8, .col-xs-9 {
  float: left;
}

.col-lg-1, .col-lg-10, .col-lg-11, .col-lg-12, .col-lg-2, .col-lg-3, .col-lg-4, .col-lg-5, .col-lg-6, .col-lg-7, .col-lg-8, .col-lg-9, .col-md-1, .col-md-10, .col-md-11, .col-md-12, .col-md-2, .col-md-3, .col-md-4, .col-md-5, .col-md-6, .col-md-7, .col-md-8, .col-md-9, .col-sm-1, .col-sm-10, .col-sm-11, .col-sm-12, .col-sm-2, .col-sm-3, .col-sm-4, .col-sm-5, .col-sm-6, .col-sm-7, .col-sm-8, .col-sm-9, .col-xs-1, .col-xs-10, .col-xs-11, .col-xs-12, .col-xs-2, .col-xs-3, .col-xs-4, .col-xs-5, .col-xs-6, .col-xs-7, .col-xs-8, .col-xs-9 {
  position: relative;
  min-height: 1px;
  padding-right: 15px;
  padding-left: 15px;
}

 ```
  - 기본 padding을 가지고있다

#### .col-sm-* class
- viewport width가 768px 이상(768px ~)일 때 .col-sm-* class 적용

#### .col-md-* class
- viewport width가 992px 이상(992px ~)일 때 .col-md-* class 적용

#### .col-lg-* class
- viewport width가 1200px 이상(1200px ~)일 때 .col-lg-* class 적용

### col- class의 복합 구성

```
<div class="col-xs-12 col-sm-6">xs-12 sm-6</div>

```
-> 
    - viewport 너비가 768px 미만(~ 768px)이면 .col-xs-12 class가 적용
    - viewport 너비가 768px 이상(768px ~)이면 .col-sm-6 class가 적용

### Mobile and desktop
- Mobile의 경우 breakpoint는 768px 미만(~ 768px) , class prefix는 .col-xs-*
- Desktop의 경우, breakpoint는 992px(992px ~) 이상 , class prefix는 .col-md-*

### Mobile, tablet, desktop
```
<div class="container">
    <p class="bg-info">Viewport width가 992px 이상이면 3열, 768px~991px이면 2열, 768px미만이면 1열로 정렬된다</p>
    <div class="row">
      <div class="col-xs-12 col-sm-6 col-md-4">1</div>
      <div class="col-xs-12 col-sm-6 col-md-4">2</div>
      <div class="col-xs-12 col-sm-6 col-md-4">3</div>
      <div class="col-xs-12 col-sm-6 col-md-4">4</div>
      <div class="col-x
      s-12 col-sm-6 col-md-4">5</div>
      <div class="col-xs-12 col-sm-6 col-md-4">6</div>
    </div>
  </div>
```

## Nesting columns
- 열 내부에 그리드를 추가하면 자식 그리드의 전체 width는 부모 row의 width값 (parents안에서 100%)

## Offsetting columns
.col-*-offset-* class를 추가하면 오른쪽으로 열을 이동
```
<div class="col-md-2 col-md-offset-4">
```

## Column ordering
.col-*-push-* 와 .col-*-pull-* 클래스를 사용하여 열의 순서를 변경할 수 있다. : 자리변경(pair만 가능)