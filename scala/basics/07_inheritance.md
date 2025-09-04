# 7. 継承

### 目次

- [継承の基本構文](#継承の基本構文)
- [コンストラクタの継承](#コンストラクタの継承)
- [抽象クラス](#抽象クラス)
- [トレイト（trait）](#トレイトtrait)
  - [使い方](#使い方)
  - [複数トレイトのミックスイン](#複数トレイトのミックスイン)
  - [トレイトに抽象メソッド](#トレイトに抽象メソッド)
- [型クラス・暗黙パラメータ](#型クラス暗黙パラメータ)

<br>

## 継承の基本構文

Scalaのクラスは`extends`キーワードで継承する

```scala
class Animal {
  def speak(): String = "..."
}

class Dog extends Animal {
  override def speak(): String = "Woof!"
}
```

- `override`修飾子は必須（Javaは任意）
- メソッド名、引数、戻り値の型は一致させる必要がある  

参照：[サンプルコード](00_sample_codes.md#7-継承)

<br>

## コンストラクタの継承

親クラスにコンストラクタがある場合、子クラスで明示的に呼び出す

```scala
class Animal(val name: String) {
  def speak(): String = "..."
}

class Dog(name: String) extends Animal(name) {
  override def speak(): String = s"$name says Woof!"
}
```

<br>

## 抽象クラス

- `abstruct class`：抽象メソッドを持てるクラス

<br>

## トレイト（trait）

- Javaの`interface`に近いが、実装付きのメソッドも書ける
- 複数継承が可能（クラスは単一継承）で、柔軟なコード構成が可能
- `abstruct class`と異なり、状態を持たずに振る舞いのみに集中するのが一般的

```scala
trait Greeter {
  def greet(name: String): String = s"Hello, $name!"
}
```

### 使い方

```scala
class EnglishGreeter extends Greeter

val greeter = new EnglishGreeter()
println(greeter.greet("ユーザー"))  // Hello, ユーザー!
```

### 複数トレイトのミックスイン

```scala
trait Friendly {
  def beFriendly(): String = "I'm friendly!"
}

trait Polite {
  def bePolite(): String = "Nice to meet you."
}

class Person extends Friendly with Polite

val p = new Person()
println(p.beFriendly())  // I'm friendly!
println(p.bePolite())    // Nice to meet you.
```

### トレイトに抽象メソッド

```scala
trait Speaker {
  def speak(): String  // 実装なし
}
```

<br>

参照：[サンプルコード](00_sample_codes.md#7-トレイト)

<br>

## 型クラス・暗黙パラメータ

- 同じ関数でも型ごとに振る舞いを変えることができる
- Javaなどではstaticに近い仕組みで書くことができるが、
- Scalaでは「型クラス」と「暗黙パラメータ」を組み合わせ、柔軟に処理を抽象化できる

<br>

- 型クラスの定義

  ```scala
  trait Show[T] {
    def show(x: T): String
  }
  ```

- given：型クラスのインスタンス、暗黙的に渡される値

  ```scala
  given Show[Int] with {
    def show(x: Int): String = x.toString
  }
  
  given Show[String] with {
    def show(x: String): String = x
  }
  ```

- using：パラメータで暗黙的に受け取る

  ```scala
  def printShow[T](x: T)(using s: Show[T]): Unit = {
    println(s.show(x))
  }
  ```

- 呼び出し

  ```scala
  printShow(123)       // Int 用 given が自動で使われる
  printShow("Scala")   // String 用 given が自動で使われる
  ```

- 明示的に渡すことも可能（`printShow(123)(using Show[Int])`）

<br>

参照：[サンプルコード](00_sample_codes.md#6-型クラス)

<br>

→[8. FP（関数型プログラミング）](08_fp.md)