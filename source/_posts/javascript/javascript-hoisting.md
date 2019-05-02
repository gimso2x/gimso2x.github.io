---
title: 자바스크립트 호이스팅
date: 2019-05-02 14:13:51
tags: javascript
categories: javascript
---
[참조](https://developer.mozilla.org/ko/docs/Glossary/Hoisting)
### 자바스크립트의 특징으로 모든 선언문은 호이스팅(Hoisting)되기 때문이다.
>JavaScript는 초기화가 아닌 선언만 끌어올립니다(hoist). 만약 변수를 선언한 뒤 나중에 초기화시켜 사용한다면, 그 값은 undefined로 지정됩니다. 아래 두 예제는 같은 동작을 보여줍니다.
```javascript
var x = 1; // x 초기화
console.log(x + " " + y); // '1 undefined'
var y = 2;


// 아래 코드는 이전 코드와 같은 방식으로 동작합니다.
var x = 1; // Initialize x
var y; // Declare y
console.log(x + " " + y); // '1 undefined'
y = 2; // Initialize y
```