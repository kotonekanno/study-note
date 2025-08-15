# 1. 変数

### 目次

- [変数定義](#変数定義)
- [型推論](#型推論)
- [Scalaのデータ型](#scalaのデータ型)
- [文字列補完（String Interpolation）](#文字列補完string-interpolation)

## 変数定義

- `val`：再代入不可（イミュータブル）
  - Scalaでは基本的に`val`を使う
- `var`：再代入可（ミュータブル）
  - 再代入が必要な時だけ`var`にする
  - 副作用を伴う処理を増やすので、なるべく避けた方が良いとされる

```scala
val name = "ユーザー"
var age = 20
```

参照：[サンプルコード](00_sample_codes.md#1-変数定義)

## 型推論

- Scalaでは右辺から型を推論してくれるため、明示的に書かなくてもよい
- 型を明示的に書くこともできる
  
  ```scala
  val score: Int = 95
  ```

## Scalaのデータ型

- 数値
  - `Byte`：8ビット符号付き整数
  - `Short`：16ビット符号付き整数
  - `Int`：32ビット符号付き整数
  - `Long`：64ビット符号付き整数
  - `Float`：32ビット浮動小数点数
  - `Double`：64ビット浮動小数点数
  - `BigInt`：任意の精度の整数
  - `BigDecimal`：任意の精度の浮動小数点数
- 真偽値
  - `Boolean`：`true`または`false`
- 文字
  - `Char`：16ビット符号なしUnicode文字
- 文字列
  - `String`：同じ内容でも異なるインスタンスが存在
  - `Symbol`：同じ内容ならインスタンスも等しい
- その他
  - `Unit`：何も返さないことを示す型（Javaの`void`）
  - `Any`：Scalaのすべての型のスーパークラス
  - `AnyVal`：Javaのプリミティブ型に相当する型のスーパークラス
  - `AnyRef`：参照型（Javaのオブジェクト型）のスーパークラス
  - `Option`：値が存在するかもしれないし、ないかもしれないことを表す型
  - `List`, `Array`, `Map`, `Set`：コレクション型

## 文字列補完（String Interpolation）

```scala
val name = "Alice"
println(s"Hello, $name!")  // → Hello, Alice!
```

- `s"文字列"`：文字列補完のプレフィックス
- `${}`や`$変数名`で文字列に変数を埋め込める

<br>

→[2. 関数](02_function.md)