---
title: 자바스크립트 값, 문, 식
date: 2019-04-25 11:13:51
tags: javascript
categories: javascript
---
#### 값 [참조](https://poiemaweb.com/js-syntax-basics#2-%EA%B0%92)
>값 은 프로그램에 의해 조작될 수 있는 대상을 말한다. 값은 다양한 방법으로 생성할 수 있다. 가장 간단한 방법은 리터럴 표기법(literal notation)을 사용하는 것이다.
```javascript
//값 = Hello World
var str = 'Hello World';
```

#### 문 [참조](https://poiemaweb.com/js-syntax-basics#6-%EB%AC%B8)
>프로그램(스크립트)은 컴퓨터(Client-side Javascript의 경우, 엄밀히 말하면 웹 브라우저)에 의해 단계별로 수행될 명령들의 집합이다.
각각의 명령을 문(statement)이라 하며 문이 실행되면 무슨 일인가가 일어나게 된다.
문은 리터럴, 연산자(Operator), 표현식(Expression), 키워드(Keyword) 등으로 구성되며 세미콜론( ; )으로 끝나야 한다.
```javascript
var x = 5;
var y = 6;
var z = x + y;

console.log(z);
```

#### 식 [참조](https://poiemaweb.com/js-syntax-basics#7-%ED%91%9C%ED%98%84%EC%8B%9D)
>표현식(Expression)은 하나의 값으로 평가(Evaluation)된다. 값(리터럴), 변수, 객체의 프로퍼티, 배열의 요소, 함수 호출, 메소드 호출, 피연산자와 연산자의 조합은 모두 표현식이며 하나의 값으로 평가(Evaluation)된다. 표현식은 결국 하나의 값이 되기 때문에 다른 표현식의 일부가 되어 조금 더 복잡한 표현식을 구성할 수도 있다. 아래의 예에서 5 * 10은 50으로 평가(연산)된다.
```javascript
// 표현식
5             // 5
5 * 10        // 50
5 * 10 > 10   // true
(5 * 10 > 10) && (5 * 10 < 100)  // true
```

(출처: [https://poiemaweb.com/js-syntax-basics](https://poiemaweb.com/js-syntax-basics))