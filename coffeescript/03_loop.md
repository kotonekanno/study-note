# ループ文

### 目次

## forループ

### in

- `for item in list`
- 配列の要素を順に取り出すループ

```coffeescript
fruits = ['apple', 'banana', 'cherry']

for fruit in fruits
  console.log fruit
```

### of

- `for index, value of object`
- オブジェクトのキーと値を取り出すループ

```coffeescript
obj = {name: 'Alice', age: 25}

for key, val of obj
  console.log "#{key}: #{val}"
```

## whileループ

```coffeescript
i = 0

while i < 3
  console.log i
  i++
```

## レンジ演算子

- `start..end`：`start`から`end`までの範囲（終端含む）
- `start...end`：`start`から`end`までの範囲（終端含まない）

### for文との組み合わせ

```coffeescript
for i in [0..4]
  console.log i
```

## ガード（when）句

ループ中に条件をつけるときは、`when`を使う

```coffeescript
for i in [1..10] when i % 2 == 0
  console.log i
```

### サンプルコード

```coffeescript
console.log "偶数"
for i in [1..10] when i % 2 == 0
  console.log i
```

```coffeescript
console.log "辞書"
obj = {a:1, b:2, c:3}
for key, val of obj
  console.log "#{key}: #{val}"
```

```coffeescript
console.log "カウント"
j = 0;
while j <= 4
  console.log j
  j++
```

→[配列・オブジェクト操作](04_list_object.md)
