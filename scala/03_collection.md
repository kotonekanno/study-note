# 4. コレクション（List）

### 目次

- [コレクション](#コレクション)
- [基本操作](#基本操作)
- [関数型コレクション操作](#関数型コレクション操作)
- [Listの高階関数操作](#listの高階関数操作)
  - [flatMap](#flatmap)
  - [reduce](#reduce)
  - [fold](#fold)

<br>

## コレクション

- ScalaのListはイミュータブルなコレクション
- Javaの`ArrayList`と異なり、基本的に操作は新しいリストを返す形
  
<br>

## 基本操作

```scala
val numbers = List(1, 2, 3, 4)
println(numbers.head)    // 1 （先頭要素）
println(numbers.tail)    // List(2, 3, 4) （先頭以外）
println(numbers.isEmpty) // false
val list2 = 0 :: list1     // 先頭に0を追加した新しいリスト
val list3 = list1 :+ 5    // 末尾に5を追加した新しいリスト
```

- `.head`：先頭要素を取り出す
- `.tail`：先頭を除いたリスト
- `.isEmpty`：空かどうかを判定（true/false）
- 要素の追加
  - `::`：リストの先頭に要素を追加（新しいリストが返る）
  - `:+`：リストの末尾に要素を追加（新しいリストが返る）

参照：[サンプルコード](00_sample_codes.md#3-基本操作)

<br>

## 関数型コレクション操作

- `map`：リストの各要素に関数を適用し、新しいリストを返す
  
  ```scala
  val doubled = numbers.map(n => n * 2)
  ```
  
- `filter`：条件に合う要素だけを抽出し、新しいリストを返す
  
  ```scala
  val evenNumbers = numbers.filter(n => n % 2 == 0)
  ```

参照：[サンプルコード](00_sample_codes.md#3-関数型コレクション操作)

<br>

## Listの高階関数操作

### flatMap

map + flatten

```scala
val data = List("a b", "c d")
val result = data.flatMap(str => str.split(" "))
// List("a", "b", "c", "d")
```

- `map`で`"a b"`→`["a","b"]`に変換
- その結果を1つのリストにまとめる（`flatten`）

### reduce

累積的に要素を処理

```scala
val numbers = List(1, 2, 3, 4)
val sum = numbers.reduce((a, b) => a + b)  // 10
```

- `reduce`：最初の2つの要素に関数を適用し、その結果と次の要素にまた適用...と繰り返す
- 要素が1つ以上必要（空リストだと例外）

### fold

`reduce`と似ているが、初期値がある

```scala
val numbers = List(1, 2, 3, 4)
val product = numbers.fold(1)((a, b) => a * b)  // 24
```

- 初期値から開始（ここでは`1`）
- 空のリストでも安全に使える

<br>

参照：[サンプルコード](00_sample_codes.md#3-listの高階関数操作)

<br>

→[4. 条件分岐](04_conditional_statement.md)