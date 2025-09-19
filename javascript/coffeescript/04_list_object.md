<!-- omit in toc -->
# 配列・オブジェクト操作

### 目次

- [分割代入（Destructuring）](#分割代入destructuring)
  - [配列](#配列)
  - [オブジェクト](#オブジェクト)
- [スプレッド構文](#スプレッド構文)
  - [配列](#配列-1)
  - [オブジェクト](#オブジェクト-1)
- [関数引数の分割代入](#関数引数の分割代入)
- [サンプルコード](#サンプルコード)

## 分割代入（Destructuring）

### 配列

```coffeescript
[arr1, arr2] = [1, 2]
console.log arr1  # 1
console.log arr2  # 2
```

スキップすることもできる

```coffeescript
[ , second] = [10, 20]
console.log second  # 20
```

### オブジェクト

```coffeescript
user = {name: "Alice", age: 30}
{name, age} = user
console.log name  # "Alice"
```

変数名を変えたい場合

```coffeescript
{name: userName, age: userAge} = user
```

## スプレッド構文

### 配列

```coffeescript
nums = [1, 2, 3]
moreNums = [...nums, 4, 5]
console.log moreNums  # [1, 2, 3, 4, 5]
```

### オブジェクト

```coffeescript
base = {a: 1, b: 2}
extended = {...base, c: 3}
console.log extended  # {a: 1, b: 2, c: 3}
```

## 関数引数の分割代入

```coffeescript
printUser = ({name, age}) ->
  console.log "#{name} is #{age} years old"

user = {name: "Bob", age: 22}
printUser user
```

## サンプルコード

```coffeescript
console.log "task1"
[ , second, ,] = [1, 2, 3,]
console.log second

console.log "task2"
book = title: "Book", price: 500
{title, price} = book
cost = price
console.log cost

console.log "task3"
nums = [10, 20, 30,]
extended_nums = [...nums, 40, 50]
console.log extended_nums

console.log "task4"
printPerson = ({name, age}) ->
  console.log "#{name} (#{age})"
person = name: "Eve", age: 28
printPerson person
```
