---
title: 자바스크립트 참 같은 값(Truthy), 거짓 같은 값(Falsy)
date: 2019-04-25 10:43:45
tags: javascript
categories: javascript
---
#### 참 같은 값(Truthy)[참조](https://developer.mozilla.org/ko/docs/Glossary/Truthy)
	참 같은 값(Truthy)인 값이란 불리언을 기대하는 문맥에서 true로 평가되는 값입니다. 따로 거짓 같은 값으로 정의된 값이 아니면 모두 참 같은 값으로 평가됩니다. (예: false, 0, "", null, undefined, NaN 등)
```javascript
if (true)
if ({})
if ([])
if (42)
if ("foo")
if (new Date())
if (-42)
if (3.14)
if (-3.14)
if (Infinity)
if (-Infinity)
```
<br>

#### 거짓 같은 값(Falsy)[참조](https://developer.mozilla.org/ko/docs/Glossary/Falsy)
	거짓 같은 값(Falsy) 값은 불리언 문맥에서 false로 평가되는 값입니다.
```javascript
if (false)
if (null)
if (undefined)
if (0)
if (NaN)
if ('')
```