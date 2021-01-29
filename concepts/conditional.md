---
description: 자바스크립트에서 조건문을 다루기 위한 개념을 살펴보겠습니다.
---

# 조건문

![](../.gitbook/assets/conditional.png)

## 🤔 조건문이란 무엇인가요?

조건문은 **특정 조건\(조건식\)**에 따라서 구분한 로직을 **조건의 평가\(조건식의 결과\)**에 따라 실행을 결정하는 역할을 해줍니다. 이 때, 조건은 우리가 이전에 다루었던 타입 중, **불리언 타입**으로 평가가 됩니다.  
물론 평가 자체를 무조건 불리언 타입으로 평가를 하는 것은 아니지만, 평가를 할 때는 평가 값을 **불리언 타입으로 강제 변경**하여 평가하게 됩니다. \(이 부분에 대해서는 따로 다루도록 하겠습니다.\)

자바스크립트의 조건문은 타 프로그래밍 언어와 동일하게 **if-else**문, 그리고 **switch**문 두 가지를 제공합니다.  
한 번 살펴보겠습니다.

## 🔍 조건문의 종류엔 어떤 것이 있나요?

### 1. if - else

**if-else**문은 프로그래밍 언어를 한 번이라도 다루어본 사람이라면 정말 익숙한 조건문입니다.  
특정 조건을 입력하고 그에 맞춰서 **블록 단위\(block scope\)**로 구분된 조건식의 대상\(로직\)이 실행되는 구조로 이루어져 있습니다.

기본적인 구조는 아래와 같습니다.

```javascript
// if-else (조건이 1개일 때)
if (조건식) {
    // 조건식이 참일 때
} else {
    // 조건식이 거짓일 때
}

// if-elseif-else (조건이 2개 이상일 때)
if (조건식1) {
    // 조건식1이 참일 때
} else if (조건식2) {
    // 조건식2이 참일 때    
} else if (조건식3) {
    // 조건식3이 참일 때
} else {
    // 조건식들이 모두 거짓일 때
}
```

기본적인 구조는 정말 간단합니다. 개념도 사실 크게 어려운것은 없습니다.  
해당 조건식이 참이라면 그 **조건식에 해당되는 블럭**의 로직이 실행되는 것이죠  
  
하지만 이렇게 문법만 봐서는 뭔가 확 와닿지 않을 것입니다.  
예제를 한 번 보겠습니다.

```javascript
var nickname = 'tigger';
var age = 29;

if (nickname === 'tigger') {
    console.log('tigger가 맞습니다.'); // 출력
} else {
    console.log('tigger가 아닙니다.');
}

if (age > 40) {
    console.log('tigger는 40대 입니다.');
} else if (age > 30) {
    console.log('tigger는 30대 입니다.');
} else {
    console.log('tigger는 20대 입니다.'); // 출력
}
```

nickname이 tigger인지 확인하는 조건식을 통해서 참인 값을 얻어냈습니다.  
참일 경우에 **참에 해당되는 블록**의 로직이 실행되겠죠?  
하지만 age의 경우에는 첫 번째 조건식과 두 번째 조건식 모두 만족하지 못하고 결국 전체가 거짓일 때 실행되는 블록이 실행되게 됩니다.

### 2. switch

**swtich** 문은 표현식을 판별해서 해당 표현식과 **일치**하는 로직을 실행하는 역할을 합니다.  
**case**를 통해서 표현식을 구별하고, 만약 case에 해당되지 않는 표현식이라면, **default**에 해당되는 로직을 실행하게 됩니다.

기본적인 구조를 보겠습니다.

```javascript
switch (표현식) {
    case 표현식1: 
      표현식1 해당되는 로직;
      break;
    case 표현식2:
      표현식2 해당되는 로직;
      break;
    default:
      표현식과 일치하는 case 없을 경우 해당되는 로직;
}
```

구조를 보면 switch, case, break 이 세가지가 보일 것입니다.  
예제를 통해 하나씩 알아보겠습니다.

```javascript
var name = "junHyeoung"
var nickname;

switch (name) {
    case "seokjin":
    nickname = "olaf";
    break;
    case "junHyeoung":
    nickname = "tigger";
    break;
    case "seungbum":
    nickname = "corn";
    break;
    default:
    nickname = null;
}

console.log(nickname); // tigger;
```

switch를 통해 switch문을 사용할 것이라는 것을 알려줍니다.  
이제 본격적으로 표현식을 걸러내봐야겠죠? 이 때 걸러 낼 때 사용하는게 **case**입니다.  
name 이라는 표현식이 들어왔을 때, 해당 표현식에 걸릴 케이스를 분류하는 역할을 하는 것입니다.  
여기서 가장 중요한 친구는 **break**입니다.

break의 역할은 해당 표현식이 case에서 걸러지게 되면 해당 블록의 로직을 실행하고 **switch문을 중단**하고 조건 판별을 **마무리** 합니다.  
즉, break는 우리가 알고 있는 **"제동기"**의 역할과 동일하다는 것입니다.

만약 break문을 사용하지 않는다면 결과가 어떻게 나올까요?

```javascript
var name = "junHyeoung"
var nickname;

switch (name) {
    case "seokjin":
    nickname = "olaf";
    case "junHyeoung":
    nickname = "tigger";
    case "seungbum":
    nickname = "corn";
    default:
    nickname = null;
}

console.log(nickname); // null;
```

break를 하지 않으니 case에 걸러져 로직을 실행하더라도 멈추지 않고 경주마처럼 **default**까지 내려갑니다. 🐎  
그래서 nickname을 null로 마무리가 되고 switch문이 종료가 되는 것이죠  
그렇기에 특별한 상황을 제외하고는 case 마지막에는 break를 해주는 것이 일반적입니다.

이전에 살펴보았던 if-else에서는 소괄호에 일일이 조건을 입력해서 블록을 구분해 로직을 실행시켰습니다.  
하지만 switch에서는 하나의 표현식에 대해서 그에 맞는 조건을 case로 구분하기 때문에 보다 여러 조건들로 인해   
if-else 문법으로 처리하기 애매하거나, 복잡해질 경우 switch문을 사용하는 것이 좋을 수 있습니다.

