# if文

### 目次

- [if文](#if文-1)
- [unless文](#unless文)
- [単行条件式（行末if/unless）](#単行条件式行末ifunless)
- [thenキーワード](#thenキーワード)
- [三項演算子的な記法](#三項演算子的な記法)
- [サンプルコード](#サンプルコード)

## if文

CoffeeScriptのif文はインデントで区切る

```coffeescript
if condition
  # 条件が真のときの処理
else
  # 条件が偽のときの処理
```

## unless文

条件が偽の時に実行する特殊なif文

```coffeescript
unless condition
  # 条件が偽のときの処理
```

## 単行条件式（行末if/unless）

単純な条件式は行末にかける

```coffeescript
console.log 'OK' if success
console.log 'NG' unless success
```

## thenキーワード

`if`と`then`を使うことで1行で書ける

```coffeescript
if a > b then console.log "a is bigger"
```

## 三項演算子的な記法

```coffeescript
message = if isOk then "Success" else "Failure"
```

## サンプルコード

```coffeesctipt
greet = (name) -> if name then "Hello, " + name else "Hello, stranger"
```

```coffeescript
checkActive = (isActive) ->
  console.log "Inactive" unless isActive

scoreCheck = (score) ->
  console.log if score >= 80 then "Pass" else "Fail"
```

→[ループ文](03_loop.md)
