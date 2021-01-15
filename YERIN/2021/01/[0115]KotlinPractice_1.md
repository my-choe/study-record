
## - 코틀린의 기본문법
```kotlin

package com.example.yerinpractice

fun main(){

}

//1. 함수

fun helloWorld()  {







  println("Hello World!")
}

fun add(a : Int, b : Int) : Int {
    return a+b
}

//2. val vs var
//val = value (값) 바뀌지 않는 것.
//var 엔 값을 새로 넣어줘도 됨
fun hi(){
    val a : Int = 10
    var b : Int = 3

    b = 100

    val c = 100
    var d = 100
    var name = "yerin"
}

//4. 조건식

fun maxBy(a : Int, b : Int) : Int{
    if( a>b){
        return a
    }else{
        return b
    }
}

fun maxBy2(a:Int, b:Int) = if(a>b) a else b

fun checkNum(score : Int){
    when(score){
        0 -> println("this is 0")
        1 -> println("this is 1")
        2, 3 -> println("this is 2 or 3")
        else -> println ("I don't know") //생략가능
    }

    var b : Int = when(score){
        1-> 1
        2-> 2
        else-> 3 //이떄는 생략 불가
    }

    println("b: ${b}")

    when(score){
        in 90..100 -> println("You are genius")
        in 10..90 -> println("not bad")
        else -> println("okay")
    }
}

//Expression vs Statement

// 5. Array and List

// Array

// List 1. List 2. MutableList(수정가능)

fun araay(){
    val array = arrayOf(1,2,3)
    val list = listOf(1,2,3)

    val array2 = arrayOf(1,"d",3.4f)
    val list2 :List<Any> = listOf(1,"d",11L)

    array[0] = 3
    var result = list.get(0)
    var arrayList = arrayListOf<Int>()
    arrayList.add(10)
    arrayList.add(20)

}

// 6. For / While

fun forAndWhile(){

    val students = arrayListOf("yerin","joyce","jenny")

    for (name: String in students){
        println("${name}")
    }

    for ((index:Int, name:String) in students.withIndex()){
        println("${index+1}번째 학생 : ${name}")
    }

    var sum : Int = 0
    for (i:Int in 1..10 ){ //1..100 이랑 until 100 다른점은 100포함하지않는것
        sum += i
    }
    println(sum)

    var index = 0
    while(index <10){
        println("current index : ${index}")
        index++
    }
}

// 7. Nullable / NonNull

fun nullcheck(){
    //NPE : NULL poninter Exception

    var name : String ="Yerin"  //String 타입 생략 가능
    var nullName : String? = null //String 타입 생략 불가
    //물음표를 뒤에 붙이면 nullable 타입이 됩니다.

    var nameInUpperCase = name.toUpperCase()

    var nullNameInUpperCase = nullName?.toUpperCase()
    //null이면 하지말고 nutnull 이면 uppercase해라를 물음표로

    // ?:

    val lastName : String? = "Ahn"

    val fullName : String = name+ " " + (lastName?: "No lastName")

    println(fullName)



}

//!!

//이거 절대로 null일리가 없어! 근데 이건 좀 지양
fun ignoreNulls(str : String?){
    val mNotNull : String = str!!
    val upper :String = mNotNull.toUpperCase()

    val email : String? = "sosu0512@naver.com"
    email?.let{
        println("my email is ${email}")
    }

}
```

##### 참조 :  [코틀린 3강으로 끝내기 - 1편 기본 문법](https://www.youtube.com/watch?v=IDVnZPjRCYg&list=PLxBf91VkJLZ_XosvQ5yJnJB3k3iho2XbV&index=1)
