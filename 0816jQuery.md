# jQuery
- DOM API
- Animation 사용에 편리함

```
var elem = document.getElementsByTagName('h1');
for (var i = 0; i < elem.length; i++) {
  elem[i].textContent = 'Hello';
}
```

```
<!DOCTYPE html>
<html>
  <head>
    <title>jQuery</title>
  </head>
  <body>
    <h1 id="main-heading">What is jQuery?</h1>

    <p>jQuery is the most popular JavaScript library.</p>
    
    <h1>Why should you learn jQuery?</h1>
    
    <p class="note">Note: jQuery functions use the DOM API (like <code>document.getElementById</code>).</p>

    <!-- CDN 방식으로 jQuery를 사용할 수도 있다. -->
    <!-- https://developers.google.com/speed/libraries/#jquery -->
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/1.12.4/jquery.min.js"></script>
    <script src="app.js"></script>
  </body>
</html>
```

* googleapis.com을 이용하자

js code - 여러개가 있을때 자동으로 for문을 돌린다.
```
// app.js
$('h1').text('Hello');
```
app.js는 jQuery를 사용하므로 app.js 로드 이전에 jQuery가 로드되어야 한다.

## 3.4 콜백함수를 인수로 전달받을 때

```
// js/app.js
$(function () {
  $('h1').text('Hello!');
});
```

- DOM이 완전히 로드되기 전까지 대기하다가 로드가 완료되면 매개변수로 전달된 콜백함수가 실행

# Selector

- jQuery

```
    <script>
      $(function () {
        console.log($('li'));
        // [li, li, li.promo, prevObject: n.fn.init(1), context: document, selector: "li"]
        $('li').text('Orlando');
      });
    </script>
```
- JS

```
var targets = document.getElementsByTagName('li');
for(var i = 0; i < targets.length; i++){
  // text노드를 선택한 후, text를 변경
  targets[i].firstChild.nodeValue = 'Orlando';
}
```

## 4.2 후손 선택자 (Descendant Selector)
후손 선택자는 'space'가 들어가야함

```
$(function () {
        $('#destinations .promo').text('Orlando');

        // var el = document.querySelectorAll('#destinations .promo');
        // for (var i = 0; i < el.length; i++) {
        //   el[i].textContent = 'Orlando';
        // }
      });
```
## 4.3 자식 선택자 (Child Selector)
```
$(function () {
        $('#destinations > li').text('Orlando').css('color', 'red');

        // var el = document.querySelectorAll('#destinations > li');
        // for (var i = 0; i < el.length; i++) {
        //   el[i].textContent = 'Orlando';
        //   el[i].style.color = 'red';
        // }
      });
```
## 4.4 복합 선택자 (Multiple Selector)
```
$(function () {
        $('#france > li, .promo').text('Orlando');

        // var el = document.querySelectorAll('#france > li, .promo');
        // for (var i = 0; i < el.length; i++) {
        //   el[i].textContent = 'Orlando';
        // }
      });
```
- 중첩관계가 부서지지않고 잘 전달됨

## 4.5 가상 클래스 선택자 (Pseudo-Class Selector)
```
$(function () {
        $('#destinations li:first').css('color', 'red');
        $('#destinations li:last').css('color', 'blue');
        // $('#destinations li:odd').css('color', 'orange'); 홀수번째
        // $('#destinations li:even').css('color', 'purple'); 짝수번째 (0번부터 선택)

        // var el = document.getElementById('destinations');
        // console.log(el.firstChild);
        // console.log(el.lastChild);

        // el.firstChild.style.color = 'red';
        // el.lastChild.style.color = 'blue';
      });
```

## 5. Traversing
```
$(function () {
        var el1 = $('#destinations li');         // Descendant Selector
        var el2 = $('#destinations').find('li'); // Traversing

        console.log(el1);
        // [li, li, li.promo, prevObject: n.fn.init(1), context: document, selector: "#destinations li"]
        console.log(el2);
        // [li, li, li.promo, prevObject: n.fn.init(1), context: document, selector: "#destinations li"]
      });
```

같은 동작이지만 traversing이 더 빠름
더 정확한 direction을 준다

## 6. Manipulation
### 6.1. Appending

```
<!DOCTYPE html>
<html>
  <head>
    <title>jQuery</title>
  </head>
  <body>
    <ul>
      <li class="vacation">
        <h2>Hawaiian Vacation</h2>
        <button>Get Price</button>
                                      //이 위치에 들어감  <p>From $399.99</p>
      </li>
    </ul>

    <script src="https://ajax.googleapis.com/ajax/libs/jquery/1.12.4/jquery.min.js"></script>
    <script>
      $(function () {
        var price = $('<p>From $399.99</p>');
        $('.vacation').append(price);
      });
    </script>
  </body>
</html>
```

- append() : 선택 요소의 닫는 태그 앞에 콘텐츠를 삽입한다.
- prepend() : 선택 요소의 여는 태그 뒤에 콘텐츠를 삽입한다.
- after() : 선택 요소의 뒤에 콘텐츠를 삽입한다.
- before() : 선택 요소의 앞에 콘텐츠를 삽입한다.

### 6.2. Removing
```
<!DOCTYPE html>
<html>
  <head>
    <title>jQuery</title>
  </head>
  <body>
    <ul>
      <li class="vacation">
        <h2>Hawaiian Vacation</h2>
        <button>Get Price</button>
      </li>
    </ul>

    <script src="https://ajax.googleapis.com/ajax/libs/jquery/1.12.4/jquery.min.js"></script>
    <script>
      $(function () {
        var price = $('<p>From $399.99</p>');
        $('.vacation').append(price);
        $('button').remove();
      });
    </script>
  </body>
</html>
```

## 8. Event

매치드셋에 이벤트를 바인딩하고 해당 이벤트가 발생했을 때 실행될 콜백 함수를 지정한다.

```
.on( events [, selector ] [, data ], handler )
```

```
$(function () {
        $('button').on('click', function () {
          var price = $('<p>From $399.99</p>');
          $(this).closest('.vacation').append(price);
          $(this).remove();
        });
      });
```
---
# 7.2 jQuery Ajax & JSON
비동기식 처리 모델과 Ajax

