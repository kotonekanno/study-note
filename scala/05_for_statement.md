# for式

### 目次

- [for式](#for式-1)

## 基本文法
  
```scala
val numbers = List(1, 2, 3, 4, 5)

for (n <- numbers) {
  println(n)
}
```

- `numbers`の全要素を順に取り出し、`println`で出力する

## フィルタとyield

```scala
val evenNumbers = for {
  n <- numbers
  if n % 2 == 0
} yield n * 2
```

- `if`：フィルタ条件
- `yield`：結果のコレクションを返す（`map`のような役割）

<br>

参照：[サンプルコード](00_sample_codes.md#5-for式)

<br>

→[6. クラス](06_class.md)