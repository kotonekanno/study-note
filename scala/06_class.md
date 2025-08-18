# 6. クラス

### 目次

- [クラス定義とコンストラクタ](#クラス定義とコンストラクタ)
- [case class（データクラス）](#case-classデータクラス)
  - [apply](#apply)
  - [unapply](#unapply)
  - [toString](#tostring)
  - [equals](#equals)
  - [hashCode](#hashcode)
  - [copy](#copy)
- [オブジェクト](#オブジェクト)
- [コンパニオンオブジェクト](#コンパニオンオブジェクト)
  - [applyの役割](#applyの役割)
  - [unapplyの役割](#unapplyの役割)
- [型クラス・暗黙パラメータ](#型クラス暗黙パラメータ)
- [カリー化と部分適用](#カリー化と部分適用)
  - [カリー化（Currying）](#カリー化currying)
  - [部分適用（Partial Application）](#部分適用partial-application)

<br>

## クラス定義とコンストラクタ

Javaと異なり、Scalaではコンストラクタとクラス定義が一体化されている

```scala
class Person(name: String, age: Int) {
  def greet(): String = s"Hi, my name is $name and I am $age years old."
}
```

- クラス名：`Person`
- コンストラクタ引数：`name`と`age`
- メソッド：`greet()`

<br>

- インスタンス生成と呼び出し
  
  ```scala
  val p = new Person("Alice", 30)
  println(p.greet())
  ```

- 外からコンストラクタの引数にアクセスしたい場合、以下のようにすることで自動的にゲッターが生成される

  ```scala
  class Person(val name: String, val kind: String)
  ```

参照：[サンプルコード](00_sample_codes.md#6-クラス定義とコンストラクタ)

<br>

## case class（データクラス）

- JavaのレコードやDTO（データ転送オブジェクト）に相当
- Scalaでは、より簡潔で強力

```scala
case class User(id: Int, name: String)
```

`case class`を定義すると、以下のメソッドが自動生成される
- `apply`：`new`を省略してインスタンス生成
- `unapply`：パターンマッチングで値を取り出す
- `toString`：オブジェクトの文字列表現
- `equals`：オブジェクトの内容が等しいか判定
- `hashCode`：`equals`とセットで使えるハッシュ値
- `copy`：一部フィールドだけを変更した新しいインスタンスを作れる
- フィールドは自動で`val`扱いになる（外部から読み取り可能に）

### apply

- `new`を省略してインスタンスを生成できる
- 詳細は[後述](#applyの役割)

### unapply

- パターンマッチングでインスタンスの中身を取り出すときに使う
- 詳細は[後述](#unapplyの役割)

### toString

- オブジェクトの文字列表現を返すメソッド
- 通常の`class`ではデフォルトでは難解（オーバーライドすればよい）
- `case class`では自動でわかりやすく生成される（例：`Class(str=Hoge)`）

```scala
case class User(name: String, age: Int)
val u = User("Alice", 20)
println(u.toString) // → User(Alice,20)
```

### equals

- オブジェクトの内容が等しいかを判定するメソッド
- Javaでは参照比較になるが、Scalaの`case class`は構造比較
- 自動で適切にオーバーライドされる

```scala
User("Alice", 20) == User("Alice", 20)  // → true
```

### hashCode

- ハッシュ値を返す
- `equals`が等しいならば`hashCode`も等しくなる
- `Map`のキーや`Set`の要素に使う場合、重要

```scala
val u = User("Alice", 20)
println(u.hashCode)
```

### copy

- 特定のフィールドだけ変えて複製
- `case class`専用
- `val`が不変でも、copyで手軽に新しいバージョンが作れる
- フィールドの変更が簡単で、関数型の設計に便利

```scala
val u1 = User("Alice", 20)
val u2 = u1.copy(age = 30)  // nameはそのまま、ageだけ変更
```

<br>

参照：[サンプルコード](00_sample_codes.md#6-case-class)

<br>

## オブジェクト

- 1回だけ作られるシングルトンオブジェクト
- `class`と異なり、`new`でインスタンス化する必要がない
- Javaの`static`のように、「どこからでも呼べる便利な機能」をまとめるのに使う

参照：[サンプルコード](00_sample_codes.md#6-オブジェクト)

<br>

## コンパニオンオブジェクト

- `class`と`object`が同じ名前で同じファイルにある場合、その`object`をコンパニオンオブジェクトという
- `class`に`apply`メソッドなどを追加したり、`case class`で自動生成されるメソッドをカスタマイズしたりできる

<br>

- `class`：インスタンスを作る設計図
- `object`：クラスに関連する便利なメソッド・定数をまとめる場所

参照：[サンプルコード](00_sample_codes.md#6-コンパニオンオブジェクト)

### applyの役割

- コンパニオンオブジェクトに書くと、`new`を省略してインスタンスを生成できる
- `case class User(id: Int, name: String`を定義した時、以下のような`apply`メソッドが自動生成されている
  
  ```scala
  def apply(name: String): User = new User(id, name)
  ```

- `user = User(1, "John")`のように呼び出した時、実際には`User.apply`が呼び出されている

### unapplyの役割

- パターンマッチングでインスタンスの中身を取り出すときに使う
- `case class User(id: Int, name: String`を定義した時、以下のような`unapply`メソッドが自動生成されている

  ```scala
  def unapply(user: User): Option[(Int, String)] = Some((user.id, user.name))
  ```

- `case User(i, n)`のようにパターンマッチングを行う時、実際には`User.unapply`が呼び出されている
- `User(i, n)`のi, nに値が展開される
- 参照：[パターンマッチング](07_conditional_statement.md#パターンマッチング)

<br>

参照：[サンプルコード](00_sample_codes.md#6-applyunapply)

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

## カリー化と部分適用

### カリー化（Currying）

複数引数の関数を、引数1つずつで呼び出せるように分割する技法

```scala
def add(a: Int)(b: Int): Int = a + b

val result = add(2)(3)  // 5
```

- `add`は実際には「`Int => (Int => Int)`」という型
- 先に`a`を与えることで、「`b`を待つ関数」になる

### 部分適用（Partial Application）

カリー化された関数に一部の引数だけを先に与えて、残りを後で与えるテクニック

```scala
val add2 = add(2)     // b: Int => Int
println(add2(5))      // 7
```

- `add2`は「2を加える関数」になった
- 以下のように、`_`を使うこともできる
  
  ```scala
  val double = multiply(2) _
  ```

  - 明示的に関数として扱う
  - 型推論が効かない場面では、`_`が必要な場合もある

<br>

参照：[サンプルコード](00_sample_codes.md#6-カリー化と部分適用)

<br>

→[7. 継承](07_inheritance.md)
