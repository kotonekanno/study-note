# 3. View（Twirlテンプレート）

### 目次

- [Twirlテンプレートとは](#twirlテンプレートとは)
- [テンプレートファイルの場所と名前](#テンプレートファイルの場所と名前)
- [基本構文](#基本構文)
- [テンプレート分割（共通レイアウト）](#テンプレート分割共通レイアウト)

## Twirlテンプレートとは

- Playに標準搭載されている、ScalaベースのHTMLテンプレートエンジン
- Scalaの式や変数をHTMLに埋め込める

## テンプレートファイルの場所と名前

- ディレクトリ：`app/views/`
- 拡張子：`.scala.html`

## 基本構文

例：
<details><summary>hello.scala.html</summary>

  ```scala
  @(name: String)

  <html>
    <body>
      <h1>Hello @name!</h1>
    </body>
  </html>
  ```

</details>

<details><summary>呼び出し元（Controller側）</summary>
  
  ```scala
  def hello(name: String) = Action {
    Ok(views.html.hello(name))
  }
  ```

</details>

- `@(...)`：テンプレートの引数宣言
- `@name`：変数の埋め込み
- `views.html.hello(...)`で呼び出す

## テンプレート分割（共通レイアウト）

共通のレイアウトを分離して、ヘッダーやフッターを一元管理できる

```scala
@main("タイトル") {
  <h1>中身</h1>
}
```

<br>

→[4. Routing](04_routing.md)