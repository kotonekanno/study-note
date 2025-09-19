<!-- omit in toc -->
# リスト内包表記

### 目次

- [リスト内包表記](#リスト内包表記-1)
- [サンプルコード](#サンプルコード)

## リスト内包表記

- Pythonのように、`for`を使って1行でアタっらしい配列を作れる構文

<br>

- 基本形
  
  ```coffeescript
  squares = (x * x for x in [1..5])
  console.log squares  # [1, 4, 9, 16, 25]
  ```

- 条件付き生成（`when`）
  
  ```coffeescript
  evens = (x for x in [1..10] when x % 2 == 0)
  console.log evens  # [2, 4, 6, 8, 10]
  ```

- ネスト（2次元配列など）

  ``` coffeescript
  pairs = ([x, y] for x in [1..2] for y in [1..2])
  console.log pairs
  # => [[1,1], [1,2], [2,1], [2,2]]
  ```

- ステップ指定（`by`句）

  ```coffeescript
  byTwo = (x for x in [1..10] by 2)
  console.log byTwo  # [1, 3, 5, 7, 9]
  ```

## サンプルコード

```coffeescript
squares = (x * x for x in [1..10])
console.log squares
```

```coffeescript
console.log "task2"
divByThree = (y for y in [1..20] by 3)
console.log divByThree
```

```coffeescript
console.log "task4"
odd = (z for z in [1..10] by 2)
console.log odd
```
