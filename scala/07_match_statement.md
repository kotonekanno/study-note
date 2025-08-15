# match式

### 目次

- [match式](#match式-1)
- [パターンマッチング](#パターンマッチング)

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

## パターンマッチング

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

<br>

参照：[サンプルコード](00_sample_codes.md#7-match式)

<br>

→[Option型](08_option_type.md)