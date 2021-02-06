---
description: 자바스크립트에서 객체를 다루기 위한 개념을 살펴보겠습니다.
---

# 객체

![](../.gitbook/assets/object.png)

## 🤔 객체란 무엇인가요?

자바스크립트에서 **객체**는 가장 기본이며, 그 기본 중에서도 핵심이라고 볼 수 있습니다.  
그 이유는 바로 자바스크립트가 객체기반의 언어이기 때문이죠

이전에도 데이터 타입에서 보았지만, **원시값을 제외**한 모든 것이 **전부 객체 타입**으로 분류가 되어있습니다.  
즉, 원시값이 아니라면 다 객체로 보기 때문에 이를 잘 이해해야한다는 것이죠!

객체에서는 **프로퍼티\(property\)**라는 값을 관리하며, 이 프로퍼티는 **key**와 **value**를 관리하게 됩니다.  
이전부터 지속적으로 프로그래밍을 해보셨다면 자료구조를 통해 이해하실 수 있지만, 프로그래밍이 처음이라면 아직은 이해가 잘 가지 않을 것입니다.

쉽게 표현을 하자면..  
객체는 집, 프로퍼티는 사람, key와 value는 양 팔이라고 생각하고 객체를 처음 맞이하시면 조금 다가가기 쉬울 것 같습니다.

이번 시간을 통해서 객체가 어떤 것인지 살펴보고 공부해보겠습니다! ✍️

## 🔨 객체를 어떻게 만드나요?

자바스크립트에서 객체를 만드는 방법에는 정말 여러가지가 있습니다.

* 객체 리터럴
* Object 생성자 함수
* 생성자 함수
* Object.create 메서드
* 클래스

위처럼 정말 많은 방법들이 있지만, 보통 가장 간단하면서 많이 사용 되는 방법이 바로 **객체 리터럴** 방식입니다.

그 이유는, 객체 리터럴 방식이 자바스크립트의 **유연함**을 가장 잘 표현하는 객체 생성 방식이며, 따로 **new 연산자**를 통해 객체를 해야한다던지, **선행작업 없이** 바로 생성할 수 있기 때문입니다.

그렇다면 이 객체 리터럴은 어떻게 만들어야 할까요?  
서론은 길었지만 정말 간단하게 만들 수 있습니다.

```javascript
var person = {}; // 빈 객체 생성
```

이게 person 이라는 객체를 생성한 것입니다. 정말 간단하지 않나요?  
이제 위에서 설명한 프로퍼티를 알아볼까요?

## 🗂 객체는 어떻게 구성이 되어있나요?

객체는 아까 **프로퍼티**라는 값을 관리한다고 말씀 드렸었죠? 즉, **프로퍼티**들을 통해 객체를 구성하게 됩니다.  
또한 프로퍼티는 자바스크립트의 **모든 값**을 다룰 수 있습니다. 😮  
그럼 프로퍼티들을 하나씩 생성해볼까요?

### 1. 프로퍼티

프로퍼티는 key와 value를 통해 선언하게 됩니다. 그래서 key는 객체 내에서 식별자 역할을 하며, value는 그 식별자의 값을 나타내는 역할을 해줍니다. 한 번 코드로 보겠습니다.

```javascript
var person = {
    name: 'tigger', // key: name, value: 'tigger'
    age: 29 // key: age, value: 29
};
```

코드를 보시면 총 2개의 프로퍼티를 person 객체에 선언한 모습입니다.  
이처럼 **두개 이상**의 프로퍼티가 있으면 **쉼표\(,\)**로 구분하여 선언해주게 됩니다.

#### 네이밍 규칙

여기서 중요한 점은 **key** 입니다.  
객체에서 key는 정해진 **네이밍 규칙**이 존재합니다. 만약 이를 따르지 않게 되면 보고싶지 않은 오류를 직면하게 되죠.. 😂

```javascript
var person = {
    name: 'tigger',
    first-name: 'kim', // SyntaxError: Unexpected token
    age: 29,
};
```

미들바\(-\)가 들어간 순간 객체에서는 이를 판독하지 못하고 문법 에러를 뱉어내버립니다..  
즉, 여기서 알 수 있는 것은 key는 **문자열**을 통해 선언하고 식별해야 한다는 것입니다.

그래서 위의 에러를 해결하기 위해서는 **문자열**로 선언을 하면 에러가 해결됩니다.  
하지만 그렇게 되면 통일성도 없고, 번거롭기 때문에 보통 CamelCase를 활용해 key를 선언합니다.

```javascript
var person = {
    name: 'tigger',
    'first-name': 'kim', // 잘 사용하지 않음
    lastName: 'junhyeoung',
    age: 29,
};
```

이렇게 되면 key를 크게 신경쓰지 않고 선언할 수 있습니다.

#### 프로퍼티가 중복된다면?

그리고 중요한 객체의 특징 중 하나는 프로퍼티는 **중복된 key**를 가질 경우, **나중에 선언된 key**에 전부 먹혀버린다는 것입니다.

```javascript
var person = {
    name: 'tigger',
    lastName: 'junhyeoung',
    age: 29,
    name: '김준형',
};

console.log(person); // {name: "김준형", lastName: "junhyeoung", age: 29}
```

이걸 활용하여 나중에는 객체 내의 **프로퍼티 값을 변경**하는 등의 핸들링에 활용되니 꼭 기억해야 되는 개념입니다.

### 2. 메소드

아까 프로퍼티는 모든 값을 다룰 수 있다고 했었죠? 그렇다면 위에서 본 값들과 마찬가지로 함수 또한 사용할 수 있다는 것입니다. \(함수는 아직 다룬 부분이 아니기 때문에 다룰 수 있다는 점에 집중해주시면 됩니다.\)

객체에서 함수를 메소드라고 하는 이유는, 기존 프로퍼티들과 혼동되지 않도록 이름을 따로 붙여준 것입니다.  
한 번 살펴보겠습니다.

```javascript
var person = {
    name: 'tigger',
    lastName: 'junhyeoung',
    age: 29,
    getName() { // 메소드 선언
        return this.name; // this는 person 객체를 가리킵니다.
    }
};

console.log(person.getName()); // 'tigger'
```

여기서 함수 문법인 괄호, 그리고 this가 나오지만 아직 전혀 모르셔도 되는 부분입니다.  
여기서 결론은 **메소드 또한 프로퍼티**가 될 수 있다는 것입니다.

## 💻 만든 객체는 어떻게 사용해야 하나요?

이전까지 우리는 객체와 프로퍼티들을 만드는 코드를 작성해보았습니다. 이렇게 만들어진 객체를 우리는 사용을 해야할텐데, 만약 사용을 해야한다면 먼저 **접근**을 해야하겠죠? 그리고 접근 후에는 프로퍼티를 다루어야 할 것입니다.

### 1. 프로퍼티 접근

프로퍼티에 접근하기 위해서는 총 2가지의 방식이 있습니다.

* 마침표\(.\)를 활용한 접근법
* 대괄호\(\[...\]\)를 활용한 접근법

여기서 가장 중요한 점은 **대괄호**를 사용하여 프로퍼티를 접근할 때는 반.드.시. **따옴표\(' '\)**로 감싸고 프로퍼티 key에 접근해야만 한다는 것입니다.

```javascript
var person = {
    name: 'tigger',
    lastName: 'junhyeoung',
    age: 29,
    getName() { 
        return this.name;
    }
};

console.log(person.name); // 'tigger'
console.log(person['age']); // 29
consolg.log(person[age]) // Uncaught ReferenceError: age is not defined
console.log(person['fullName']); // undefined
```

**접근법을 준수하지 않고** 접근하게 되면 age라는 식별자를 찾지 못하는 **레퍼런스 에러**를 마주하게 됩니다.  
또한 접근법으로 **객체에 없는 프로퍼티**에 대해 접근하려고 하면 에러가 나는 것이 아닌 **undefined**가 출력되기 때문에 이 두가지의 에러 케이스를 잘 구분할 필요가 있습니다. 🥶

### 2. 프로퍼티 수정\(갱신\)

프로퍼티에 잘 접근했다면, 이를 수정할 필요성도 있겠죠?  
그냥 접근법을 통해 접근한 후, 대입 연산자를 통해 바꾸어주면 됩니다. 참 쉽죠?

```javascript
var person = {
    name: 'tigger',
    lastName: 'junhyeoung',
    age: 29,
    getName() { 
        return this.name;
    }
};

person.name = 'fronttigger';

console.log(person.name); // fronttigger
```

### 3. 프로퍼티 생성

우리가 프로퍼티에 접근 할 때, 접근법을 준수했다는 가정하에 없는 프로퍼티에 접근하면 **undefined**가 출력된다고 했었죠? 그렇다는 것은 우리가 프로퍼티를 수정할 때 처럼 **undefined에 값을 대입**하면 되면 그 값이 들어갈 것입니다.  
한 번 해보겠습니다.

```javascript
var person = {
    name: 'tigger',
    lastName: 'junhyeoung',
    age: 29,
    getName() { 
        return this.name;
    }
};

person.fullName = 'kimjunhyeoung';

console.log(person.fullName); // 'kimjunhyeoung'
```

### 4. 프로퍼티 삭제

객체에 프로퍼티가 필요가 없어지는 경우도 있겠죠?  
delete 연산자를 통해 간단하게 삭제할 수 있습니다.

```javascript
var person = {
    name: 'tigger',
    lastName: 'junhyeoung',
    age: 29,
    getName() { 
        return this.name;
    }
};

delete person.lastName;

console.log(person); // {name: "tigger", age: 29, getName: ƒ}
```



