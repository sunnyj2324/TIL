#Javascript

## 1. Computational thinking
- 수행해야하는 명령을 컴퓨터에게 전달 (0-off,1-on) 
- bit 는 0과1이다 8개로 하면 byte가 된다
- 문제해결능력이 필요

## 2. Syntax & Semantics (문법과 의미)
- 인간이 이해할수있도록 문법을 사용하여 프로그램 작성
- 문법을 이해하고 문맥을 알아야 언어가 통한다.
- 문장은 프로그래밍 언어의 구문에 해당한다.
- 구문은 변수 , 값 , 키워드 , 연산자 , 표현식 , 주석 으로 구성된다
  - 변수 , 값 : 선언
  - 키워드 : 외워
- 위에서 아래로 진행하지만 조건문과 반복문에 의해 control할수있다

# Javascript

## 1. Introduction
Javascript는 HTML, CSS와 함께 웹을 구성하는 요소중 하나
- 웹브라우저에서 동작하는 유일한 언어
- Ecmascript6 (따로공부할것)
- 점점 서버가 가벼워지고 클라이언트로 역할 이동
- jQuery의 등장 : Cross Browsing -> 복잡한 프로젝트에 문제가 생기기 시작 -> 현재는 jQuery를 배제, Angular, React, Vue.js 로
-  C-family language
- Interpreter language : 동시통역 한줄한줄 읽으면서 파싱 (Compile x , html 파일안에 직접 기술가능 )
- 프로토타입의 객체지향 언어
- Node.js 로 브라우저 바깥에서도 실행할수있는 범용적 사용가능

##2. 브라우저 동작 원리

![브라우저동작원리](http://poiemaweb.com/img/client-server.png)
script 태그의 위치에 의해 DOM의 생성이 지연될 수 있다.
DOM을 만드는 프로세스때문에 </body> 바로 앞에 위치하는것이 좋다

## 3. History
- ECMAScript = javascript : java의 저작권문제로 이름을 못씀..정식명칭이다.
- 매년 업데이트되니까 꾸준히 공부할것

##4. Browsers Support
2017년 1월, 대부분의 브라우저는 ES6를 지원하고 있지만 100%는 아니다. 그리고 Node.js의 경우 v4부터 지원. 지금 사용할라면 babel과 같은 Transpiler를 사용

---

## Javascript Syntax Basics

### 구문 (Statement)
각각의 명령을 statement(구문)이라 하며 statement가 실행되면 무슨 일인가가 일어나게 된다. 구문은 값(Value), 연산자(Operator), 표현식(Expression), 키워드(Keyword), 주석(Comment)으로 구성되며 세미콜론( ; )으로 끝나야 한다.(자연어의 하나의 문장)

- 코드블럭
  ```
  // Function
function myFunction(x, y) {
  return x + y;
}
```

### 표현식 
- 하나의 값 : 값,변수,연산자의 조합으로 연산을 통해 하나의 값을 만듬

### 변수
값을 일시적으로 저장을 해야할 때가 있다.
값을 저장,참조하기위해 변수사용 (memory사용)
- naming: 식별자 (identify)

```
var name = 'Lee'
```
```
var name; // 변수의 선언과 undefind 초기화
name = 'Lee'; // 정수값의 할당 (처음으로 값이 주어짐)
```
 - 리터럴(literal)이란 변수 또는 상수에 저장되는 값 자체를 의미한다. 변수명은 메모리에 할당된 공간을 가리키는 식별자(identifier)이며 리터럴은 이 공간에 저장되는 값이다.

- 기본 자료형 (primitive data type)
  - Boolean
  - null
  - undefined
  - Number
  - String
  - Symbol (New in ECMAScript 6)
- Object

### 연산자

### 키워드
var keyword
```
var x = 5 + 6;
var y = x * 10;
```
## Javascript Data type & Variable

:: 변수는 위치를 기억하는 저장소, 위치는 memory 상의 주소를 의미
-> memory address에 접근하기위하여 naming을 한 식별자 identifier

:: Dynamic Typing : 변수의 타입을 정해놓고 시작하는 것이 아니라 값이 할당되는 과정에서 자동으로 자료형이 결정된다. 

- Boolean : true, false / '(whit space)' null undefined 0 -> false

- null : 의도적으로 값을 지움 / null을 체크할때는 typeof가 아니라 === 사용

- undefined : 선언은 되었지만 할당 x , 혹은 선언된적없는 변수의 접근



