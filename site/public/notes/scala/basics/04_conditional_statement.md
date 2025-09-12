# 3. 条件分岐

### 目次

- [if式](#if式)
- [match式](#match式)
  - [パターンマッチング](#パターンマッチング)
  - [部分関数（Partial Function）](#部分関数partial-function)

<br>

## if式

- 基本文法
  
  ```scala
  val result = if (age >= 20) "adult" else "minor"
  ```

- Scalaではifは式（expression）であり、値を返す
  ```scala
  val status = if (age >= 65) "senior"
               else if (age >= 20) "adult"
               else "minor"
  ```

<br>

参照：[サンプルコード](00_sample_codes.md#4-if式)

<br>

## match式

- Scalaでは`match`は値を返す式
- `case`で分岐し、どの条件にマッチしたかで値を決定する

```scala
val n = 2

val result = n match {
  case 1 => "one"
  case 2 => "two"
  case _ => "other"
}

println(result) // "two"
```

- `_`：どれにもマッチしなかった時のワイルドカード
- すべての分岐が値を返す式

<br>

### パターンマッチング

- match文と`case class`の組み合わせ
- `case class`の構造をそのまま分解できる
- `Option`, `List`, `Either`などとも相性がいい
- `_`は「使わない変数」を明示するためのシグナルとなる

```scala
u match {
  case User("Alice", _) => println("Hi Alice!")
  case User(name, age) => println(s"$name is $age years old.")
}
```

### 部分関数（Partial Function）

`case`を使って特定の入力にだけ反応する関数

```scala
{
  case 0 => "zero"
  case _ => "other"
}
```

<br>

参照：[サンプルコード](00_sample_codes.md#4-match式)

<br>

→[5. 繰り返し](05_loop_statement.md)