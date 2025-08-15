# 7. 継承

### 目次

- [継承の基本構文](#継承の基本構文)
- [コンストラクタの継承](#コンストラクタの継承)
- [抽象クラス](#抽象クラス)
- [トレイト（trait）](#トレイトtrait)
  - [使い方](#使い方)
  - [複数トレイトのミックスイン](#複数トレイトのミックスイン)
  - [トレイトに抽象メソッド](#トレイトに抽象メソッド)

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

→[8. エラーハンドリング](08_error_handling.md)