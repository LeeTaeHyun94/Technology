[JavaScript]
======================

������ ���������� �����ϱ� ���� ��ȵ� ���. (for ClientSide)  
����� �پ��� �о߿� ������ �����ϴ�.



# 1. ServerSide Script

```
�� ���� (����) -> �� <- (��û) �� ������
```
Node.js



# 2. ClientSide Script



## 2.1 jQuery

```HTML�� Ŭ���̾�Ʈ ���̵� ������ �ܼ�ȭ �ϵ��� ����� ũ�ν� �÷����� �ڹٽ�ũ��Ʈ ���̺귯��.```



# 3. Grammar



## 3.1 �� ������ (==, ===)



### 3.1.1 ���� ������ (==)

```�ٸ� ����� ���������� ���װ� ������ ���ؼ� ���� ��(value)�� ���ٸ� true, �ٸ��ٸ� false�� ��ȯ�Ѵ�.```



### 3.1.2 ��ġ(���� �׵�) ������ (=== <=> !==)

```
�ٸ� ����� �ٸ��� �ڹٽ�ũ��Ʈ�� �����ϴ� ���װ� ������ ��Ȯ�ϰ� ��ġ�� �� true, �ٸ��ٸ� false�� ��ȯ�ϴ� ������
��Ȯ�ϰ� ��ġ�Ѵٴ� �ǹ̴� ��(value)�Ӹ��� �ƴ϶� ������������ �����ϰ� ��ġ�ؾ� �Ѵٴ� ���̴�.
```



## 3.2 Data Type

1. null - ���α׷��Ӱ� �ǵ��� ���� ���� ����  
2. undefined - �� �״�� ���ǵ��� ����, �׷��� ���� ���� ���¸� ���Ѵ�.
3. NaN - �Ұ����� ������ ����� ��ȯ (ex. x / 0 ���)
4. boolean - true / false (* '' == false, 'string', !undefined, !null, !NaN == true)



## 3.3 Regular Expression (���� ǥ����)

���ڿ����� Ư���� ���ڸ� ã�Ƴ��� ����.

```
var pattern = /a/ = new RegExp('a');
pattern.exec('abcdef'); // return Object ["a", index : 0, input: "abcdef", groups: undefined]
			// �ʿ��� ������ ����
'abcdef'.match(pattern);
pattern.test('abcdef'); // return boolean
			// ������ ����
'abcdef'.replace(pattern, 'A'); // ������ ã�� ������ ���ڿ��� ��ü

/(\w+)\s(\w+)/ // $1(�ϳ� �̻��� �ɺ�) + ���� + $2(�ϳ� �̻��� �ɺ�)

var urlPattern = /\b(?:https?):\/\/[a-z0-9-+&@#\/%?=~_|!:,.;]*/gim;
```



### 3.3.1 �ɼ� (i, g)

- i : ��ҹ��� ���о��� ���� �˻�
- g : �˻��� ��� ����� ��ȯ



## 3.4 Debug

> Chrome ������ ���� (F12) - Sources ���� ���� ������� �����ϴ�. (Go to next breakpoint, Step into, Step over)  
	=> Watch Expressions : ������ �Է��ϸ� �ش� ������ ���� ����͸��� ����.  
	=> Global : ���� ����  
	=> Scope Variables : ���� ����  
	=> ��ũ��Ʈ �ڵ� �ߴ��� �ܿ��� DOM, XHR, Event Listener �ߴ����� �ִ�.



## 3.5 Function (�Լ�)

������ ������ ���α׷��� ����� ����ϴ�. ���� �����ϰ�, �ڵ��� �������� ���� �ϰ� ���� ������ �����ϴ�.
* �ڹٽ�ũ��Ʈ�� ��Ư�� ǥ���� : var numbering = function(){} <- ������ �����Ͽ� �ȿ� �Լ��� ���� ����.  
				 (function(){})(); <- �͸��Լ�



## 3.6 Array (�迭)

```
var arr = ['apple', 'banana', 'cat']; // �ε����� ���� �������� ���� ����� �ٸ� ���α׷��� ���� ����.
arr.length // �迭�� ũ��
arr.push(''); // �迭�� �� ���� �����͸� �߰��Ѵ�.
arr.concat(array); // �ٸ� �迭�� arr �迭�� ���� �̾� ���δ�.
arr.unshift(''); // �迭�� �� �տ� ������ �߰�.
arr.splice(index, ������ ������ ����, ����...); // �迭�� Ư�� ������ �ε������� ���ڷ� ������ ������ŭ
					      // ������ ���Ҹ� �����ϰ� ���ο� ���Ҹ� �����Ѵ�. ������ ���ҵ��� ��ȯ.
arr.shift(); // �迭�� �� �� ��Ҹ� �����ϰ� ��ȯ.
arr.pop(); // �迭�� �� �� ��Ҹ� �����ϰ� ��ȯ.
arr.sort(); // ����, �Ű������� compare �Լ��� �ְ� ���� ����. ���ٸ� �⺻ �������� ����.
arr.reverse(); // �迭�� �Ųٷ� �����´�.
```

## 3.7 Object (��ü)



### 3.7.1 Dictionary (C++ Map�� ����.)

```
var dic = {'apple' : 1, 'banana' : 2, 'cat' : 3}; // ��ü(Dictionary)�� ����, Key : Value
dic['apple'], dic.apple // value�� �����ϴ� �� ���� ǥ�����.
for(key in dic) console.log("key : " + key + ", value : " + dic[key]);
// for(var in Object) <= for in ���� ���� ��ü�� ���� ����.
```



### 3.7.2 ��ü ���� ���α׷���

```
var grades = {
	'list' : {'A' : 100, 'B' : 90, 'C' : 80},
	'show' : function() {
		for (var key in this.list) console.log("key : " + key + ", value : " + this.list[key]);
	}
};
grades.show();
// �� ������ ���α׷����� �����ϴ�. Java���� �޼ҵ带 �����ߴ� ����� JavaScript������ ������ �Լ��� �����Ͽ�
// grades��� ��ü�� �Լ��� ��� �����ϰ� ��� ���� ���� ��� �����ϴ�.
```



## 3.8 �Լ� ���� - ��ȿ����

* ���� ��ȿ���� (Static Scoping) = Lexical Scoping

```javascript
var i = 10;
// a �Լ������� i = 5�� b �Լ��� ������ ��ġ�� ���Ѵ�.
function a(){
    var i = 5;
    b();
}

function b(){
    Console.log(i);
}
```



## 3.9 �Լ� ���� - �����μ��� �Լ��� �ݹ�

JavaScript������ �Լ� ���� ��ü (������ ��)



### 3.9.1 �Լ��� �پ��� ����(�뵵)

```javascript
var a = {
    b : function(){
        
    }
}; // �̷� ������ ������ �Լ� ���� ���� �����ϴ�.

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
// �Լ��� return �����ε� ��� ����

var process = [
    function(input) { return input + 10; },
    function(input) { return input * input; },
    function(input) { return input / 2; }
];
var input = 1;
for(var i = 0; i < process.length; i++) input = process[input];
console.log(input);
// �迭�� �����ε� �Լ��� ���� �����ϴ�.
```



### 3.9.2 Callback

�Լ��� ������ ���� �� �ִ� Ư���� �̿��Ͽ� �Լ��� ���ڷ� �������ָ� ���ڷ� ������ �� �Լ��� ȣ��Ǵ� ���� ���� �����ϰ��� �ϴ� �Լ��� ���� ����� �ٲ� �� �ִ�.

```javascript
var numbers = [20, 10, 9, 8, 7, 6, 5, 4, 3, 2, 1];
var sortFunc = function(a, b) {
    return b - a;
};
console.log(numbers.sort(sortFunc));
// ���� sort �޼ҵ�� �迭�� ���ڵ��� ���ڿ��� ó���ؼ� ���� ������ ������������ ���� ������ ���� �Լ��� �ۼ��Ͽ� ���ڷ�
// �������ְ� �Ǹ� ������ ũ�⸦ ������������ ������ �ȴ�.
```

* Ajax�� ���� �񵿱� ó������ �ݹ��� �����ϰ� ���ȴ�.



## 3.10 �Լ� ���� - Closure

���� �Լ��� �ܺ� �Լ��� Context�� �����ϴ� ����

���� �Լ������� �ܺ� �Լ��� ���� ������ ���� �����ϴٴ� ���� Ư¡.

```javascript
function outter() {
    var title = 'coding everybody';
    function inner() {
        console.log(title);
    }
    inner();
}
outter();
// � Ư���� �ܺ� �Լ� ���ο����� ���� ���� �Լ��� �ܺ� �Լ� �� �ʿ� �Լ��� �����ϰ� �ȴ�.
// inner �Լ����� ���� title ������ ���� �����ϴ�.

function outter() {
    var title = 'coding everybody';
    return function() {
        console.log(title);
    }
}
inner = outter();
inner();
// �ܺ� �Լ��� ������ ������ �ܺ� �Լ��� �Ҹ�� ���Ŀ��� ���� �Լ��� �ܺ� �Լ��� ������ ������ �� �ִ�.
// �̷��� ��Ŀ������ Closure ��� �Ѵ�.
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
ghost.set_title('�����⵿��');
console.log(ghost.get_title());
console.log(matrix.get_title());
// �̿� ���� ������� ���� �Լ��� ���� �ٸ� ��ü�� ���� �� �ִ�.
// �ܺ� �Լ��� ���� ������ title�� ���� �ٸ� ���� ����� ��ü�� ���� �� �ִٴ� ��!
// title ���� private variable�� ���α׷��� �����ϴ�.
```



### 3.10.2 Closure�� �����ϸ� �����ؾ� �� ��

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
// �̷��� �ڵ��ϸ� arr �迭�� ������ ���� 5�� �ȴ�. ����ó�� 0, 1, 2, 3, 4 �� ������� �ʴ� ���� �� �� �ִ�.
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
// �̷��� �迭�� ���� �ܺ� �Լ��� ���� ������ id�� �����ϰ� �� id�� ��ȯ�ϴ� ���� �Լ��� ��ȯ�ϴ� �ܺ� �Լ��� �����ϰ� �Ǹ�
// �迭�� �� �ε������� ���������� �ܺ� �Լ��� private variable ���� ���� �Ǿ�
// 0, 1, 2, 3, 4�� ������ �� �ְ� �ȴ�.
```



## 3.11 �Լ� ���� - Arguments

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
// ��ó�� sum �Լ��� ���ڸ� ���޹޴� �κ��� �������� �ұ��ϰ� 1, 2, 3, 4�� ���ڷ� ������ �� �ִ�.
// ������ ��� �Լ����� arguments��� Ư���� �迭�� �ֱ� �����̴�.

function zero(){
    console.log(
        'zero.length', zero.length, // �Լ��� ���޵� ���� ������ ���� �ǹ�
        'arguments', arguments.length // �Լ��� ���ǵ� ������ ���� �ǹ�
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



## 3.12 �Լ� ���� - �Լ��� ȣ��

�츮�� ����ϴ� �Լ����� ��� Function ��ü�� �ν��Ͻ��̴�. ������ Function ��ü�� ���� �޼ҵ���� ��밡���ѵ�, ȣ�⿡ ���Ǵ� �޼ҵ�� apply�� call�� �ִ�.

```javascript
function sum(arg1, arg2) {
    return arg1 + arg2;
}
console.log(sum.apply(null, [1, 2]));

o1 = {val1 : 1, val2 : 2, val3 : 3}
o2 = {v1 : 10, v2 : 50, v3 : 100, v4 : 25}
function sum(){
    var _sum = 0;
    for(name in this){ // this�� ��ü�� ���ڷ� ����
        _sum += this[name];
    }
    return _sum;
}
console.log(sum.apply(o1)) // 6
console.log(sum.apply(o2)) // 185
```



## 3.13 Object Oriented Programming (��ü ���� ���α׷���)

������ ����(State)�� ����(Behave)�� �����Ͽ� �̸� �ϳ��� ��ü(���� + �޼ҵ�)��� ������ ���α׷����ϴ� �з�����.

* �߻�ȭ
* ��ǰȭ : ����Ʈ��� ��ü ������ �����Ͽ� ��� �ϳ��� ��ɿ� �ش��ϴ� ��ü�� ����, Javascript������ Object
* ���� ����, ĸ��ȭ : ��ü�� �̷��� Ư������ ���´�.
* �������̽� : ������ ��ǰ�� �����ϱ� ���� ������. �̷��� ���������� �׻� ǥ���� �ִ�.
* Javascript�� Prototype-based Programming



## 3.14 ��ü ���� - �����ڿ� new

```javascript
var person = {}; // ��� �ִ� ��ü ���� (Literal Object)
person.name = 'llstaaar';
person.introduce = function() {
    return 'My name is ' + this.name;
};
console.log(person.introduce());
// �� �ڵ�� ��ü�� ����� ������ �л�Ǿ� �����Ƿ� ��ü�� ������ �� ���� �����ϵ��� ����.

var person = {
    'name' : 'llstaaar',
    'introduce' : function() { return 'My name is ' + this.name; }
};
// ������ �� �ڵ� ���� ���� Ư¡�� ���� ��ü�� ������ �� �ڵ��� �ߺ��� ����Ƿ� ���� �ڵ�� �ƴϴ�.
```

- Constructor (������) : ��ü�� ����� ������ �ϴ� �Լ�, ������ �����ϸ鼭 new Ű���带 �ٿ��ָ� �Լ��� ��ü�� �����ڷ� ���Ǵ� ���� �� �� �ִ�.

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



## 3.15 ��ü ���� - Global Object (���� ��ü)

��� ��ü�� window��� ���� ��ü�� ������Ƽ�̴�. (Node.js������ global)



## 3.16 ��ü ���� - this

* this : �Լ� �������� �Լ� ȣ�� �ƶ�(Context), Javascript������ �Լ��� ��ü�� ������ ���踦 ��������ִ� ������ �ϴ� Ű����, �Լ��� ��� ȣ���ϴ��Ŀ� ���� this�� ����Ű�� ����� �޶�����.

```javascript
this === window; // true, �򹮿����� this�� ���� ��ü�� window�� ����Ų��.
var o = {
    func : function() {
        if(o === this) console.log("o === this");
    } // ��ü�� ���ϴ� �޼ҵ��� this�� �� ��ü�� ����Ų��.
};

// ������(�Լ�) �ȿ� �ִ� this�� �Լ��� ȣ����� ���� ���� ��ü�� window�� ����Ű��
// �����ڷ� ������ ���� �����Ǵ� ��ü�� ����Ű�� �ȴ�.

function sum1(x, y) { return x + y; }
var sum2 = new Function('x', 'y', 'return x + y;'); // ��ü�μ� �Լ��� ����

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
func(); // �Լ��� �׳� ȣ������ ������ this === window
func.apply(o); // apply �޼ҵ带 ���� o ��ü�� ���ڷ� �����Ͽ� �Լ��� ȣ���ϸ� this === o
func.apply(p); // apply �޼ҵ带 ���� p ��ü�� ���ڷ� �����Ͽ� �Լ��� ȣ���ϸ� this === p
```



## 3.17 ��ü ���� - Inheritance (���)

����� ���� ��ü�� ������ �״�� �����޴� �� �ٸ� ��ü�� ���� �� �ִ�.

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
// prototype�̶�� Ư���� Property�� ��ӹ��� ��ü�� �����Ͽ� �����ϸ� Person ��ü��
// prototype property�� �������� ���� ��ü�� �����Ͽ� �Ѱ��ִ� ���

Programmer.prototype.coding = function () { return 'Hello, World!'; };
// prototype property�� ���� ���ο� property�� method���� �߰����� �� �ִ�.

var p2 = new Programmer('llstaaar');
console.log(p2.introduce());
```

* prototype : 