<!-- omit in toc -->
# 引数

### 目次

- [デフォルト引数](#デフォルト引数)
- [可変超引数（スプレッド引数）](#可変超引数スプレッド引数)
- [引数の分割代入](#引数の分割代入)
- [サンプルコード](#サンプルコード)

## デフォルト引数

```coffeescript
greet = (name = "Guest") ->
  console.log "Hello, #{name}"
```

## 可変超引数（スプレッド引数）

```coffeescript
sum = (nums...) ->
  total = 0
  for n in nums
    total += n
  total
```

`nums...`は任意の数の引数を配列として受け取る

## 引数の分割代入

```coffeescript
showUser = ({name, age}) ->
  console.log "#{name} is #{age} years old"
```

## サンプルコード

```coffeescript
hello = (str = "World") ->
  console.log("Hello, #{str}")
hello()
hello('User')
```

```coffeescript
addAll = (nums...) ->
  sum = 0
  for i in nums
    sum += i
  console.log sum
addAll 1, 2, 3
```

```coffeescript
bookInfo = ({title, author}) ->
  console.log "title: #{title} author: #{author}"
book = {title: "Story", author: "John Smith"}
bookInfo(book)
```
