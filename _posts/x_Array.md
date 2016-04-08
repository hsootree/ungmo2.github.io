#Array
배열(array)는 1개의 변수로 여러 개의 값을 순차적으로 저장할 때 사용한다.

자바스크립트의 배열은 객체이며 매우 유용한 내장 메서드를 포함하고 있다.

##배열 리터럴
0개 이상의 값을 쉼표로 구분하여 대괄호로 묶는다. 첫번째 값은 속성 '0'으로 읽을 수 있다.

존재하지 않는 요소에 접근하면 `undefined`를 얻게 된다.

```javascript
var empty = [];

var numbers = [
  'zero', 'one', 'two', 'three', 'four',
  'five', 'six', 'seven', 'eight', 'nine'
];

empty[1]        // undefined

numbers[1]      // 'one'

empty.length    // 0

numbers.length  // 10
```

위의 예를 객체 리터럴로 유사하게 표현하면 다음과 같다.

```javascript
var numbers_object = {
  '0': 'zero',  '1': 'one',   '2': 'two',
  '3': 'three', '4': 'four',  '5': 'five',
  '6': 'six',   '7': 'seven', '8': 'eight',
  '9': 'nine'
};
```

`numbers`와 `numbers_object`는 모두 10개의 속성을 가지고 있고, 각 속성은 모두 같은 이름과 값이 있다.

두 객체의 근본적 차이는 `numbers`는 `Array.prototype`을 상속받았으나 `numbers_object`는 `Object.prototype`을 상속 받았다는 것이다.

`Array`객체는 다양한 메서드(e.g. `sort`)와 속성(e.g. `legth`)을 제공한다.

대부분의 언어에서 배열의 요소들은 모두 같은 데이터 타입이어야 하지만, 자바스크립트 배열은 어떤 데이터 타입의 조합이라도 포함할 수 있다.

```javascript
var misc = [
  'string', 98.6, true, false, null, undefined, ['nested', 'array'], {object: true}, NaN, Infinity
];

misc.length   // 10
```

##`length`속성
현재 `length`보다 더 큰 인덱스로 항목을 추가하면 `length`는 새로운 항목을 추가할 수 있도록 늘어난다.

```javascript
var myArray = [];
myArray.length    // 0

myArray[1000000] = true;  
// --> [ , , ... , , true ]

myArray.length    // 1000001
myArray[0]        // undefined
```

`length` 값은 명시적으로 설정할 수 있다. 만약 `length` 값을 현재 보다 작게 설정하면 설정한 값보다 크거나 같은 인덱스에 해당하는 요소는 모두 삭제된다.

```javascript
var numbers = [
  'zero', 'one', 'two', 'three', 'four',
  'five', 'six', 'seven', 'eight', 'nine'
];

// 배열 길이의 명시적 설정
numbers.length = 3;
// --> [ 'zero', 'one', 'two' ]

// 배열 끝에 새 요소 추가
numbers[numbers.length] = 'shi';
// --> [ 'zero', 'one', 'two', 'shi' ]

// 배열 끝에 새 요소 추가
numbers.push('go');
//--> [ 'zero', 'one', 'two', 'shi', 'go' ]
```

##delete
자바스크립트 배열은 객체이기 때문에 배열의 요소를 삭제하느데 `delete` 연산자를 사용할 수 있다.

```javascript
// 요소의 값만 삭제된다
delete numbers[2];
// --> ['zero', 'one', undefined, 'shi', 'go']

// 요소 일부를 삭제 (배열 시작점, 삭제할 요소수)
numbers.splice(2, 1);
// --> ['zero', 'one', 'shi', 'go']
```

##열거

```javascript
for (var i = 0; i < numbers.length; i++) {
  document.writeln(numbers[i]);
}
```

`for in` 문은 요소들의 순서를 보장하지 않으므로 배열을 열거하는데 적합하지 않다.

##Method
####array.concant(item...)
자신의 복사본에 인수로 넘어온 값들을 추가한 새로운 배열을 반환한다.

```javascript
var a = ['a', 'b', 'c'];
var b = ['x', 'y', 'z'];

var c = a.concat(b);
// --> ['a', 'b', 'c', 'x', 'y', 'z']

var d = a.concat('String');
// --> ['a', 'b', 'c', 'String']

var e = a.concat(b, true);
// --> ['a', 'b', 'c', 'x', 'y', 'z', true]
```

####array.join(separator)
배열로 문자열을 만든다. 기본구분자는 ','이다.

`join` 메서드가 `+` 연산자보다 빠르다.

```javascript
var a = ['a', 'b', 'c'];
a.push('d');
var c = a.join();     // --> 'a,b,c,d';
var d = a.join('');   // --> 'abcd';
var e = a.join(':');  // --> 'a:b:c:d';
```

####array.pop( )
`pop`과 `push` 메서드는 배열을 스택처럼 동작하게 한다.
`pop` 메서드는 배열에서 마지막 요소를 제거하고 제거한 요소를 반환한다. 만약 빈 배열일 경우 `undefined`를 반환한다.
```javascript
var a = ['a', 'b', 'c'];
var c = a.pop( );
// a --> ['a', 'b']
// c --> 'c'
```

####array.push(item…)
`push` 메서드는 인수로 넘어온 항목을 배열의 끝에 추가한다. `concat` 메서드와 다르게 배열 자체를 수정하여 넘어온 인수 전체를 배열에 추가한다. 반환값은 배열의 새로운 `length` 값이다.

```javascript
var a = ['a', 'b', 'c'];
var b = ['x', 'y', 'z'];
var c = a.push(b, true);
// a --> ['a', 'b', 'c', ['x', 'y', 'z'], true]
// c --> 5;
```

배열의 마지막에 값을 추가 할 때는 `push`, 선두에 추가 할 때는 `unshift`, 중간에 추가할 때는 `splice` 메서드를 사용한다.

단, `push`, `unshift` 메서드는 사용하기 간편하나 performance 면에서는 좋은 방법은 아니다.

```javascript
var arr = [1,2,3,4,5];

arr.push(6);
arr[arr.length] = 6; // 43% faster in Chrome 47.0.2526.106 on Mac OS X 10.11.1

arr.unshift(0);
[0].concat(arr); // 98% faster in Chrome 47.0.2526.106 on Mac OS X 10.11.1
```
####array.reverse( )
배열 요소의 순서를 반대로 변경한다. 반환값은 배열이다.

```javascript
var a = ['a', 'b', 'c'];
var b = a.reverse( );
// a,b --> ['c', 'b', 'a']
```

####array.shift( )
배열에서 첫요소를 제거하고 제거한 요소를 반환한다. 만약 빈 배열일 경우 `undefined`를 반환한다.

```javascript
var a = ['a', 'b', 'c'];
var c = a.shift( );
// a --> ['b', 'c']
// c --> 'a'
```

####array.slice(start, end)
배열의 특정 부분에 대한 복사본을 생성한다.
첫번째 매개변수 start에 해당하는 인덱스를 갖는 요소부터 매개변수 end에 해당하는 인덱스를 가진 요소 전까지 복사된다. 매개변수 end는 옵션이며 기본값은 `length`값이다.

```javascript
var a = ['a', 'b', 'c'];
var b = a.slice(0, 1);  // b --> ['a']
var c = a.slice(1);     // c --> ['b', 'c']
var d = a.slice(1, 2);  // d --> ['b']
```

####array.splice(start, deleteCount, item…)
기존의 배열 요소를 제거하고 그 부분을 새로운 항목으로 대체한다.
매개변수 start는 배열에서의 위치이며 매개변수 deleteCount는 시작점부터 삭제할 요소수이다. 매개변수 item은 옵션이며 삭제한 위치에 추가될 요소들이다. 반환값은 삭제한 요소들을 가진 배열이다.

이 메서드의 가장 일반적인 사용은 배열에서 요소를 삭제할 때다.

```javascript
var a = ['a', 'b', 'c'];
var r = a.splice(1, 1, 'ache', 'bug');
// a --> ['a', 'ache', 'bug', 'c']
// r --> ['b']
```

배열 중간에 새로운 값을 추가할 때도 사용된다.

```javascript
var items = ['one', 'two', 'three', 'four'];
items.splice(2, 0, 'hello');

// items --> [ 'one', 'two', 'hello', 'three', 'four' ]
```

####array.sort(comparefn)
배열의 내용을 적절하게 정렬한다.

```javascript
var fruits = ["Banana", "Orange", "Apple", "Mango"];

// The sort() method sorts the items of an array.
// ascending
fruits.sort();
console.log(fruits); // [ 'Apple', 'Banana', 'Mango', 'Orange' ]

// descending
fruits.reverse();
console.log(fruits); // [ 'Orange', 'Mango', 'Banana', 'Apple' ]

var points = [40, 100, 1, 5, 25, 10];

points.sort();
console.log(points); // [ 1, 10, 100, 25, 40, 5 ]

// Syntax : array.sort(compareFunction)

// Sort numbers in an array in ascending order:
points.sort(function(a, b){return a-b});
console.log(points); // [ 1, 5, 10, 25, 40, 100 ]

// Get the lowest value in an array:
console.log(points[0]); // 1

// Sort numbers in an array in descending order:
points.sort(function(a, b){return b-a});
console.log(points); // [ 100, 40, 25, 10, 5, 1 ]

// Get the highest value in an array:
console.log(points[0]); // 100
```

##Reference  

* [JavaScript : The Good Parts - 06.배열](http://www.yes24.com/24/goods/3071412?scode=032&OzSrank=1)  