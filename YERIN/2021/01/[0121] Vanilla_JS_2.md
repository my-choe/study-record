

### 📖 2-1 너의 첫번째 함수! (Your first JS Function)

``` javascript
function sayHello(name, age){
    console.log('Hello!', name, "you have", age, " years of age.");
}

sayHello("Yerin",15);
console.log("Hi!");
```

### 📖 2.1.1 More Function Fun

``` javascript
function sayHello(name, age){
    console.log('Hello!'+ name + "you are " + age + " years of age.");
}

sayHello("Yerin",15);
console.log("Hi!");
```

``` javascript
function sayHello(name, age){
    return `Hello ${name} you are ${age} years old`;
    

}

const greetYerin = sayHello("Yerin", 26);

console.log(greetYerin)
```

##### 더하기 계산기

``` javascript



const calculator = {
    plus: function(a,b){
        return a+b;
    }
}


const plus = calculator.plus(5,5)
console.log(plus)


```

##### 곱하기 계산기

``` javascript

const claculator = {
    multiple: function(a,b){
        return a * b
    }
}

const multiple = claculator.multiple(5,5);
console.log(multiple)


```

##### 빼기 계산기

``` javascript

const calculator = {
    minus: function(a,b){
        return a - b
    }
}

const minus = calculator.minus(3,1)
console.log(minus)

```

### 📖 2-2 JS DOM Functions

```html

<!DOCTYPE html>
<html>
    <head>
        <title>Something</title>
        <link rel="stylesheet" href="index.css"/>
    </head>
    <body>
        <h1 id="title">This works</h1>
        <script src="index.js"></script>
    </body>
</html>

```

``` javascript

 const title = document.getElementById("title");

 console.log(title);
 title.innerHTML = "Hi! From JS";

```

### 📖 2-3 Modifying the DOM with JS

``` javascript

 const title = document.querySelector("#title");

 console.log(title);
 title.innerHTML = "Hi! From JS";
 title.style.color = "#DEEE";
 document.title = "YERIN"
 

```


### 📖 2-4 Events and event handlers

사이즈 조절 시 이벤트 콘솔에 찍기
``` javascript
 const title = document.querySelector("#title");

function handleResize(event){
    console.log(event);
}
window.addEventListener("resize", handleResize);
```
클릭 시 이벤트 발생
``` javascript
 const title = document.querySelector("#title");

function handleClick(){
    title.style.color = "red";
}
title.addEventListener("click", handleClick);
```

### 📖 2-5 첫번째 조건문!! If, else, and, or

if와 else

``` javascript
if (10 === 5) {
    console.log("hi");
}else if( 10 > 5){
    console.log("ho");
}else {
    console.log("hey");
}
```
and와 or의 차이점
``` javascript
true && true = true;
false && true = false;
true && false = false;
false && false = false;

true || true = true;
false || true = true;
true || false = true;
false || false = false;
```
연령체크 if else문
``` javascript
const age = prompt("How dold are you");

if(age >= 18){ 
    console.log("you can drink");
}else if(age > 21){
    console.log("go ahed");
}else{
    console.log("you cant")
}
```

### 📖 2-6 DOM If else Function practice

``` javascript
const title = document.querySelector("#title");

const BASE_COLOR = "rgb(52, 73, 94)";
const OTHER_COLOR = "#7F8C8D";

function handleClick() {
    const currentColor = title.style.color;
    if(currentColor === BASE_COLOR){
        title.style.color = OTHER_COLOR;
    }else{
        title.style.color = BASE_COLOR;
    }

}

function init (){
    title.style.color = "#34495e";
    title.addEventListener("click", handleClick);
}

init();

function handleOffline(){
    console.log("Bye bye");
}

function handleOnline(){
    console.log("Welcome back");
}

window.addEventListener("offline", handleOffline);
window.addEventListener("online", handleOnline);




```

# html javascript dom event mdn 
어떤이벤트가 있는지 궁금할땐 mdn 검색!


### 📖 2-7 DOM If else Function practice part Two


