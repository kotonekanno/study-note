# クラス

### 目次

- [クラス定義とコンストラクタ](#クラス定義とコンストラクタ)
- [case class（データクラス）](#case-classデータクラス)
  - [toString](#tostring)
  - [equals](#equals)
  - [hashCode](#hashcode)
  - [copy](#copy)
  - [パターンマッチング（match）](#パターンマッチングmatch)
- [継承](#継承)
  - [基本的な継承構文](#基本的な継承構文)
  - [コンストラクタの継承](#コンストラクタの継承)
  - [抽象クラスとトレイト](#抽象クラスとトレイト)
- [カリー化と部分適用](#カリー化と部分適用)
  - [カリー化（Currying）](#カリー化currying)
  - [部分適用（Partial Application）](#部分適用partial-application)

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

- 参照：[サンプルコード](00_sample_codes.md#6-クラス定義とコンストラクタ)

## case class（データクラス）

- JavaのレコードやDTO（データ転送オブジェクト）に相当
- Scalaでは、より簡潔で強力

```scala
case class Person(name: String, age: Int)
```

`case class`を定義すると、
- `new`不要に
- 自動で`toString`, `equals`, `hashCode`, `copy`, `パターンマッチング`が使える

### toString

- オブジェクトの文字列表現を返すメソッド
- 通常の`class`ではデフォルトでは難解（オーバーライドすればよい）
- `case class`では自動でわかりやすく生成される

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

### パターンマッチング（match）

参照：[パターンマッチング](07_match_statement.md#パターンマッチング)

<br>

参照：[サンプルコード](00_sample_codes.md#6-case-class)

## 継承

### 基本的な継承構文

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

### コンストラクタの継承

親クラスにコンストラクタがある場合、子クラスで明示的に呼び出す

```scala
class Animal(val name: String) {
  def speak(): String = "..."
}

class Dog(name: String) extends Animal(name) {
  override def speak(): String = s"$name says Woof!"
}
```

### 抽象クラスとトレイト

- `abstruct class`：抽象メソッドを持てるクラス
- `trait`：Javaのインターフェースに近いが、実装も持てる

<br>

参照：[サンプルコード](00_sample_codes.md#6-継承)

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

カリー化されt何晏数に一部の引数だけを先に与えて、残りを後で与えるテクニック

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
  - 方推論がきかない場面では、`_`が必要な場合もある

<br>

参照：[サンプルコード](00_sample_codes.md#6-カリー化と部分適用)

<br>

→[7. match式](07_match_statement.md)