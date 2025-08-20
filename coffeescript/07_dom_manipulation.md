# DOM操作実践

### 目次

- [基本](#基本)
  - [課題１](#課題１)
  - [課題2](#課題2)
  - [課題3](#課題3)
  - [課題4](#課題4)
- [応用](#応用)
  - [課題１：チェック付きToDo](#課題１チェック付きtodo)
  - [課題２：ダブルクリックでリスト項目を編集](#課題２ダブルクリックでリスト項目を編集)
  - [課題３：リアルタイム検索フィルター](#課題３リアルタイム検索フィルター)

## 基本

### 課題１

```html
<input type="text" id="itemInput">
<button id="addButton">追加</button>
<ul id="itemList"></ul>
```

- 上記HTMLに対応したコード（リストに追加＆クリックで削除）
- 入力が空なら何も追加されないようにする
- 追加後、入力欄を空に戻す

<br>

解答例：

```coffeescript
$ ->
  $('#addButton').on 'click', ->
    text = $('#itemInput').val()
    return unless text?.trim()
    
    li = $("<li>#{text}</li>")
    $('#itemList').append li

    li.on 'click', -> $(this).remove()
    $('#itemInput').val('')
```

- `$->`：DOM構築完了時に実行する
- `text?`：＝`text != null`（`null`または`undefined`ではない）
- `.trim`：空白入力の排除
- `unless`：早期リターン

### 課題2

```html
<input id="taskInput">
<button id="addTask">追加</button>
<ul class="taskList"></ul>
```

- 入力→「追加ボタン」で`<ul>`にリスト追加（`class`指定あり）
- 空欄を無視して、`.tasklist`に`<li>`を追加
- クリックされた`<li>`は削除される

<br>

解答例：

```coffeescript
$ ->
  $("#addTask").on 'click', ->
    text = $("#taskInput").val()
    return unless text?.trim()

    li = $("<li>#{text}</li>")
    $(".taskList").append li

    li.on 'click', -> $(this).remove()
    $("#taskInput").val('')
```

### 課題3

```html
<input id="itemInput">
<ul id="itemList"></ul>
```

- 「Enterキー」で追加
- 入力中にEnterキー（keyCode 13）を押すと`<li>`が追加される
- 入力が空白なら無視
- `click`で項目を削除

<br>

解答例；

```coffeescript
$ ->
  $("#itemInput").on 'keypress', (evt) ->
    if evt.which == 13
      text = $("#itemInput").val()
      return unless text?.trim()

      li = $("<li>#{text}</li>")
      $("#itemList").append li

      li.on 'click', -> $(this).remove()
      $("#itemInput").val('')
```

### 課題4

```html
<input id="noteInput">
<button id="addNote">追加</button>
<button id="clearAll">全削除</button>
<ul id="noteList"></ul>
```

- 「削除」ボタンでリスト全削除
- `addNote`でリスト追加（空白無視）
- `clearAll`を押すと`#noteList`を空にする

<br>

解答例：

```coffeescript
$ ->
  $('#clearAll').on 'click', ->
    $('#noteList .notes').remove()

  $('#addNote').on 'click', ->
    text = $('#noteInput').val()
    return unless text?.trim()

    li = $("<li class='notes'>#{text}</li>")
    $('#noteList').append li
    $('#noteInput').val('')
```

<br>

## 応用

### 課題１：チェック付きToDo

```html
<input id="todoInput">
<button id="addTodo">追加</button>
<ul id="todoList"></ul>
```

- 追加時、`<li>`の中にチェックボックス+ラベルを入れる
- チェックされた項目は横線
- チェック解除で横線は外れる

<br>

解答例：

```coffeescript
$ ->
  $("#addTodo").on 'click', ->
    text = $("#todoInput").val()
    return unless text?.trim()

    li = $("<li>
              <label>
                <input type='checkbox'>#{text}
              </label>
            </li>")

    $("#todoList").append li
    $("#todoInput").val('')
  
  $("#todoList").on 'click', (e) ->
    checkbox = $(e.target)
    if checkbox.prop('checked')
      checkbox.closest('li').css 'text-decoration', 'line-through'
    else
      checkbox.closest('li').css 'text-decoration', 'none'
```

- 改善例：`toggleClass('done')`にして、CSS側で`text-decoration`を管理

### 課題２：ダブルクリックでリスト項目を編集

```html
<input id="todoInput">
<button id="addTodo">追加</button>
<ul id="todoList"></ul>
```

- `<li>`をダブルクリックすると、入力欄に変わる
- 編集後にEnterを押すと確定し、テキスト表示に戻る

### 課題３：リアルタイム検索フィルター

```html
<input id="filterInput">
<ul id="filterList">
  <li>Apple</li>
  <li>Banana</li>
  <li>Cherry</li>
</ul>
```

- `#filterInput`に文字を入力すると、`filterList li`の中で一致しない要素は非表示になる（大文字小文字は無視）
