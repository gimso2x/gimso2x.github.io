---
title: 자바스크립트 리터럴, 생성자, 클래스 방식 소스비교
date: 2019-05-23 11:13:51
tags: javascript
categories: javascript
---

#### 리터럴방식

```javascript
/**
 * Literal 방식
 */
const company = {
  sectors: "Programming" /* 회사영역 */,
  personNum: "100" /* 회사구성원수 */,
  createdYear: "1985" /* 설립연도 */,
  workingtime: "8hours" /* 일하는시간 */,
  openState: false /* 회사오픈상태 */,
  dispatchState: false /* 파견상태 */,
  developmentType: [] /* 개발타입 */,
  companyOperation: function() {
    this.openState = !this.openState;
  },
  dispatchThrow: function() {
    this.dispatchState = !this.dispatchState;
  },
  addDevelopType: function(item) {
    this.developmentType.push(item);
  }
};

company.companyOperation(); // 회사오픈
company.dispatchThrow(); // 파견보내기
company.addDevelopType("C");
company.addDevelopType("Java");
console.log(company);
```

#### 생성자 방식

```javascript
/**
 * 생성자 함수
 */

function company2( sectors, personNum, createdYear, workingtime, openState, dispatchState, developmentType ) {
  this.sectors = sectors;
  this.personNum = personNum;
  this.createdYear = createdYear;
  this.workingtime = workingtime;
  this.openState = openState || false;
  this.dispatchState = dispatchState || false;
  this.developmentType = developmentType;
  this.companyOperation = function() {
    this.openState = !this.openState;
  };
  this.dispatchThrow = function() {
    this.dispatchState = !this.dispatchState;
  };
  this.addDevelopType = function(item) {
    this.developmentType.push(item);
  };
}

const samsung = new company2( "semiconductor", 100000, "1960", "24hours", "", "", ["Java", "Android"] );
samsung.companyOperation(); // 회사오픈
samsung.dispatchThrow(); // 파견보내기
samsung.addDevelopType("C");
samsung.addDevelopType("Java");
console.log(samsung);
```

#### 클래스 방식

```javascript
/**
 * 클래스 방식
 */

class company3 {
  constructor( sectors, personNum, createdYear, workingtime, openState, dispatchState, developmentType ) {
    this.sectors = sectors;
    this.personNum = personNum;
    this.createdYear = createdYear;
    this.workingtime = workingtime;
    this.openState = openState || false;
    this.dispatchState = dispatchState || false;
    this.developmentType = developmentType;
    this.companyOperation = function() {
      this.openState = !this.openState;
    };
    this.dispatchThrow = function() {
      this.dispatchState = !this.dispatchState;
    };
    this.addDevelopType = function(item) {
      this.developmentType.push(item);
    };
  }
}

const hyundai = new company3( "semiconductor", 80000, "1962", "23hours", "", "", ["C", "IOS"] );
hyundai.companyOperation(); // 회사오픈
hyundai.dispatchThrow(); // 파견보내기
hyundai.addDevelopType("C");
hyundai.addDevelopType("Java");
console.log(hyundai);
```
