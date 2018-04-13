[JavaScript]
======================

원래는 웹브라우저를 제어하기 위해 고안된 언어. (for ClientSide)  
현재는 다양한 분야에 응용이 가능하다.



# 1. ServerSide Script

```
웹 서버 (응답) -> 웹 <- (요청) 웹 브라우저
```
Node.js



# 2. ClientSide Script



## 2.1 jQuery

```HTML의 클라이언트 사이드 조작을 단순화 하도록 설계된 크로스 플랫폼의 자바스크립트 라이브러리.```



# 3. Grammar



## 3.1 비교 연산자 (==, ===)



### 3.1.1 동등 연산자 (==)

```다른 언어들과 마찬가지로 좌항과 우항을 비교해서 서로 값(value)이 같다면 true, 다르다면 false를 반환한다.```



### 3.1.2 일치(완전 항등) 연산자 (=== <=> !==)

```
다른 언어들과 다르게 자바스크립트에 존재하는 좌항과 우항이 정확하게 일치할 때 true, 다르다면 false를 반환하는 연산자
정확하게 일치한다는 의미는 값(value)뿐만이 아니라 데이터형까지 엄격하게 일치해야 한다는 것이다.
```



## 3.2 Data Type

1. null - 프로그래머가 의도한 값이 없는 상태  
2. undefined - 말 그대로 정의되지 않은, 그래서 값이 없는 상태를 말한다.
3. NaN - 불가능한 연산의 결과를 반환 (ex. x / 0 등등)
4. boolean - true / false (* '' == false, 'string', !undefined, !null, !NaN == true)



## 3.3 Regular Expression (정규 표현식)

문자열에서 특정한 문자를 찾아내는 도구.

```
var pattern = /a/ = new RegExp('a');
pattern.exec('abcdef'); // return Object ["a", index : 0, input: "abcdef", groups: undefined]
			// 필요한 정보를 추출
'abcdef'.match(pattern);
pattern.test('abcdef'); // return boolean
			// 패턴의 유무
'abcdef'.replace(pattern, 'A'); // 패턴을 찾고 전달한 문자열로 교체

/(\w+)\s(\w+)/ // $1(하나 이상의 심볼) + 공백 + $2(하나 이상의 심볼)

var urlPattern = /\b(?:https?):\/\/[a-z0-9-+&@#\/%?=~_|!:,.;]*/gim;
```



### 3.3.1 옵션 (i, g)

- i : 대소문자 구분없이 패턴 검색
- g : 검색된 모든 결과를 반환



## 3.4 Debug

> Chrome 개발자 도구 (F12) - Sources 탭을 통해 디버깅이 가능하다. (Go to next breakpoint, Step into, Step over)  
	=> Watch Expressions : 변수를 입력하면 해당 변수에 대한 모니터링이 가능.  
	=> Global : 전역 변수  
	=> Scope Variables : 지역 변수  
	=> 스크립트 코드 중단점 외에도 DOM, XHR, Event Listener 중단점도 있다.



## 3.5 Function (함수)

개념은 기존의 프로그래밍 언어들과 비슷하다. 재사용 가능하고, 코드의 가독성을 좋게 하고 유지 보수에 용이하다.
* 자바스크립트의 독특한 표현법 : var numbering = function(){} <- 변수를 선언하여 안에 함수를 대입 가능.  
				 (function(){})(); <- 익명함수



## 3.6 Array (배열)

```
var arr = ['apple', 'banana', 'cat']; // 인덱스를 통한 데이터의 접근 방식은 다른 프로그래밍 언어와 같다.
arr.length // 배열의 크기
arr.push(''); // 배열의 맨 끝에 데이터를 추가한다.
arr.concat(array); // 다른 배열을 arr 배열의 끝에 이어 붙인다.
arr.unshift(''); // 배열의 맨 앞에 데이터 추가.
arr.splice(index, 삭제할 원소의 개수, 원소...); // 배열의 특정 순서의 인덱스부터 인자로 전달한 개수만큼
					      // 기존의 원소를 삭제하고 새로운 원소를 삽입한다. 삭제된 원소들을 반환.
arr.shift(); // 배열의 맨 앞 요소를 삭제하고 반환.
arr.pop(); // 배열의 맨 끝 요소를 삭제하고 반환.
arr.sort(); // 정렬, 매개변수로 compare 함수를 넣고 정렬 가능. 없다면 기본 내림차순 정렬.
arr.reverse(); // 배열을 거꾸로 뒤집는다.
```

## 3.7 Object (객체)



### 3.7.1 Dictionary (C++ Map과 유사.)

```
var dic = {'apple' : 1, 'banana' : 2, 'cat' : 3}; // 객체(Dictionary)의 생성, Key : Value
dic['apple'], dic.apple // value에 접근하는 두 가지 표현방식.
for(key in dic) console.log("key : " + key + ", value : " + dic[key]);
// for(var in Object) <= for in 문을 통해 객체에 접근 가능.
```



### 3.7.2 객체 지향 프로그래밍

```
var grades = {
	'list' : {'A' : 100, 'B' : 90, 'C' : 80},
	'show' : function() {
		for (var key in this.list) console.log("key : " + key + ", value : " + this.list[key]);
	}
};
grades.show();
// 위 형태의 프로그래밍이 가능하다. Java에서 메소드를 정의했던 방식을 JavaScript에서는 변수에 함수를 정의하여
// grades라는 객체는 함수도 사용 가능하고 멤버 변수 또한 사용 가능하다.
```



## 3.8 함수 지향 - 유효범위

* 정적 유효범위 (Static Scoping) = Lexical Scoping

```javascript
var i = 10;
// a 함수에서의 i = 5는 b 함수에 영향을 미치지 못한다.
function a(){
    var i = 5;
    b();
}

function b(){
    Console.log(i);
}
```



## 3.9 함수 지향 - 값으로서의 함수와 콜백

JavaScript에서는 함수 또한 객체 (일종의 값)



### 3.9.1 함수의 다양한 형태(용도)

```javascript
var a = {
    b : function(){
        
    }
}; // 이런 식으로 변수에 함수 값을 대입 가능하다.

function cal(func, num) {
    return func(num);
}
function increase(num) {
    return num + 1;
}
function decrease(num) {
    return num - 1;
}
console.log(cal(increase, 1));
console.log(cal(decrease, 1));

function cal(mode) {
    var funcs = {
        'plus' : function(left, right) { return left + right; },
        'minus' : function(left, right) { return left - right; }
    };
    return funcs[mode];
}
console.log(cal('plus')(2, 1));
console.log(cal('minus')(2, 1));
// 함수의 return 값으로도 사용 가능

var process = [
    function(input) { return input + 10; },
    function(input) { return input * input; },
    function(input) { return input / 2; }
];
var input = 1;
for(var i = 0; i < process.length; i++) input = process[input];
console.log(input);
// 배열의 값으로도 함수를 대입 가능하다.
```



### 3.9.2 Callback

함수가 값으로 사용될 수 있는 특성을 이용하여 함수의 인자로 전달해주면 인자로 전달해 준 함수가 호출되는 것을 통해 실행하고자 하는 함수의 동작 방식을 바꿀 수 있다.

```javascript
var numbers = [20, 10, 9, 8, 7, 6, 5, 4, 3, 2, 1];
var sortFunc = function(a, b) {
    return b - a;
};
console.log(numbers.sort(sortFunc));
// 원래 sort 메소드는 배열의 숫자들을 문자열로 처리해서 사전 순으로 정렬해주지만 직접 정렬을 위한 함수를 작성하여 인자로
// 전달해주게 되면 숫자의 크기를 오름차순으로 정렬이 된다.
```

* Ajax를 통한 비동기 처리에서 콜백이 유용하게 사용된다.



## 3.10 함수 지향 - Closure

내부 함수가 외부 함수의 Context에 접근하는 행위

내부 함수에서는 외부 함수의 지역 변수에 접근 가능하다는 것이 특징.

```javascript
function outter() {
    var title = 'coding everybody';
    function inner() {
        console.log(title);
    }
    inner();
}
outter();
// 어떤 특정한 외부 함수 내부에서만 쓰고 싶은 함수를 외부 함수 안 쪽에 함수를 선언하게 된다.
// inner 함수에서 밖의 title 변수에 접근 가능하다.

function outter() {
    var title = 'coding everybody';
    return function() {
        console.log(title);
    }
}
inner = outter();
inner();
// 외부 함수의 실행이 끝나서 외부 함수가 소멸된 이후에도 내부 함수는 외부 함수의 변수에 접근할 수 있다.
// 이러한 메커니즘을 Closure 라고 한다.
```



### 3.10.1 Private Variable

```javascript
function factory_movie(title) {
    return {
        get_title : function() {
            return title;
        },
        set_title : function(_title) {
            title = _title
        }        
    };
}
ghost = factory_movie('Ghost in the shell');
matrix = factory_movie('Matrix');
console.log(ghost.get_title());
console.log(matrix.get_title());
ghost.set_title('공각기동대');
console.log(ghost.get_title());
console.log(matrix.get_title());
// 이와 같은 방식으로 같은 함수를 통해 다른 객체를 만들 수 있다.
// 외부 함수의 지역 변수인 title이 서로 다른 같은 모양의 객체를 만들 수 있다는 것!
// title 같은 private variable을 프로그래밍 가능하다.
```



### 3.10.2 Closure를 응용하며 주의해야 할 점

```javascript
var arr = []
for(var i = 0; i < 5; i++){
    arr[i] = function(){
        return i;
    }
}
for(var index in arr) {
    console.log(arr[index]());
}
// 이렇게 코딩하면 arr 배열의 값들은 전부 5가 된다. 생각처럼 0, 1, 2, 3, 4 가 저장되지 않는 것을 볼 수 있다.
var arr = []
for(var i = 0; i < 5; i++){
    arr[i] = function(id) {
        return function(){
            return id;
        }
    }(i);
}
for(var index in arr) {
    console.log(arr[index]());
}
// 이렇게 배열의 값에 외부 함수의 지역 변수로 id를 선언하고 그 id를 반환하는 내부 함수를 반환하는 외부 함수를 구성하게 되면
// 배열의 각 인덱스에는 개별적으로 외부 함수의 private variable 값이 들어가게 되어
// 0, 1, 2, 3, 4를 저장할 수 있게 된다.
```



## 3.11 함수 지향 - Arguments

```javascript
function sum(){
    var i, _sum = 0;    
    for(i = 0; i < arguments.length; i++){
        console.log(i + ' : ' + arguments[i]);
        _sum += arguments[i];
    }   
    return _sum;
}
console.log('result : ' + sum(1,2,3,4));
// 이처럼 sum 함수에 인자를 전달받는 부분이 없음에도 불구하고 1, 2, 3, 4를 인자로 전달할 수 있다.
// 이유는 모든 함수에는 arguments라는 특수한 배열이 있기 때문이다.

function zero(){
    console.log(
        'zero.length', zero.length, // 함수로 전달된 실제 인자의 수를 의미
        'arguments', arguments.length // 함수에 정의된 인자의 수를 의미
    );
}
function one(arg1){
    console.log(
        'one.length', one.length,
        'arguments', arguments.length
    );
}
function two(arg1, arg2){
    console.log(
        'two.length', two.length,
        'arguments', arguments.length
    );
}
zero(); // zero.length 0 arguments 0 
one('val1', 'val2');  // one.length 1 arguments 2 
two('val1');  // two.length 2 arguments 1
```



## 3.12 함수 지향 - 함수의 호출

우리가 사용하는 함수들은 모두 Function 객체의 인스턴스이다. 때문에 Function 객체의 내장 메소드들을 사용가능한데, 호출에 사용되는 메소드는 apply와 call이 있다.

```javascript
function sum(arg1, arg2) {
    return arg1 + arg2;
}
console.log(sum.apply(null, [1, 2]));

o1 = {val1 : 1, val2 : 2, val3 : 3}
o2 = {v1 : 10, v2 : 50, v3 : 100, v4 : 25}
function sum(){
    var _sum = 0;
    for(name in this){ // this에 객체를 인자로 전달
        _sum += this[name];
    }
    return _sum;
}
console.log(sum.apply(o1)) // 6
console.log(sum.apply(o2)) // 185
```



## 3.13 Object Oriented Programming (객체 지향 프로그래밍)

로직을 상태(State)와 행위(Behave)로 구성하여 이를 하나의 객체(변수 + 메소드)라는 단위로 프로그래밍하는 패러다임.

* 추상화
* 부품화 : 소프트웨어를 객체 단위로 구성하여 어느 하나의 기능에 해당하는 객체를 구현, Javascript에서는 Object
* 정보 은닉, 캡슐화 : 객체는 이러한 특성들을 갖는다.
* 인터페이스 : 각각의 부품을 연결하기 위한 연결점. 이러한 연결점에는 항상 표준이 있다.
* Javascript는 Prototype-based Programming



## 3.14 객체 지향 - 생성자와 new

```javascript
var person = {}; // 비어 있는 객체 생성 (Literal Object)
person.name = 'llstaaar';
person.introduce = function() {
    return 'My name is ' + this.name;
};
console.log(person.introduce());
// 위 코드는 객체를 만드는 과정이 분산되어 있으므로 객체를 정의할 때 값도 저장하도록 하자.

var person = {
    'name' : 'llstaaar',
    'introduce' : function() { return 'My name is ' + this.name; }
};
// 하지만 이 코드 또한 같은 특징을 가진 객체를 생성할 때 코드의 중복이 생기므로 좋은 코드는 아니다.
```

- Constructor (생성자) : 객체를 만드는 역할을 하는 함수, 변수를 선언하면서 new 키워드를 붙여주면 함수가 객체의 생성자로 사용되는 것을 알 수 있다.

```javascript
function Person(name) {
    this.name = name;
    this.introduce = function() {
        return 'My name is ' + this.name;
    };
}
var p1 = new Person('llstaaar');
var p2 = new Person('llmooon');
console.log(p1.introduce());
console.log(p2.introduce());
```



## 3.15 객체 지향 - Global Object (전역 객체)

모든 객체는 window라는 전역 객체의 프로퍼티이다. (Node.js에서는 global)



## 3.16 객체 지향 - this

* this : 함수 내에서의 함수 호출 맥락(Context), Javascript에서는 함수와 객체의 느슨한 관계를 연결시켜주는 역할을 하는 키워드, 함수를 어떻게 호출하느냐에 따라서 this가 가리키는 대상이 달라진다.

```javascript
this === window; // true, 평문에서의 this는 전역 객체인 window를 가리킨다.
var o = {
    func : function() {
        if(o === this) console.log("o === this");
    } // 객체에 속하는 메소드의 this는 그 객체를 가리킨다.
};

// 생성자(함수) 안에 있는 this는 함수로 호출됐을 때는 전역 객체인 window를 가리키고
// 생성자로 사용됐을 때는 생성되는 객체를 가리키게 된다.

function sum1(x, y) { return x + y; }
var sum2 = new Function('x', 'y', 'return x + y;'); // 객체로서 함수를 선언

var o = {}
var p = {}
function func(){
    switch(this){
        case o:
           	console.log('o');
            break;
        case p:
            console.log('p');
            break;
        case window:
            console.log('window');
            break;          
    }
}
func(); // 함수를 그냥 호출했을 때에는 this === window
func.apply(o); // apply 메소드를 통해 o 객체를 인자로 전달하여 함수를 호출하면 this === o
func.apply(p); // apply 메소드를 통해 p 객체를 인자로 전달하여 함수를 호출하면 this === p
```



## 3.17 객체 지향 - Inheritance (상속)

상속을 통해 객체의 로직을 그대로 물려받는 또 다른 객체를 만들 수 있다.

```javascript
function Person(name) {
    this.name = name;
}
Person.prototype.name = null;
Person.prototype.introduce = function () { return 'My name is ' + this.name; };
var p1 = new Person('llstaaar');
console.log(p1.introduce());
function Programmer(name) {
    this.name = name;
}
Programmer.prototype = new Person();
// prototype이라는 특수한 Property에 상속받을 객체를 생성하여 대입하면 Person 객체의
// prototype property의 정보들을 갖고 객체를 생성하여 넘겨주는 방식

Programmer.prototype.coding = function () { return 'Hello, World!'; };
// prototype property를 통해 새로운 property나 method들을 추가해줄 수 있다.

var p2 = new Programmer('llstaaar');
console.log(p2.introduce());
```

* prototype : 