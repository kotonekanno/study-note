# 関数

### 目次

- [関数定義](#関数定義)

## 関数定義

CoffeeScriptの関数定義には2種類ある

- `->`：通常の関数（JSのfunction）
  - 呼び出し元に応じて`this`が変わる
- `=>`：`this`を固定する関数（JSのアロー関数）
  - 定義された時の`this`を維持し、呼び出し側のコンテキストに依存しない
 
```coffeescript
class Counter
  constructor: ->
    @count = 0
    @intervalId = setInterval (() => @count++), 1000

  getCount: ->
    @count

  reset: ->
    @count = 0

  pause: ->
    clearInterval @intervalId
```

→[if文](02_if_statement.md)
