# 8. エラーハンドリング

### 目次

- [概要](#概要)
- [Option型](#option型)
- [Optionの活用](#optionの活用)
  - [.map](#map)
  - [.getOrElse](#getorelse)
- [Either](#either)
- [for式との組み合わせ](#for式との組み合わせ)
  - [Optionの合成](#optionの合成)
  - [Eitherの合成](#eitherの合成)

<br>

## 概要

- `Option[T]`：値があるかないか
- `Either[L, R]`：成功か失敗か（右が成功）

<br>

## Option型

- 「値があるかもしれないし、ないかもしれない」を表現するコンテナ型
- Javaや他の言語では`null`が多用され、その扱いでバグが多発する
- Scalaは`null`の代わりに`Option`型を使い、安全に値の有無を表現する

<br>

- `Some("")`
  - 「値がある」ことを表す
  - カッコ内の文字列`""`が「実際の値」
  - 例：`Some("hello")`は「値が'hello'で存在する」ことを表す
- `None`
  - 「値がない」ことを表す
  - 値を持たないため、`()`は付けない

<br>

- 基本例
  
  ```scala
  def findName(id: Int): Option[String] = {
    if (id == 1) Some("Alice")
    else None
  }

  val nameOpt = findName(2)

  nameOpt match {
    case Some(name) => println(s"Name found: $name")
    case None       => println("No name found")
  }
  ```

- 使い方例1

  ```scala
  def findUser(id: Int): Option[String] = {
    if (id == 1) Some("Alice")
    else None
  }

  val user1 = findUser(1) // Some("Alice")
  val user2 = findUser(2) // None
  ```

- 使い方例2

  ```scala
  def findName(id: Int): Option[String] = {
    if (id == 1) Some("Alice")
    else None
  }

  val nameOpt = findName(2)

  nameOpt match {
    case Some(name) => println(s"Name found: $name")
    case None       => println("No name found")
  }
  ```

参照：[サンプルコード](00_sample_codes.md#8-option型)

## Optionの活用

### .map

`.map`：値があるときだけ関数を適用
  
```scala
val nameOpt = Some("Alice")
val upper = nameOpt.map(n => n.toUpperCase)  // Some("ALICE")
```
`None`だった場合はスルーされ、結果も`None`のまま

### .getOrElse

`.getOrElse`：値がないときのデフォルトを指定

```scala
val result = nameOpt.getOrElse("No name")  // "Alice"
val noneOpt: Option[String] = None
val fallback = noneOpt.getOrElse("No name")  // "No name"
```

<br>

参照：[サンプルコード](00_sample_codes.md#8-option型の活用)

<br>

## Either

```scala
val result: Either[String, Int] = Right(42)
val error: Either[String, Int] = Left("Error occurred")
```

- `Right`：成功（正常系）
- `Left`：失敗（異常系）

<br>

活用例

```scala
val res: Either[String, Int] = Right(42)

res match {
  case Right(v) => println(s"Success: $v")
  case Left(e)  => println(s"Error: $e")
}
```

参照：[サンプルコード](00_sample_codes.md#8-either)

<br>

## for式との組み合わせ

複数の`Option`や`Either`を連続的に使いたいときに、ネストせずに読みやすく書くことができる

### Optionの合成

```scala
def getUser(id: Int): Option[String] = Some("ユーザー")
def getEmail(name: String): Option[String] = Some(s"$name@example.com")

val result: Option[String] = for {
  name  <- getUser(1)
  email <- getEmail(name)
} yield s"Send to: $email"

println(result.getOrElse("No email found"))
```

- `None`が1つでもあれば全体が`None`になる
- `Some`ならばその中身を抽出して順に使える
- `yield`の中が最終結果になる  

参照：[サンプルコード](00_sample_codes.md#8-optionの合成処理)

### Eitherの合成

```scala
def getUser(id: Int): Either[String, String] = Right("ユーザー")
def getEmail(name: String): Either[String, String] = Right(s"$name@example.com")

val result: Either[String, String] = for {
  name  <- getUser(1)
  email <- getEmail(name)
} yield s"Send to: $email"

println(result) // Right(Send to: ユーザー@example.com)
```

- `Left`が1つでも出たらその時点で打ち切られる（早期return）
- `Right`同士ならば、合成されて最終的に`Right（結果）`になる  

参照：[サンプルコード](00_sample_codes.md#8-eitherの合成処理)

<br>

→[9. 非同期処理](09_future.md)