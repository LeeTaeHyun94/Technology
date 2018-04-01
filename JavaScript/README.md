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