# 😎 코틀린을 공부해보자

### - 코틀린의 기본문법

```kotlin
//1. 함수
fun helloWorld() { //리턴 형이 없을 때 Unit작성 안써도 무방하다
    println("Hello World")
}

fun add(a : Int, b : Int) : Int { //변수명을 type보다 먼저 써준다
    return a+b
}

//2. val 과 var
//val = value
fun hi() {
    val a : Int = 10 //변하지 않는 값
    var b : Int = 9 //변수
    b = 100
    val c = 10
    var d = 100
    var name = "soyce"
}

//3. String Template
val name = "joyce"
val lastName = "Park"
//println("my name is ${name + lastName}I'm 25") //$ 사용하여 변수 출력 사용 후 띄어쓰기하거나 ${}로 묶어줌
//println("Is this true? ${1==0}")
//println("this is 2\$a")
//4. 조건식
fun maxBy(a : Int, b : Int) : Int {
    if(a > b){
        return a
    }else{
        return b
    }
}

fun maxBy2(a : Int, b : Int) = if(a > b) a else b

fun checkNum(score : Int) {
    when(score){
        0 -> println("this is 0")
        1 -> println("this is 1")
        2,3 -> println("this is 2 or 3")
    }

    var b = when(score){
        1 -> 1
        2 -> 2
        else -> 3
    }

    println("b : ${b}")

    when(score) {
        in 90..100 -> println("You are genius!")
        in 10..80 -> println("Not bad")
        else -> println("oK")
    }
}

// Expression vs Statement
// Expression은 표현식으로 리턴값을 반환하는 경우, Statement는 이렇게 이렇게 해라 하고 명령을 지시하는 경우
// 5. Array and List
//Array
//List 1. List 2. MutableList
fun array(){
    val array : Array<Int> = arrayOf(1,2,3)
    val list : List<Int> = listOf(1,2,3)

    val array2 : Array<Any> = arrayOf(1, "d", 3.4f)
    val list2 : List<Any> = listOf(1, "d", 11L)

    array[0] = 3
    var result : Int = list.get(0)

    var arrayList : ArrayList<Int> = arrayListOf<Int>()
    arrayList.add(10)
    arrayList.add(20)
    arrayList[0] = 20
    arrayList = arrayListOf()
}

//6. For / While
fun forAndWhile() {
    val students : ArrayList<String> = arrayListOf("joyce", "jenny", "james", "jenifer")

    for (name in students){
        println("${name}")
    }

    for((index : Int, name : String) in students.withIndex()){
        println("${index+1}번째 학생은? ${name}")
    }

    var sum : Int = 0
    for (i in 10 until 100){
        sum += i
    }
    println(sum)

    var index = 0
    while(index < 10){
        println("current index : ${index}")
        index++
    }
}

//7. Nullalble / NonNull
fun nullCheck(){
    //NPE : NULL pointer Exception
    var name = "joyce" //NonNul
    var nullName : String? = null //Nullable
    var nameInUpperCase : String = name.toUpperCase()
    var nullNameInUpperCase : String? = nullName?.toUpperCase() //? 붙여서 null인지 아닌지 check
    // ?:
    val lastName : String? = "Hong"
    val fullName : String = name + " " + (lastName ?: "NO lastName")
    println(fullName)

    //!!
}

fun ignoreNulls(str : String?){
//    val mNotNull : String = str!! //Null이 확실히 않을 때!
//    val upper : String = mNotNull.toUpperCase()
    val email : String? = null
    email?.let {
        print("my emamli is ${email}")
    }
}

//Class
//class ClassPractice
open class Human constructor(val name : String = "Anonymous"){

    //val name : String = name
    //java
    /*
    class Person{
    }
    public Person(String name, int age){
     this(name);}
     */
    constructor(name : String, age: Int) : this(name){
        println("My name is ${name}, ${age}years old")
    }

    init { //주생성자의 일부로 제일 먼저 실행됨
        println("New Human has been born!")
    }

    fun eatingCake(){
        println("This is so YUMMY~~~")
    }

    open fun singASong(){
        println("lalala")
    }
}

class Korean : Human(){
    override fun singASong(){
        super.singASong()
        println("라라라")
        println("My name is ${name}")
    }
}

fun main(){
//    val human = Human( name= "yeeun")
//    val stranger = Human()
//    human.eatingCake()
//    val mom = Human(name = "Kurl", age = 52)
//    println("This human's name is ${stranger.name}")
    val korean = Korean()
    korean.singASong()

}
```

##### 참조 :  [코틀린 3강으로 끝내기 - 1편 기본 문법](https://www.youtube.com/watch?v=IDVnZPjRCYg&list=PLxBf91VkJLZ_XosvQ5yJnJB3k3iho2XbV&index=1)
