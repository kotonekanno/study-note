# 6. フォーム入力

### 目次

- [フォームとは](#フォームとは)
- [フォーム用のデータ構造定義](#フォーム用のデータ構造定義)
- [フォーム定義](#フォーム定義)
- [フォームデータの受け取り](#フォームデータの受け取り)
- [テンプレート側（HTML）との連携](#テンプレート側htmlとの連携)

## フォームとは

- ユーザーがWebページ上で情報を入力・送信するための仕組み
- フォームに入力された値は、HTTPリクエストとしてサーバに送られる
- Playでは、`Form`オブジェクトを使い、その値をScala型のデータに変換（**バインド**）して受け取る

## フォーム用のデータ構造定義

```scala
case class LoginData(email: String, password: String)
```

- `case class`でデータ構造を定義する
- 例：email、passwordという値を持つオブジェクトを作る

## フォーム定義

```scala
val loginForm: Form[LoginData] = Form(
  mapping(
    "email" -> email,
    "password" -> nonEmptyText
  )(LoginData.apply)(LoginData.unapply)
)
```

- Form型：フォームから送られてくるデータを受け取るための型
- `Form[LoginData]`：LoginData型のデータを受け取るフォームを意味する
- `"email"`：フォームのinput name属性
- `email`：Scala側の型（形式チェックも含む）

## フォームデータの受け取り

- `bindFromRequest`：リクエストの中にあるフォームデータを、Scalaのデータ型（case class）に変換する処理

```scala
loginForm.bindFromRequest.fold(
  formWithErrors => BadRequest("入力エラー"),        // 入力に不備がある場合
  loginData => Ok("ログイン成功: " + loginData.email) // 入力が正常な場合
)
```

## テンプレート側（HTML）との連携

```scala
@helper.form(action = routes.LoginController.login()) {
  @helper.inputText(loginForm("email"))
  @helper.inputPassword(loginForm("password"))
  <input type="submit" value="ログイン">
}
```

- `@helper.form(...)`：フォームの開始タグと送信先を生成
- `@helper.inputText(...)`：inputタグを自動生成し、エラー表示などもしてくれる

→[7. JSON API](07_json.md)