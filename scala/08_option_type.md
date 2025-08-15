# Option型

### 目次

- [Option型の背景](#option型の背景)
- [Option型の構造](#option型の構造)
- [Optionの活用](#optionの活用)
  - [.map](#map)
  - [.getOrElse](#getorelse)

<br>

## Option型の背景

- Javaやほかの言語では`null`が多用され、その扱いでバグが多発する
- Scalaは`null`の代わりに`Option`型を使い、安全に値の有無を表現する

<br>

## Option型の構造

「値があるかもしれないし、ないかもしれない」を表現するコンテナ型

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
