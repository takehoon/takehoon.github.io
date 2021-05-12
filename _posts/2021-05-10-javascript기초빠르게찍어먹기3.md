---
layout: post
title: "Javascript 기초: 빠르게 찍어먹기 3 - (함수)"
subtitle: "Javascript 기초 정리"
date: 2021-05-10 20:48:00 -0400
background: '/img/posts/javascript.jpg'
categories: [javascript]
tags: [javascript]
---
# Javascript 기초 빠르게 찍어먹기 3 - (함수)

## 3.1 개요
이전 [Javascript 기초 빠르게 찍어먹기 2](https://takehoon.github.io/javascript/2021/05/10/javascript기초빠르게찍어먹기2.html) 에서 객체에 대해 살펴보았습니다. 이번 포스트에서는 Javascript 의 함수에 대해 알아보겠습니다.

우리는 필요한 데이터를 메모리상에 저장해두고 그 위치를 변수로 기억을 하며 변수를 통해 데이터에 접근합니다. 반면 필요한 데이터가 여러 개라면 어떻게 할까요? 우리는 이를 ***함수*** 로 정의하여 사용합니다. 즉, 함수를 메모리상에 저장해두고 필요할때마다 이를 꺼내서 사용합니다.

### 3.1.1 함수
Javascript는 이러한 함수를 ***function*** keyword를 이용하여 정의합니다.
```js
function method() {
    code
}
```
또한 javascript에서는 익명 함수라는 것이 존재합니다. 이름 그대로 함수명이 없는 함수로써 다음과 같이 정의합니다.
```js
method = function(){
    code
}
```

함수의 정의 자체는 바로 실행되지 않습니다. 다만 함수를 호출할 때에 정의한 내용을 기억해두었다가 실행합니다.

### 3.1.2 호이스팅(Hoisting)
익명 함수 얘기가 나왔으니 ***호이스팅(hoisting)***에 대한 설명이 필요할 것 같습니다. 호이스팅은 쉽게 말해 *정의를 찾는다* 라고 볼 수 있습니다. 

위에 언급한 예제들을 이용하여 설명드리자면, ```function method()``` 보다 ```method()```코드가 먼저 나온다하더라도 문제없이 실행됩니다. 그 이유는 호이스팅에 의해 정의를 찾아 *끌어올려* 함수 실행에 문제가 없도록 합니다.

하지만, 익명 함수를 사용하면서 ```method = function()```보다 ```method()``` 코드를 먼저 실행할 경우에는 호이스팅을 지원하지 않아 함수가 실행되지 않아 에러를 발생시킵니다.
```js
func1() // 함수 정의보다 먼저 나오더라도 hoisting에 의해 정상 실행

function func1() {
    document.write("hoisting")
}

func2 = function(){
    document.write("hoisting x")
}

func2() // 익명 함수로 hoisting을 지원하지 않아 함수 정의가 먼저 나온뒤 호출되어야 한다.
```

## 3.2 parameter
javascript의 함수도 parameter를 가질 수 있습니다. parameter를 가진 함수의 기본형은 다음과 같습니다.
```js
function method(param1, param2, param3, ..., paramN){
    code
}
```

물론 parameter의 개수를 가변적으로 받을 수 있는 방법도 지원합니다. 이때 ***arguments*** 변수를 이용합니다. ```arguments```변수는 배열처럼 접근하여 사용하면 됩니다.
```js
function method(){
    for(i in arguments){
        documents.write(arguments[i])
    }
}
```

## 3.3 함수 scope
scope는 변수 또는 함수의 유효 범위를 말합니다.

### 3.3.1 local 변수 & global 변수
전역 변수(global)는 어디에서나 사용할 수 있는 변수를 말하며, 지역 변수(local)는 해당 함수 scope에서만 사용할 수 있는 변수입니다.
```js
var val = "global"

function method(){
    var val = "local"

    alert(val) // "local"
}

alert(val) // "global"
```
위의 예제와 같이 함수 내에서 정의한 변수는 해당 함수에서만 유효하고 이 블록을 벗어나게 되면 더이상 유효하지 않게됩니다. 반면 전역 변수는 지역 변수와 동일한 명칭을 사용하지 않는다면 어디에서나 사용이 가능합니다.
```js
var val = "global"

function method(){
    alert(val) // "global"
}

alert(val) // "global"
```

### 3.3.2 global 함수와 local 함수의 차이
전역 함수(global)와 지역 함수(local)도 변수와 동일합니다.
```js
function global(){
    code
}

function method(){
    function local(){
        code
    }
}
```
위 예제에서 ```global()``` 함수는 어디에서나 사용이 가능하지만, ```local()```함수는 ```method()`` 함수 내에서만 사용이 가능합니다.

### 3.3.3 즉시 실행 함수
```js
var val = 100
function method() {
    val += 100
    alert(val) // 200
}
method()
function method(){
    alert(val) // 100
}
```
위의 예제는 결국 100을 alert합니다. 그 이유는 마지막에 정의한 ```method()``` 함수가 호이스팅되어 호출되기 때문입니다.

이와 같이 지역 함수의 명칭이 충돌하여 원치않는 결과를 출력할 수도 있습니다. 이를 해결하기 위해서 *즉시 실행 함수*에 대해서 살펴보도록 하겠습니다. 우선 즉시 실행 함수로 위 문제를 해결해보겠습니다.
```js
(function(){
    var val = 100
    function method(){
        val += 100;
        alert(val) // 200
    }
    method() 
}());
(function(){
    var val = 100
    function method(){
        alert(val) // 100
    }
}());
```
즉, ```function``` keyword를 이용하여 함수 scope 를 별도로 생성하고 이 안에서 ```method()```함수를 정의함으로써 동일한 이름을 가진 함수지만 다른 함수 scope로 인해 원하는 결과인 200 을 출력할 수 있게 됩니다. 

## 3.4 객체 생성자 함수의 활용
### 3.4.1 객체 생성자 함수
객체 생성자의 기본형은 다음과 같습니다.
```js
function object(param1, param2, ..., paramN){
    this.property = value
    this.method = function(){
        code
    }
}
```
```this``` keyword를 통해 객체의 속성과 함수를 지정할 수 있습니다.
이렇게 정의한 객체 생성자를 ```new``` keyword와 함께 사용함으로써 객체를 생성합니다.
```js
var obj = new object()
```

### 3.4.2 프로토타입
객체 생성자 함수를 통해 객체를 생성하는 방법을 살펴보았습니다. 앞서 소개한 방법으로 객체를 생성한다면 같은 동작, 속성을 지닌 객체를 손쉽게 만들 수 있습니다.

하지만, 객체들이 생성될 때마다 동일한 동작을 하는 메소드들 또한 각각 생성이 되어 메모리를 낭비하게 됩니다. 이를 방지하기 위해 프로토타입을 사용합니다. 프로토타입은 함수의 원형을 만들어 각 객체들이 공유하여 사용할 수 있도록 함으로써 메모리 공간을 절약할 수 있습니다.

프로토타입을 만드는 방법은 다음과 같습니다.
```js
function object(param1, param2, ..., paramN){
    this.property = value
}

object.prototype.method = function(){
    code
}
```
즉 **3.3**에서 살펴본 객체 생성자 함수에서 ```this``` keyword를 통해 메소드를 지정하였다면, 프로토타입은 해당 메소드를 밖으로 빼내어 ```prototype``` keyword로 지정합니다.

---
지금까지 Javascript의 객체에 대해 살펴보았습니다. 다음 포스트에서는 jQuery에 대해서 살펴보도록 하겠습니다. jQuery는 이전 포스트에서도 언급한 것과 같이 javascript의 브라우저간 호환성이 떨어지는 것을 보완할 수 있으며 DOM을 간편하게 사용할 수 있도록 지원합니다. 그럼 다음 포스트에서 뵙겠습니다. 감사합니다.