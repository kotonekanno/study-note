# 2. 関数

### 目次

- [関数定義](#関数定義)
- [無名関数（関数リテラル）](#無名関数関数リテラル)
  - [部分関数（Partial Function）](#部分関数partial-function)
  - [クロージャ（Closure）](#クロージャclosure)
- [高階関数（Higher-Order Functions）](#高階関数higher-order-functions)
  - [関数を変数として定義する](#関数を変数として定義する)
  - [関数を引数として渡す](#関数を引数として渡す)

<br>

## 関数定義

- 文法
  
  ```scala
  def 関数名(引数: 型): 戻り値の型 = {
    // 処理
    return 値
  }
  ```

- `return`は省略できる
  
  ```scala
  def greet(name: String): String = {
    "Hello, " + name
  }
  ```

- 呼び出し
  ```scala
  println(greet("ユーザー"))
  ```

- 1行で書く場合
  ```scala
  def double(n: Int): Int = n * 2
  ```

参照：[サンプルコード](00_sample_codes.md#2-関数定義)

<br>

## 無名関数（関数リテラル）

```scala
(x: Int) => x + 1
```

- `=>`の左側：引数
- `=>`の右側：処理（戻り値の式）

<br>

1. 変数に代入して使う場合
   
   ```scala
   val addOne = (x: Int) => x + 1
   println(addOne(5))  // 6
   ```

2. 高階関数の引数に渡す場合
   
   ```scala
   val nums = List(1, 2, 3)
   val doubled = nums.map(x => x * 2)  // List(2, 4, 6)
   ```

<br>

- 引数の型は省略可能
  
  ```scala
  x => x + 1
  ```

- 引数が一つの場合、`_`で簡略化
  
  ```scala
  nums.map(_ * 2)
  ```

- 複数引数の場合
  ```scala
  (x: Int, y: Int) => x + y
  ```

### 部分関数（Partial Function）

`case`を使って特定の入力にだけ反応する関数

```scala
{
  case 0 => "zero"
  case _ => "other"
}
```

### クロージャ（Closure）

外側の変数を参照・利用する無名関数

```scala
val factor = 2
val multiply = (x: Int) => x * factor
```

<br>

## 高階関数（Higher-Order Functions）

- 関数を引数として受け取るか、関数を戻り値として返す関数のこと
- Scalaでは、関数も変数に代入したり他の関数に渡したり返したりできる

### 関数を変数として定義する

```scala
val square = (x: Int) => x * x
println(square(5))  // 25
```

- `square`：整数をつけ取って平方を返す関数
- `(x: Int) => x * x`：無名関数

### 関数を引数として渡す

```scala
def applyTo10(f: Int => Int): Int = f(10)

val result = applyTo10(square)
println(result) // 100
```

- `applyTo10`：関数を引数に撮り、それを10に適用する関数
参照：[サンプルコード](00_sample_codes.md#2-高階関数)

<br>

→[3. コレクション](03_collection.md)