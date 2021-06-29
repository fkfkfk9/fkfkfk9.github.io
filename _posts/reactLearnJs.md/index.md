---
title: 리엑트를 배우기전 알아야할 javascript 개념
date: 2021-05-10 22:10:33
tags: [react, javascript]
categories: [react, javascript]
---

---

# 리엑트를 배우기전 알아야할 javascript 개념

## Arrow function

Arrow Function은 ES6에서 새로 등장한 기능으로 일반적인 함수에 비해 구문이 짧고 this, agrs, super, target를 바인딩 하지 않으며 항상 익명함수이다.

#### 일반함수

```javascript
function sum(num1, num2) {
  return num1 + num2;
}
```

#### Arrow Function

```javascript
const sum = (num1, num2) => num1 + num2;
```

일반함수는 return을 표기하지 않으면 제대로 된 결과를 받을 수 없지만 Arrow function은 다로 return을 표기하지 않아도 return된다.

```javascript
addEventListener("click", (event) => alert("event"));
```

기존에 익명함수를 넣어서 더럽게 보였던 코드를 깔끔하게 표현할 수 있다.
위 화면처럼 매개변수가 **event**하나라면 `()`를 표시하지 않고 작성이 가능하다.

---

## Default 값

```javascript
function sum(num1 = 33, num2 = 22) {
  return num1 + num2;
}
```

함수에서 매개변수를 넘겨주지 않는다면 원하는 결과를 받을 수 없는게 정상이지만 매개변수에 값을 셋팅해준다면 default로 해당 값들을 호출하여 결과가 나온다.
이 기능은 Arrow Function에서도 사용 가능하다.

---

## Template literals

내장된 표현식을 허용하는 문자열 리터럴이다. 기존처럼 `'`, `"`로 감싸는 게 아닌 \`로 감싸준다.

```javascript
function printStr(str) {
  `${str}을 출력합니다.`;
}
```

기존의 문자열 저장 방식과 다른점은 변수들을 `+`기호로 더해줄 필요없이 하나의 구문에 변수까지 `${}`로 감싸주어 표현이 가능하다는 점이다.

---

## Javascript 객체 Destructuring

ES5에서 Destructuring하기 위해선 `obj.key`방식으로 데이터를 호출해야 했다.
Es6에서는 객체의 각 프로퍼티를 책체로부터 추출하여 변수 리스트에 할당한다.

#### ES5

```javascript
const obj = {name = "Yoo", age = 34, gender = "M"}
var name = obj.name;
var age = obj.age;
```

#### ES6

```javascript
const obj = {name = "Yoo", age = 34, gender = "M"}
const {name, age, gender:sex} = obj;
```

여기서 `{}` 안에 들어가는 값은 key와 일치해야 하는데 변수명을 변경하고 싶다면 gender처럼 변경해주면 된다.

---

## Spread Operator

Spread Operator를 사용하면 배열이나 문자열과 같이 반복 가능한 객체를 개별요소로 분리시킬 수 있다.

```javascript
const arr1 = [1, 2, 3];
const arr2 = [4, 5, 6];

const arr_plus = [...arr1, ...arr2];
```

위처럼 코딩한다면 arr_plus는 `[1,2,3,4,5,6]`이 된다.
하나의 배열로서 각각의 요소가 들어와 더해지는 것이다.
이는 배열뿐 아니라 Object에서도 마찬가지로 적용된다.

---

## Class

Javascript는 원래 class가 없지만 ES6에서 Class를 제공한다. 그리고 React의 컴포넌트는 모두 Class로 되어있기 때문에 그 개념을 알아야 한다.

```javascript
class unit {
  constructor(name, strength) {
    this.name = name;
    this.strength = strength;
  }
}

class marin extends unit {
  attack() {
    console.log("Attack!!!");
  }
}
```

class의 경우 자바를 해본사람이라면 익숙할것이다.
다른점이라면 생성자에 클래스명이 아닌 constructor로 정의해준다는 점이다.
상속받아 부모의 값을 호출한다던지 extends가 가능한점 등 자바와 매우 유사하다.

---

## Array Map

배열 변수의 map메서드는 배열의 각 요소들에 접근할 수 있다.
map메서드 안에 익명함수를 넣는다면 마치 forEach를 사용한것처럼 각각의 배열 요소들에 반복작업을 할 수 있다.

```javascript
const numbers = [1, 2, 3, 4, 5, 6, 7];
numbers.map((number) => console.log(number));
```

위처럼 코딩을 한다면 number은 numbers 배열의 각각의 값으로서 출력된다.
그럼 forEach가 있는데 왜 map이 있는지 의아할탠대 forEach가 각 요소들로 작업을 하는걸로 끝난다면 map은 배열의 형태로 리턴해준다.
위의 코드는 단순 출력이니 사실 forEach를 사용해주는것이 맞고 모든 배열 요소에 같은 작업을 하여 새로운 배열로 리턴해야한다면 map을 사용해야 한다.
위에 나온 대부분의 내용들은 IE에서 호환되지 않으나 map은 호환이 가능하므로 다양한 개발 환경에서 유용할듯 하다.

---

## Array Filter

map이 각각의 요소들로 작업을 했다면 filter은 배열에서 특정조건의 데이터들을 배열의 형태로 리턴해준다.

```javascript
const numbers = [1, 2, 3, 4, 5, 6, 7];
const bigNumbers = numbers.filter((number) => 3 < number);
console.log(bigNumbers);
```

map과 비슷하지만 filter은 배열의 값 중 3보다 큰 숫자들만 리턴하여 새로운 배열로 변수에 들어가지만 map으로 했다면 number을 3과 비교하여 true, false로 리턴해준다.
즉 map은 각각의 배열요소들로 작업을 해준다면 filter은 배열의 요소 중 원하는 데이터를 걸러준다.
filter 또한 IE에서 지원하니 꼭 사용해봐야겠다.

---

## 그외 유용한 기능들

위에 나온대로 배열 뒤에 `forEach()`를 사용한다면 각각의 요소들을 반복하면서 작업할 수 있고 `push()`를 사용한다면 배열에 새로운 데이터를 추가할 수 있다.
`include()`를 사용한다면 해당 배열에 있는 데이터를 비교검사하여 true/false로 리턴해준다.
이 외에도 mdn사이트에서 js에 관련된 여러 함수를 조회할 수 있으니 찾아야 하는 기능들이 있다면 검색해보면 된다.
