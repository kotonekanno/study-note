# サンプルコード集


### 1-変数定義

```scala
def main(args: Array[String]): Unit = {
  val name = "John Smith"
  var age = 21
  age += 1
  println(name)
  println(age)
}
```

### 2-関数定義

```scala
def greet(name: String): String = {
  "Hello, " + name + "!"
  }

def ageIn10Years(age: Int): Int = age + 10

def main(args: Array[String]): Unit = {
  println(greet("John"))
  println(ageIn10Years(21))
}
```

### 2-高階関数

```scala
def main(args: Array[String]): Unit = {
  val square = (x: Int) => x * x
  def applyTo3(f: Int => Int): Int = f(3)

  println(applyTo3(square))
}
```

### 3-基本操作

```scala
def main(args: Array[String]): Unit = {
  val numbers = List(1, 2, 3, 4, 5)
  println(numbers.head)
  println(numbers.tail)
  println(numbers.isEmpty)

  val tailList = numbers.tail
  println(tailList.head)
}
```

### 3-関数型コレクション操作

```scala
def main(args: Array[String]): Unit = {
  val numbers = List(1, 2, 3, 4, 5)
  val doubledNumbers = numbers.map(_ * 2)
  val evenNumbers = numbers.filter(n => n % 2 == 0)

  println(numbers)
  println(doubledNumbers)
  println(evenNumbers)
}
```

### 3-Listの高階関数操作

```scala
def main(args: Array[String]): Unit = {
  val words = List("I am", "learning Scala", "and it's fun")
  val flattenedWords = words.flatMap(_.split(" "))
  println(flattenedWords)
  println(flattenedWords.length)

  val numbers = List(1, 2, 3, 4, 5)
  val added = numbers.reduce((x, y) => x + y)
  val multiplied = numbers.fold(1)((x, y) => x * y)
  println(added)
  println(multiplied)
}
```

### 4-if式

```scala
def isEven(n: Int): Boolean = n % 2 == 0

def ageCategory(age: Int): String = {
  if (age <= 12) "child"
  else if (age <= 19) "teen"
  else if (age >= 20) "adult"
}

def main(args: Array[String]): Unit = {
  println(isEven(10))
  println(isEven(11))
  println(ageCategory(6))
  println(ageCategory(14))
  println(ageCategory(21))
}
```

### 4-match式

```scala
case class Animal(kind: String, name: String)

def main(args: Array[String]): Unit = {
  val dog = Animal("dog", "John")
  
  val msg = dog match {
    case Animal("dog", name) => s"This is a dog named $name."
    case Animal("cat", name) => s"This is a cat named $name."
    case Animal(kind, name)  => s"Unknow animal: $kind"
  }

  println(msg)
}
```

### 5-for式

```scala
def main(args: Array[String]): Unit = {
  val numbers = List(1, 2, 3, 4, 5, 6, 7, 8, 9, 10)

  val evenNumbers = for {
    n <- numbers
    if n % 2 == 0
  }yield n * 2

  println(evenNumbers)
}
```

### 6-クラス定義とコンストラクタ

```scala
class Animal(val name: String, val kind: String){
  def describe(): String = s"This is a $kind named $name."
}

def main(args: Array[String]): Unit = {
  val animal = new Animal("John", "dog")
  println(animal.describe())
  println(a.name)
}
```

### 6-case class

```scala
case class Book(title: String, author: String){
  def str: String = s"This is a book called $title written by $author"
}

def main(args: Array[String]): Unit = {
  val book1 = Book("Story", "John Smith")
  val book2 = book1.copy(author = "Jane Doe")

  println(book1.toString)
  println(book1.str)
  println(book2.toString)
  println(book2.str)
}
```

### 6-カリー化と部分適用

```scala
def main(args: Array[String]): Unit = {
  def multiply (a: Int) (b: Int): Int = a * b
  val double = multiply(2)
  println(double(5))
}
```

### 7-継承

```scala
abstract class Shape {
  def area(): Double
}

class Circle (radius: Double) extends Shape {
  override def area(): Double = radius * radius * 3.14
}

class Rectangle (width: Double, height: Double) extends Shape {
  override def area(): Double = width * height
}

def main(args: Array[String]): Unit = {
  val c = new Circle(3)
  val r = new Rectangle(2, 5)

  println(c.area())
  println(r.area())
}
```

### 7-トレイト

```scala
trait Walker {
  def walk(): String = "I'm walking"
}

trait Talker {
  def talk(): String = "I'm talking"
}

class Robot extends Walker with Talker

def main(args: Array[String]): Unit = {
  val robot = new Robot
  println(robot.walk())
  println(robot.talk())
}
```

### 8-Option型

```scala
def findAnimal(name: String): Option[String] = {
  if (name == "dog") Some("Found a dog")
  else if (name == "cat") Some("Found a cat")
  else None
}

def main(args: Array[String]): Unit = {
  val dog = findAnimal("dog")
  
  dog match {
    case Some(str)   => println(str)
    case None        => println("No name found")
  }
}
```

### 8-Option型の活用

```scala
def findAnimal(name: String): Option[String] = {
  if (name == "dog") Some("Found a dog")
  else if (name == "cat") Some("Found a cat")
  else None
}

def main(args: Array[String]): Unit = {
  val cat = findAnimal("cat")
  val msg = cat
    .map(_ + "!!!")
    .getOrElse("Not found...")
  println(msg)
}
```

### 8-Either

```scala
def main(args: Array[String]): Unit = {
  def safeDivide2(a: Int, b: Int): Either[String, Int] = {
    if(b == 0) Left("Division by zero")
    else Right(a / b)
  }

  println(safeDivide2(10, 0))
  println(safeDivide2(10, 2))
}
```

### 8-Optionの合成処理

```scala
def parseInt(s: String): Option[Int] = scala.util.Try(s.toInt).toOption
def nonZero(n: Int): Option[Int] = if (n == 0) None else Some(n)
def inverse(n: Int): Option[Double] = Some(1.0 / n)

def main(args: Array[String]): Unit = {
  val result = for {
    i <- parseInt("5")
    nz <- nonZero(i)
    inv <- inverse(nz)
  }yield inv

  println(result)
}
```

### 8-Eitherの合成処理

```scala
def parseInt(s: String): Either[String, Int] =
  scala.util.Try(s.toInt).toEither.left.map(_ => "Invalid number")

def nonZero(n: Int): Either[String, Int] =
  if (n == 0) Left("Division by zero") else Right(n)

def inverse(n: Int): Either[String, Double] =
  Right(1.0 / n)

def main(args: Array[String]): Unit = {
  val result = for {
    i <- parseInt("5")
    nz <- nonZero(i)
    inv <- inverse(nz)
  }yield inv

  println(result)
}
```

### 9-非同期処理

```scala
import scala.concurrent._
import ExecutionContext.Implicits.global
import scala.util.{Success, Failure}
import scala.concurrent.duration._

def main(args: Array[String]): Unit = {
  val f = Future {
    Thread.sleep(1000)
    100
  }

  f.onComplete {
    case Success(value) => println(s"Result is $value")
    case Failure(e)     => println(s"Failed with $e")
  }

  Await.result(f, 2.seconds)
}
```