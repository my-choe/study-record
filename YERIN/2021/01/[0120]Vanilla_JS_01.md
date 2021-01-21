


### 0-1 Requirements : JS for Beginners 

### 0-2 What are we building : JS for Beginners 

### 1-1 Why JS? : JS for Beginners

### 1-2 Super Powers of JS

### 1-3 ES5, ES6 ES....WTF!?!?!
 #### ECMAScript 와 JavaScript의 차이점

### 1-4 VanillaJS
 #### 바닐라 자바스크립트를 배워야하는 이유

### 1-5 Hello World with Javascript

``` html
<!DOCTYPE html>
<html>
    <head>
        <title>Something</title>
        <link rel="stylesheet" href="index.css"/>
    </head>
    <body>
        <h1>This works</h1>
        <script src="index.js"></script>
    </body>
</html>
``` 

```css
body{
    background-color: peru;
    h1{color:#fff}
} 
``` 

``` javascript
alert('Im Working. Im Js. Im Beautiful')
console('Im Working. Im Js. Im Beautiful')
``` 

### 1-5-1 What are we learning

### 1-6 Your first JS Variable(변수!)
* 변수란 무엇인가?
* let이란 무엇인가?

### 1-7 let, const, var

``` 
변수 선언에는 기본적으로 const를 사용하고, 재할당이 필요한 경우에 한정해 let 을 사용하는 것이 좋다.
그리고 객체를 재할당하는 경우는 생각보다 흔하지 않다. const 를 사용하면 의도치 않은 재할당을 방지해 주기 때문에 보다 안전하다.
재할당이 필요한 경우에 한정해 let 을 사용한다. 이때, 변수의 스코프는 최대한 좁게 만든다.
재할당이 필요 없는 상수와 객체에는 const 를 사용한다.
``` 
### 1-8 Data Types on JS

### 1-9 Organizing Data with Arrays
### 1-10 Organizing Data with Objects

``` javascript

배열과 객체(Object)의 차이



예를들어,

배열 선언은 ex) const info = ["book", "read"];       //////     Object 선언은 const info = {"book", "read"}  이라할 때,



Object로 선언한 info를 console.log로 찍어보면 SyntaxError: Unexpected token 에러가 뜬다.



즉, Object를 배열처럼 {} 안에다가 "" , "" 로 선언할 수 없다는 뜻.

참고로 배열은 [] 괄호로, Object는 {}로 사용한다.



Object는 실제 객체를 만드는 것.

ex) const info = {

name:"park",

gender:"male"

}

이렇게 변수와 값을 넣어주고 console.log(info)를 찍어보면 {name: "park", gender: "male}가 출력이 된다.

근데 나는 name만 출력하고 싶어...



그러면 console.log(info.name); 이라고 찍으면 콘솔에는 park이 출력된다.



만약에 내가 name을 park이 아닌 kim 으로 바꾸고 싶으면 기존에



ex) const info = {

name:"park",

gender:"male"

}

info.name = 'kim';



console.log(info.name); 이라고 바꾸면 된다.



하지만 info 자체를 바꿀 수는 없다는 점은 꼭 알아두길 바란다.



ex) info = "park";     (x)



우리는 한 사람의 정보를 여러개 저장해야할 경우가 생길텐데 그때, Object안에 Array를 넣어서 사용한다.



ex) const info = {

name:"park",

gender:"male",

hobby: ["movie", "sing", "computergame"],                    //배열의 Object

favFood: [

{

name:"rice", 

fatty:false

}, 

{

name:"Cheese burger",

fatty:true

}]  // Object의 배열

}


console.log(info) 출력

{ name: 'park',

  gender: 'male',

  hobby: [ 'movie', 'sing', 'computergame' ],

  favFood: 

   [ { name: 'rice', fatty: false },

     { name: 'Cheese burger', fatty: true } ] }

이 안에서 name이 'rice'를 뽑으려면 어떻게 해야할까? 그것은 본인에게 맞기겠습니다.


``` 
* 참조 : [자바스크립트 배열이란?](https://docu94.tistory.com/53)
* 참조 : [Array vs Object 무슨차이야?(Object란)](https://docu94.tistory.com/54)

``` javascript
//실습
const something = "Something"
const daysOfWeek = ["Mon", "Tue", "Wed", "Thu", "Fri", "Sat", "Sun", 54, true, something];
const yerinInfo = {
    name:"Yerin",
    age:"26",
    gender:"Female",
    isHandsome:true,
    favMovies: ["Along the gods", "LOTR"],
    favFood: [{name:"Kimchi",
                fatty:false},{name:"Buger",fatty:true}]
}

console.log(yerinInfo.gender); //f

yerinInfo.gender = "male";

console.log(yerinInfo.gender);//m

console.log(daysOfWeek);
console.log(yerinInfo);


const sq = {
    name:"saeque",
    age:"8",
    gender:"Female",
    favFood:["인간밥","해바라기씨","밀렛"],
    favPerson:[{name:"yerin",age:"26",gender:"Female"},{name:"mom",age:"56",gender:"female"}]

}

console.log(sq);
console.log(sq.favFood[2]);

``` 

##### 참조 :  [초보자를 위한 바닐라 자바스크립트](https://youtu.be/PRA_bhUxuh4)
