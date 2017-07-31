## Data type (자료형)
- 기본자료형 (privitive data type)은 변경 불가능한 값이다.

### Number
- 숫자 자료형
- Infinity (+양의 무한대/-음의 무한대)
- NaN : 숫자가 아니다
```
var foo = 42 / -0;
console.log(foo);        // -Infinity
console.log(typeof foo); // number

var bar = 1 * 'string';
console.log(bar);        // NaN
console.log(typeof bar); // number
```

### String
- 텍스트 데이터 (유니코드 문자의 집합 *유니코드:다국어지원하는 문자포맷)
string은 '',"" 로 묶어준다 하지만 대부분 '' 사용
ex) It's -> 'It's'일경우 에러발생 -> "It's" 로 사용
- 자바스크립트의 문자열은 변경 불가능하다, 새로운 문자열을 할당하는것은 가능

```
var str = 'string'
str = str.substring(0,3)
/* 객체       함수             -> 메서드 */
```

### Symbol
- ES6에서 추가됨

---

# * 객체형 (Object type) *
- object는 변경가능한 데이터
- 객체안에는 데이터도 있고 함수도 있다.
- property와 method 를 포함, method 또한 property로 볼수있다.
 - 함수
 - 배열
 - 날짜
 - 정규식

---

 # * 변수 * 

- 제일 어려운거 : naming / 의미있는 이름을 지정하여야한다.
- 휘발성데이터가 아닌 값을 유지할 필요가 있을때 사용
- 저장한 데이터를 뽑아오는거 : 메모리에 있는 데이터를 변수를 이용해서 꺼내오는거
- 반드시 영문자, _(underscore:private한), $(jQuary)
```
var name;     // 변수 name 선언
name = 'Lee'; // 변수 name에 값 'Lee'가 저장(할당)되었다.

var age = 30; // 선언과 할당
```

* = 는 같다라는 의미가 아니라 할당을 의미한다. 같다를 하려면 ===

- 선언하는 방법 ,(comma로도 가능 but 하나씩 선언하는게 좋다)
```
var person = 'Lee',
    address = 'Seoul',
    price = 200;

var price = 10;
var tax   = 1;
var total = price + tax;
```
- 변수 선언을 하는순간 undefined로 공간을 확보한다. - 자체초기화
```
var x;
console.log(x); // undefined 변수선언은 했지만 할당없음
console.log(y); // ReferenceError 변수 선언한것이 없음
```

/* 할수있지만 사용하지말자
1. 변수의 중복 선언
```
var x = 1;
console.log(x); // 1

// 변수의 중복 선언
var x = 100;
console.log(x); // 100
```
-> 아래의 변수로 변경됨, 의도치않게 변수값을 변경할수있으므로 사용하지말자

2. var 키워드 생략해도 변수선언이 됨
x = 1; -> var x = 1;
but 의도치않게 전역변수로 사용될 수 있으므로 사용하지말자
전역변수가 되면 골치아픔.. */

## 동적 타이핑 
- 타이핑이란 데이터의 타입을 정하는것(엔진이 대신해줌)
- 변수의 타입이 무엇인지 선언하지않아도 값이 할당되는 과정에서 (데이터 타입을 보고) 자동으로 자료형이 결정
-> but 동적 타이핑의 한계때문에 type script가 등장함
 // runtime error

* 돌려쓰기 변수는 쓰지않는다 쓰고 버리세요

## 변수 호이스팅 (variable hoisting)

```
console.log(foo); // ① undefined
var foo = 123;
console.log(foo); // ② 123
{
  var foo = 456;
}
console.log(foo); // ③ 456
```
- 위에서 console.log(foo); // ① undefined 가 ReferenceError 아닌 이유 : var 선언문이나 function 선언문을 해당 Scope의 선두로 옮겨지는것처럼 행동, 즉 var 키워드로 선언된 변수는 선언 단계와 초기화 단계가 한번에 이루어진다. 즉, 스코프에 변수가 등록되고 변수는 메모리에 공간을 확보한 후 undefined로 초기화된다. 그후 var foo =123;으로 값이 할당되었으므로 그다음 consoled 은 값이 나타남
- 한줄요약 : 호이스팅되기때문에 var 변수가 맨위로 올라가서 선언과 동시에 초기화되므로 undefined로 나타남 아직 할당은 안되어있음!

*Scope(유효범위,지역)
{
  var foo = 456;
}
- 위와 같이 써도 자바스크립트는 다른 범위로 보지않는다. 결국 같은 변수를 위와같이 사용하면 중복선언이 되는거임

## var 키워드로 선언된 변수의 문제점

1. 전역 변수가 남발될 확률이 높다
2. var 키워드 생략하면 의도치않은 전역변수 생성
3. 중복선언을 해도 에러가 안나옴
4. 호이스팅으로 인해 변수선언 전에 참조 가능
: 대부분의 문제가 전역변수로 인해서 발생한다
* 해결방안 
 - ES6 의 let 과 const 키워드 도입 
 - 변수의 범위를 좁게 설정할수록 좋다.

---

# 연산자
## 1.산술연산자
```
var x = 5;
var y = 2;
var z;

z = x + y;  // 7
z = x - y;  // 3
z = x * y;  // 10
z = x / y;  // 2.5
z = x % y;  // 1
z = x++;    // 5 선대입후증가
z = ++x;    // 7 선증가후대입
z = x--;    // 7 선대입후감소
z = --x;    // 5 선감소후대입
```
// + 연산자는 덧셈 연산과 문자열 연결 연산을 수행한다.
```
var str1 = '5' + 5;      // '55' - 문자열
var str2 = 5 + '5';      // '55' - 문자열
var str3 = 'Hello' + 5;  // 'Hello5' - 문자열
```
## 2.대입연산자
=	  x = y	  x = y
+=	x += y	x = x + y
-=	x -= y	x = x - y
*=	x *= y	x = x * y
/=	x /= y	x = x / y
%=	x %= y	x = x % y

## 3.비교연산자
== 비교하고 같으면 true 다르면 false
=== 타입이 일치해야함 
```
var x = 5

x == 5    // true
x == '5'  // true 문자열인데 알아서 숫자로 변경해서 같다고 함
x == 8    // false

x === 5   // true
x === '5' // false
```

!= 같지않다
!==

/*
```
// 삼항연산자(ternary operator)
// 조건 ? 조건이 ture일때 반환할 값 : 조건이 false일때 반환할 값
var condition = true;
var result = condition ? 'true' : 'false';
console.log(result); // 'true'
```
*/

## 4.논리연산자
|| or
&& and
! not
-> true / false
: || 에서는 둘다 false일때만 false
: && 에서는 둘다 true일때만 true

## 5. 단축 평가 (Short-Circuit Evaluation)
true || anything	true
false || anything	anything
true && anything	anything
false && anything	false

## 6.타입연산자
typeof	변수의 자료형을 문자열로 반환한다. null과 배열의 경우 object, 함수의 경우 function를 반환하는 것에 유의하여야 한다.

typeof myCar                  // returns undefined (설계적 결함)
typeof null                   // returns object (설계적 결함) 

## 7. !!
!!의 역할은 피연산자를 boolean 값으로 변환

---

# Control Flow (제어문)

## 1. 블록구문 (Block statement)

## 2. 조건문
-코드블럭을 실행 할지 안할지
### if 문
```
if (조건식) {
  // 조건식이 참이면 이 코드블록이 실행된다.
} else {
  // 조건식이 거짓이면 이 코드블록이 실행된다.
}
```

꼭 else를 써야하는건 아님
```
var hour = 20;
var greeting;

// if 문
if (hour < 18) {
  greeting = 'Good day';
}

console.log(greeting); //undefined 출력
```

### switch
- switch문에는 break 를 써야한다.
```
var color = 'red';

switch (color) {
  case 'yellow':
    console.log('yellow color');
    break;
  case 'red':
    console.log('red color');
    break;           // true를 찾았으니 케이스를 종료하고 빠져나가
  case 'blue':
    console.log('blue color');
    break;
  default:
    console.log('unknown color');
}
```
brack를 만나야 참인데서 케이스 종료하고 값을 산출

---

# 반복문
## for
for ([초기문]; [조건문]; [증감문]) {
  구문;
}

-> 안쓰면 무한루프

## while

- 조건이 언제나 참이면 무한루프
- 증감식이 없으면 무한루프*
- 무한루프에서 탈출하기위해 if 문을 써서 break를 사용

## do while
코드블럭을 한번 실행하고 조건문을 확인

## continue
구문의 실행을 스킵하고 반복문의 조건문으로 이동
```
for (var i = 0; i < 5; i++) {
  if (i % 2 == 0) continue;
  console.log(i);
}
```
-> 위의 예제는 홀수만 출력 왜냐
if문이 짝수 continue 때문에 조건문으로 돌아감 짝수+1을 출력?

## 평가 (Evaluating)
ture false로 평가

### 암묵적 강제 형 변환 (Type coercion)
```
console.log('1' > 0);            // true
console.log(1 + '2');            // '12'
console.log(2 - '1');            // 1
console.log('10' == 10);         // true
console.log('10' === 10);        // false (타입까지 보니까)
console.log(undefined == null);  // true
console.log(undefined === null); // false
```
연산자가 돌아갈수있도록 최대한 형변환을 한다고 하지만 이렇게 하면 안돼

### data type conversion
string 에 *1 처럼 산술을 적용하면 숫자가 된다
```
var val = '123';
console.log(typeof val + ': ' + val); // string: 123

// sting -> number
val *= 1;
// val = Number(val);
// val = parseInt(val);
console.log(typeof val + ': ' + val); // number: 123

// number -> sting 
val += '';
// val = String(val);
console.log(typeof val + ': ' + val); // string: 123
```

### Checking equality
```
// logs false !!!
console.log(null == false);
console.log(undefined == false);
console.log(null == 0);
console.log(undefined == 0);
console.log(undefined === null);
console.log(NaN == null);
console.log(NaN == NaN);
```
- if 문 같은 조건문 쓸때 주의해야함

## Checking existence
```
if (document.getElementById('header')) {
  // 요소가 존재함 : 필요한 작업을 수행
} else {
  // 요소가 존재하지 않음 : 필요한 작업을 수행
}
```
있으면 헤더를 가져옴 (true) 없으면? 빠져나가던지 뭔가를 해야지

잘못된 예 (아래: 난 더 정확하게 쓸거야 / :응 아니야 돌아가 )
```
if (document.getElementById('header') == true) // false
```
---

# Object 객체
자바스크립트를 이루고있는 거의 모든것
property와 property value
 - 프로퍼티 이름 : 빈 문자열을 포함하는 문자열과 숫자
 - 프로퍼티 값 : undefined을 제외한 모든 값
- property에는 함수도 들어올수있고 표현식 등 데이터가 다 들어올수있지만 property에 함수가 들어오면 Method라고 부른다.
- 자바에서는 객체생성을 위해 클래스(붕어빵틀)을 만드는 과정이 필요하지만 자바스크립트는 클래스가 필요없다.

##  객체 리터럴
```
var emptyObject = {}; // 빈객체 생성(클래스가 필요없지)
console.log(typeof emptyObject); // object


var person = {
  name: 'Lee',   // 이름 name is property name, 'Lee' is value
  gender: 'male', // 성별 gender property name, 'male' is value
  sayHello: function () {  // 말할수있는 기능 sayHello is property name, function is value
    console.log('Hi! My name is ' + this.name); //this is person
  }
};

console.log(typeof person); // object
console.log(person); // { name: 'Lee', gender: 'male', sayHello: [Function: sayHello] }

person.sayHello(); // Hi! My name is Lee
```

## object() 생성자 함수
- 자바를 흉내낸 문법
 Object() 생성자 함수를 new 연산자와 함께 사용하면 빈객체가 만들어진다.

'var person = new Object();'
-빈객체를 만들고 프로퍼티 추가
```
// 빈 객체의 생성
var person = new Object();
// 프로퍼티 추가
person.name = 'Lee';
person.gender = 'male';
person.sayHello = function () {
  console.log('Hi! My name is ' + this.name);
};

console.log(typeof person); // object
console.log(person); // { name: 'Lee', gender: 'male', sayHello: [Function] }

person.sayHello(); // Hi! My name is Lee
```
객체 리터럴과 뭐가 달라?
결국 객체 리터럴은 object()생성자 함수의 shorthand 이다

## 생성자 함수
객체 리터럴 방식과 Object() 생성자 함수 방식으로 객체를 생성하는 것은 프로퍼티 값을 계속 기술해주어야한다. 불편해..이런 비효율을 해결하기 위해 생성자함수를 사용
생성자 함수를 사용하면 마치 객체를 생성하기 위한 템플릿(클래스)처럼 사용하여 구성이 동일한 객체 여러개를 간편하게 생성 
```
// 생성자 함수
function Person(name, gender) {
  this.name = name;
  this.gender = gender;
  this.sayHello = function(){
    console.log('Hi! My name is ' + this.name);
  };
}

// 인스턴스의 생성
var person1 = new Person('Lee', 'male');
var person2 = new Person('Kim', 'female');

console.log('person1: ', typeof person1);
console.log('person2: ', typeof person2);
console.log('person1: ', person1);
console.log('person2: ', person2);

person1.sayHello();
person2.sayHello();
```
->  객체를 뽑아내는 공장같은것
객체는 instance (리터럴방식으로 쓰는게 더 쉽지)

- 생성자 함수 이름은 일반적으로 첫문자를 대문자로 시작한다.

## 객체 프로퍼티에 접근
### 프로퍼티 이름
```
var person = {
  'first-name': 'Ung-mo',
  'last-name': 'Lee', //''를 쓰는 이유는 -를 연산자로 인식하기때문 이름을 쓰고싶다면 last_name으로 사용하자 혹은 lastName을 많이 쓴다.
  gender: 'male',
  function: 1 // OK. 하지만 예약어는 변수명으로 사용하지 말아야 한다.옳지않은 방법이다.
};

console.log(person.function);
```

- 예약어와 키워드는 변수명으로 쓰지마세요
- 변수명은 명사로 많이 사용, 값은 동사나 목적어를 많이 사용한다.

### 프로퍼티 값 읽기
```
var person = {
  'first-name': 'Ung-mo', 
  'last-name': 'Lee',
  gender: 'male',
};

console.log(person);

console.log(person.first-name);    // NaN: undefined-name 이렇게 이름쓰면 안돼 -연산자때문에
console.log(person[first-name]);   // ReferenceError: first is not defined
console.log(person['first-name']); // 'Ung-mo'

console.log(person.gender);    // 'male'
console.log(person[gender]);   // ReferenceError: gender is not defined
console.log(person['gender']); // 'male'
```

### 프로퍼티 값 갱신

### 프로퍼티 동적 생성
```
var person = {
  'first-name': 'Ung-mo',
  'last-name': 'Lee',
  gender: 'male',
};

person.age = 20;      //나중에 프로퍼티 값 할당
console.log(person.age); // 20 : 알아서 객체에 추가하고 값을 할당해준다.
```

### 프로퍼티 삭제
delete연산자로 객체의 프로퍼티를 삭제, 객체는 삭제안된다.

## Pass-by-reference

ex) var obj1={} -> 빈객체를 생성
var obj1 = obj2 -> obj2 === {} 빈객체와 같아
obj1.name ='Lee' -> obj2.name은 'Lee' 

