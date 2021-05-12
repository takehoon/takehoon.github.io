---
layout: post
title: "Javascript 기초: 빠르게 찍어먹기 2 - (객체)"
subtitle: "Javascript 기초 정리"
date: 2021-05-10 19:07:00 -0400
background: '/img/posts/javascript.jpg'
categories: [javascript]
tags: [javascript]
---
# Javascript 기초 빠르게 찍어먹기 2 - (객체)

## 2.1 개요
이전 [Javascript 기초 빠르게 찍어먹기 1](https://takehoon.github.io/javascript/2021/05/07/javascript기초빠르게찍어먹기1.html) 에서 기초 문법을 살펴 보았습니다. 이번 포스트에서는 Javascript의 객체에 대해서 살펴볼 생각입니다. 물론, 이전 포스트와 같이 이번에도 모든 함수, 모든 속성에 대해 살펴보지 않을 것입니다. (전부 외우지도 못할 뿐더러 그럴 필요가 없다고 생각합니다. 아마 개발을 하게 되면서 주로 사용하게될 keyword들이 생길 것이고 백문이 불여일견이라고 직접 손으로 치고 사용해봐야 쉽고 오래 기억할 것이라 생각합니다.)

다시 본론으로 돌아와, Javascript는 객체 기반 언어입니다. 어느 언어와 같이 객체는 기능과 속성을 가지고 있으며 이들을 각각 method 와 property로 부르며 정의하여 사용합니다.

### 2.1.1 내장 객체
내장 객체는 Javascript 엔진에 내장되어 있어 필요한 경우 생성하여 사용합니다. 
- String
- Date
- Array
- Math

### 2.1.2 브라우저 객체 모델
BOM 은 브라우저에 계층 구조로 내장되어 있는 객체를 말합니다.
- window
- screen
- location
- history
- navigator

### 2.1.3 문서 객체 모델
DOM 은 HTML 문서 구조를 말합니다. IE8 이하에서는 호환성이 떨어지기 때문에 jQuery를 이용한 DOM 을 주로 사용합니다.

## 2.2 내장 객체
### 2.2.1 내장 객체 생성하기
내장 객체를 생성하는 기본형은 ***new*** keyword를 통해 이뤄집니다.
```js
obj = new Object()
```

property와 method는 다음과 같이 정의합니다.
```js
var smartphone = new Object()
smartphone.color = "white"
smartphone.price = 1200000;
smartphone.on = function() {
    document.write("smartphone on")
}
```
***color*** 와 ***price***는 property로서 객체의 속성 정보를 가지고 있으며 ***on()*** 은 method로서 객체의 기능에 해당합니다.

### 2.2.2  날짜 정보 객체
날짜나 시간 관련 정보를 제공받으려면 ***Date*** 객체를 생성하여 이용합니다.

### 2.2.3 수학 객체
수학 관련 기능을 사용하기 위해선 ***Math*** 객체를 생성하여 이용합니다.

### 2.2.4 배열 객체
Javascript에서의 배열 객체는 ***Array*** 객체를 생성하여 이용합니다. index가 0부터 시작한다는 점도 타언어와 동일하며 ***[]*** 를 이용하여 원소에 접근하는 것 또한 동일합니다. 다만, 각 원소의 자료형이 동일할 필요는 없습니다.
```js
var arr = new Array()
arr[0] = 0
arr[1] = "1"
arr[2] = true
```

물론 ***Array*** 를 명시적으로 사용하지 않고도 배열 객체를 생성하는 방법도 존재합니다.
```js
var arr = [0, "1", true]
```

Javascript는 ***in*** keyword 를 지원합니다. 다만, 파이썬과 다른 점은 원소 자체를 가져오는 것이 아닌 원소의 인덱스를 가져옵니다.
```js
for(i in arr){
    document.write(arr[i])
}
```

### 2.2.5 문자열 객체
Javascript에서는 문자열도 객체로 취급합니다. 따라서 문자열을 생성하는 기본형은 다음과 같습니다.
```js
var str = new String("test")
```
하지만, 대게 바로 문자형 데이터를 입력하면서 사용합니다.
```js
var str = "test"
```

문자형 데이터에서 특정 문자를 얻고자 할 때에 ***charAt()*** method 를 사용합니다. 물론, ***[]*** 을 이용해서도 가능합니다.
```js
document.write(str.charAt(2))
document.write(str[2])
```

Javascript 문자형 데이터는 ***+*** 를 통해 concatenate 연산도 지원합니다.
```js
var str = "123" + "***" // "123***"
```

## 2.3 브라우저 객체 모델 (BOM)
브라우저에 내장된 객체를 *브라우저 객체* 라고 합니다.

### 2.3.1 Window 객체
window 객체는 브라우저 객체의 최상위 객체입니다.

- open() / close()
팝업 페이지를 띄우거나 닫습니다.
```js
window.open(url, title, option)
window.close()
```
<input type="button" value="open/close" onclick="test1()">
<script>function test1(){window.open("http://takehoon.github.io", "test", "width=300, height=300")}</script>

- alert()
alert 팝업을 띄웁니다. window 객체를 명시하지 않아도 사용 가능합니다.
```js
alert(message)
```
<input type="button" value="alert" onclick="test2()">
<script>function test2(){alert("alert test")}</script>

- prompt()
prompt 창을 띄웁니다. alert와 마찬가지로 window 객체를 명시하지 않아도 사용 가능합니다.
```js
prompt(query, base)
```
<input type="button" value="prompt" onclick="test3()">
<script>function test3(){prompt("hello", "prompt test")}</script>

- confirm()
confirm 은 확인/취소 창을 말하며 window 객체를 생략 가능합니다.
```js
confirm(query)
```
<input type="button" value="confirm" onclick="test4()">
<script>function test4(){confirm("confirm test")}</script>

### 2.3.2 일정 시간 간격으로 코드 실행하기
일정 시간 간격으로 코드를 실행하는 메소드로는 setInterval()과 setTimeout()가 있습니다.

- setInterval()
일정 시간 간격으로 반복 실행
- clearInterval()
setInterval() 메소드 실행을 취소
- setTimeout()
일정 시간이 지나면 코드를 실행하고 종료
- clearTimeout()
setTimeout() 메소드 실행을 취소

### 2.3.3 screen 객체
사용자의 모니터 정보를 제공하는 객체입니다.
- width
- height
- availWidth
- availHeight
- colorDepth

### 2.3.4 location 객체
location 객체는 현재 URL에 대한 정보와 새로고침 메소드를 제공합니다.

### 2.3.5 history 객체
사용자가 방문한 사이트에 대한 정보를 기록하고 이전 사이트로 되돌아갈 수 있는 메소드를 제공합니다.

### 2.3.6 navigator 객체
navigator 객체는 사용자의 브라우저와 OS 정보를 제공하는 객체입니다.

### 2.3.7 실습 예제
현재 사용자의 OS 와 스크린 사이즈 정보를 출력하는 예제.

<input type="button" value="test" onclick="test5()">
<script>
function test5(){
    alert("[OS] : " + navigator.userAgent)
    alert("[screen] : " + screen.width + " : " + screen.height)
}
</script>
