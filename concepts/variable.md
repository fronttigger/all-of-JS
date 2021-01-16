---
description: 자바스크립트에서 변수를 다루기 위한 개념을 살펴보겠습니다.
---

# 변수

![](../.gitbook/assets/datatype.png)

## 🤔 데이터 타입이란 무엇인가요?

데이터 타입은 말 그대로 **데이터의 타입**을 표현하는 역할을 합니다. 하나의 애플리케이션을 구현하기 위해서는 정말 많은 데이터가 필요할 것입니다. 이 많은 데이터들은 각각 본인의 타입을 가지게 되고, 이를 활용하여 목적에 맞는 역할을 수행하게 되는 것이죠

자바스크립트에는 **7개**의 데이터 타입을 통해 타입을 관리하고 있습니다.  
한 번 살펴보겠습니다.

## 💾 자바스크립트의 데이터 타입들

데이터 타입은 원시 타입\(primitive type\)과 객체 타입\(object type\)으로 구분되어집니다.  
두 가지는 어떤 차이가 있을까요 ?

| 구분 | 데이터 타입 | 설명 |
| :--- | :--- | :--- |
| 원시 타입 | 숫자\(number\) | 모든 숫자 타입 |
| 원시 타입 | 문자\(string\) | 문자로 된 타입 |
| 원시 타입 | 불리언\(boolean\) | 참\(true\) / 거짓\(false\) 타입 |
| 원시 타입 | undefined | var로 선언된 변수에 초기화 단계에 할당되는 타 |
| 원시 타입 | null | 값이 없는 타입 |
| 원시 타입 | symbol | 유일한 값의 타입 |
| 객체 타입 | object, function, array... | 원시 타입을 제외한 객체 타입 |

표를 보시면 객체타입은 하나로 분류가 되었고 나머지는 각각 하나의 타입을 가지고 있다는 것입니다.  
쉽게 생각한다면 객체 타입을 제외하면 나머지는 하나의 고유한 자신만의 타입을 가지고 있다는 것이죠  
  
이제 하나씩 타입들을 살펴보며 어떤 타입인지 알아보겠습니다. 

### 1. 숫자 타입

자바스크립트의 숫자는 타 프로그래밍 언어와는 다르게 **64비트 부동소수점** 방식을 따르고 있습니다. 즉, **실수**로만 표현한다는 것이죠  
  
실제로 다양한 종류의 수를 입력해도 실수로 표현됩니다.

```javascript
var integer = 10; // 정수
var double = 20.10; // 실수
var negative = -10; // 음의 정수

var binary = 0b01000001; // 2진수 65
var octal = 0o101 // 8진수 65
var hex = 0x41; // 16진수 65
```

그래서 어떠한 숫자값과 비교해도, 실수로서 비교하기 때문에 값이 동일하다면 **참**인 판단이 출력됩니다.

```javascript
console.log(binary === octal) // true
console.log(octal === hex) // true
console.log(1 === 1.0) // true
```

또한 숫자가 무한대거나, 숫자로서 연산 작업을 할 수 없을 때 사용하는 값도 존재합니다. 

* Infinity : 양수로서 값이 무한대
* -Infinity : 음수로서 값이 무한대
* NaN : 연산이 불가한 값

```javascript
console.log(10 / 0) // Infinity
console.log(10 / -0) // Infinity
console.log(10 * "hello") // NaN
```

### 2. 문자열 타입

문자열 타입은 말 그대로 **텍스트**를 타입으로 가지는 타입입니다. 작은 따옴표\(' '\), 큰 따옴표\(" "\), 백틱\(\` \`\)으로 감싼 대상으로 하여 문자열 타입을 부여합니다.

```javascript
var nickname;
nickname = 'tigger'; // 작은 따옴표
nickname = "tigger"; // 큰 따옴표
nickname = `tigger`; // 백틱

nickname = tigger // ReferenceError: tigger is not defined
```

위 세 가지 방법으로 감싸게 되면 nickname은 문자열 타입을 가지게 됩니다.  
만약 따옴표를 통해 문자열을 선언하지 않게 되면, 자바스크립트 엔진은 이걸 문자열이라고 인지하지 못하고 **식별자**로 인식하기 때문에 꼭 따옴표로 묶어주어야 합니다. 

여기서 따옴표 시리즈와는 다르게 **백틱**은 ES6 이후에 새롭게 추가된 문법으로 **템플릿 리터럴\(template literal\)**을 통해 보다 편하게 문자열을 다룰 수 있게 해줍니다. 차후 ES6 문법을 주제로 알아보도록 하겠습니다.

### 3. 불리언 타입

불리언 타입은 true 혹은 false로 구분되어진 타입입니다.  
값이 참이라면 true를, 값이 거짓이라면 false로 표현되어집니다.

```javascript
const isTrue = true
console.log(isTrue) // true

const isFalse = false
console.log(isFalse) // true
```

불리언 타입은 **조건문**이나 **Flag\(깃발\)** 요소 처럼 특정 조건이 만족할 때 비즈니스 로직을 실행하는 부분에서 굉장히 많이 활용이 되는 타입입니다.

### 4. undefined

undefined는 **"자료형이 정해지지 않은 상태"**를 말합니다. 이전 변수에서도 잠깐 살펴봤지만, 자바스크립트 엔진이 var로 변수를 선언하게 되면 초기화 단계까지 함께 일어나며 자동으로 undefined를 할당하게 됩니다.

```javascript
var coffee;
console.log(coffee); // undefined
```

자바스크립트 엔진이 자동으로 undefined를 할당해 주기 때문에 개발자들이 만약 수동으로 undefined를 할당해주는 것은 필요 없는 코드를 작성한 것일 뿐만 아니라 해당 데이터를 파악하는데 있어 혼동을 야기할 수 있기 때문에 권장하는 방법은 아닙니다.

### 5. null

null은 타 프로그래밍 언어와 동일하게 **값이 없다**는 것을 의미합니다.  
값이 없는 것은 해당 변수가 더이상 자바스크립트 엔진이 볼 필요가 없어진다는 의미이고 차후 가비지 컬렉터에 의해 정리할 대상이 되기도 합니다.

```javascript
var nickname = "tigger";
console.log(nickname); // tigger

nickname = null;
console.log(nickname); // null
```

 위 처럼 값을 가지고 있다가 필요가 없을 때 null을 선언하여 참조하는 값을 없애기도 합니다.

