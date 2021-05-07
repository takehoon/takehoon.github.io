---
layout: post
title: "Javascript 기초: 빠르게 찍어먹기 1 - (기초문법)"
subtitle: "Javascript 기초 정리"
date: 2021-05-07 16:03:00 -0400
background: '/img/posts/javascript.jpg'
categories: [javascript]
tags: [javascript]
---
# Javascript 기초 빠르게 찍어먹기 1 - (기초문법)

## 1.1 개요
Javascript는 Web browser에서 동작하는 script 언어입니다. 즉, FE(Front-End) 개발 언어로서 흔히 정적인 페이지(HTML)에 동작을 부여하는, *동적 페이지*를 개발하는데 주로 사용됩니다.


## 1.2 기초 문법
### 1.2.1 선언문
Javascript 코드를 작성할 영역을 알리기 위해 ```<script></script>```를 이용합니다.

선언문은 ```<head>``` 또는 ```<body>``` 영역에 선언할 수 있으며 대게 ```<head>``` 영역에 주로 사용합니다.

### 1.2.2  주석
Javascript의 주석은 다른 언어들과 유사하기 ```//``` 또는 ```/* */``` 를 사용합니다.

### 1.2.3 외부코드
관리, 유지보수 등을 위해 html 파일과 js 파일을 분리하여 개발할 수 있습니다. 따라서 ```.js``` 파일을 별도로 만들어 개발하고 이를 html 페이지에서 ```<script src="*.js"></script>```로 불러와 사용할 수 있습니다.
<br>

## 1.3 변수
### 1.3.1 변수 선언
변수를 선언할 때는 ```var``` keyword를 사용합니다. 변수에 저장할 데이터 종류로는 String, Number, Boolean, Null 데이터가 있으나 타 언어와는 달리 ```var``` keyword로 통일하여 사용 가능합니다.

### 1.3.2 변수에 저장할 수 있는 자료형
변수에 데이터를 저장하기 전 기본 상태는 ```undefined``` 입니다. 이후 변수에 저장된 값에 따라, ```String```, ```Number```, ```Boolean```, ```Null``` 값으로 구분됩니다.

이러한 데이터의 타입을 알아보기 위해선 ```typeof``` 를 이용하면 됩니다.

```js
var num = 100;
var str = "hello world"

document.write(typeof num);
document.write(typeof str);
```
<br>

## 1.4 연산자
Javascript의 연산자도 타언어와 비슷합니다.

| 종류 | 기본형 | 설명 |
|-----|------|-----|
|\+|A+B|덧셈|
|\-|A-B|뺄셈|
|\*|A*B|곱셈|
|/|A/B|나눗셈|
|%|A%B|나머지|

<p></p>

### 1.4.1 문자결합 연산자
문자 결합연산은 피연산자 중 하나라도 String 타입일 경우에 적용됩니다.
> "Hello" + "World" // "HelloWorld"

> "123" + 456       // "123456"
 

### 1.4.2 대입 연산자
타 언어와 동일하게 ```+=```, ```-=```, ```*=``` 등등 대입연산자 또한 사용 가능합니다.

### 1.4.3 증감 연산자
```++```, ```--``` 도 사용가능하며, 전위 연산, 후위 연산 모두 가능합니다.

### 1.4.4 비교 연산자
비교 연산도 타언어와 동일합니다. 다만 ```==``` 과 ```!=```은 String, Number 타입에 상관없이 표현하고자 하는 값이 같다면 동일하다고 보며 타입의 동일성 여부도 확인하기 위해서는 ```===```과 ```!==```를 사용합니다.
> "123" == 123 // true 

> "123" !=== 123 // false

### 1.4.5 논리 연산자
논리 연산도 ```&&```, ```||```, ```!``` 로 표현하며 삼항 연산도 지원합니다.

> 조건식 ? code1 : code2

## 1.5 실습 예제
이름, 신장, 체중을 입력받은 뒤 오차범위 +-5의 평균 체중을 구하는 소스
```js
var name = prompt("name?", "")
var height = prompt("height?", "")
var weight = prompt("weight?", "")

var avgW = (height - 100) * 0.9
var result = weight >= avgW - 5 && weight <= avgW + 5
result = result ? "적정 체중" : "적정 체중 x"
alert("name님은 " + result)

```

<input type="button" value="test" onclick="test()"/>
<br>

<script>
function test(){
    var name = prompt("name?", "")
    var height = prompt("height?", "")
    var weight = prompt("weight?", "")

    var avgW = (height - 100) * 0.9
    var result = weight >= avgW - 5 && weight <= avgW + 5
    result = result ? "적정 체중" : "적정 체중 x"
    alert("name님은 " + result)
}
</script>

## 1.6 조건문
### 1.6.1 if 문
```if```문으로 조건을 걸어 *true*, *false*를 판단합니다. 
조건식에서 *0*, *null*, *""*, *undefined*는 *false* 값으로 인식됩니다.

### 1.6.2 switch 문
Javascript는 switch 문도 지원합니다. 여러 case를 고려한 상태 변경에 사용됩니다.

## 1.7 반복문
### 1.7.1 while 문
```while```문도 반복할 내용을 블록안에 기술하고 반복조건을 ***만족할때 까지*** 반복합니다. C언어에서 많이 봤던 ```do-while```문도 지원합니다.

### 1.7.2 for 문
for 문의 조건식 표기도 C언어와 동일합니다. 다만 변수 타입의 경우 *int*형이 아닌 *var* 타입으로 기재합니다.

### 1.7.3 break 문
일정 조건을 만족하여 반복문을 벗어나고자할 때 break문을 사용합니다.

### 1.7.4 continue 문
반복문안에서 continue문을 이용하여 아래 코드를 실행하지 않고 다음 반복차수로 넘어갑니다.

---
기초 문법을 다룬다고 하였지만, 사실 타언어와 동일한 점이 많아 대부분 건너뛰었습니다. 저의 포스트는 기초적인 부분을 빠르게 넘어가고 실제 소규모 프로젝트를 구성하고 개발하는데 집중하려합니다. Javascript는 FE 개발에 중요하고 배울점도 매우 많기 때문에 기초적인 부분은 앞으로도 생략하도록 하겠습니다.

