# 😎 코틀린을 공부해보자

### - 코틀린의 고급문법

#### 1. Lamda
```kotlin
// 1. Lamda
// 람다식은 우리가 마치 value처럼 다룰 수 있는 익명함수이다.
// 1) 메소드의 파라미터로 넘겨줄 수가 있다. fun maxBy(a : Int)
// 2) return 값으로 사용할 수가 있다.
// 람다의 기본정의
// val lamdaName : Type = {argumentList -> codeBody}
val square : (Int) -> (Int) = {number:Int -> number * number} //Type을 한 군데에 명시해주어야함
val nameAge  = {name : String, age : Int ->
    "my name is ${name} I'm ${age}"
}
fun main() {
    println(square(12))
    println(nameAge("joyce", 99))
    val a = "joyce said "
    val b = "mac said "
    println(a.pizzaIsGreat())
    println(b.pizzaIsGreat())

    println(extendString("ari", 25))
    println(calculateGrade(97))
    println(calculateGrade(971))

    val lamda = {number : Double ->
        number == 4.3213
}
    println(invokeLamda(lamda))
    println(invokeLamda({ it > 3.242}))
    println(invokeLamda{it > 3.22})
}

// 확장함수
val pizzaIsGreat : String.() -> String = {
    this + "Pizza is the best!"
}
fun extendString(name : String, age : Int) : String{
    val introduceMyself : String.(Int) -> String = {"I am ${this} and ${it} years old"}
    return name.introduceMyself(age)
}

// 람다의 Return
val calculateGrade : (Int) -> String = {
    when(it){
        in 0..40 -> "fail"
        in 41..70 -> "pass"
        in 71..100 -> "perfect"
        else -> "Error"
    }
}
//람다를 표현하는 여러가지 방법
fun invokeLamda(lamda : (Double) -> Boolean) : Boolean {
    return lamda(5.2343)

}
```

#### 2. data class
```kotlin
data class Ticket(val companyName : String, val name : String, var date : String, var searNumber : Int)
// toString(), hashCode(), equals(), copy()
class Ticket2(val companyName : String, val name : String, var date : String, var searNumber : Int)

fun main() {
    val ticketA = Ticket("koreanAir", "joyceHong","2020-02-14",  14)
    val ticketB = Ticket2("koreanAir", "joyceHong","2020-02-14",  14)

    println(ticketA)
    println(ticketB)

}
```

#### 3. Companion object
```kotlin
class Book private constructor(val id : Int, val name : String) {

    companion object BookFactory : IdProvider{

        override fun getId(): Int {
            return 44
        }

        val myBook = "new Book"
        fun create() = Book(getId(), myBook)
    }

}

interface IdProvider {
    fun getId() : Int
}

fun main(){
//    val book = Book.Companion.create()
    val book = Book.create()

    val bookId = Book.BookFactory.getId()
    println("${book.id} ${book.name}")

}
```

#### 4. Object
```kotlin
//Singleton Pattern
object CarFactory {
    val cars : MutableList<Car> = mutableListOf<Car>()
    fun makeCar(horsePower: Int) : Car {
        val car = Car(horsePower)
        cars.add(car)
        return car
    }
}

data class Car(val horsePower : Int)

fun main(){
    val car = CarFactory.makeCar(10)
    var car2 = CarFactory.makeCar(200)

    println(car)
    println(car2)
    println(CarFactory.cars.size.toString())

}
```

##### 참조 :  [코틀린 3강으로 끝내기 - 2편 고급 문법](https://www.youtube.com/watch?v=Q5noYbbc9uc&list=PLxBf91VkJLZ_XosvQ5yJnJB3k3iho2XbV&index=2)
