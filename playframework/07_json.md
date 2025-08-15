# JSON APIとのやり取り

### 目次

- [JSONとは](#jsonとは)
- [PlayでJSONを扱う](#playでjsonを扱う)
- [case classとJSONを変換](#case-classとjsonを変換)
- [ControllerでJSONを受け取る](#controllerでjsonを受け取る)
- [JSONを返す（レスポンス）](#jsonを返すレスポンス)

## JSONとは

- JSON, JavaScript Object Notation
- データを構造化して表現するためのシンプルなテキストフォーマット
- Webアプリ同士、特にサーバとクライアントの間のやり取りに使われる
- Playでは、サーバ側のScalaオブジェクトと、クライアントとやり取りするJSON形式のデータを**変換**する

```json
{
  "id": 1,
  "name": "ユーザー",
  "email": "user@example.com"
}
```

## PlayでJSONを扱う

- Playは標準で`play.api.libs.json`を使ってJSONを扱える
- インポートが必要

```scala
import play.api.libs.json._
```

## case classとJSONを変換

例：UserクラスをJSONに変換／変換から復元

```scala
case class User(id: Long, name: String)

object User {
  implicit val userFormat: Format[User] = Json.format[User]
}
```

- `Json.format[T]`：`Reads`（JSON→オブジェクト）と`Writes`（オブジェクト→JSON）を自動で生成

## ControllerでJSONを受け取る

```scala
def receiveJson = Action(parse.json) { request =>
  val result = request.body.validate[User]
  result.fold(
    errors => BadRequest("Invalid JSON"),
    user => Ok("Received user: " + user.name)
  )
}
```

- `Action(parse.json)`：「リクエストボディをJSONとして扱う」という宣言
- `request.body.validate[user]`：JSONをUserオブジェクトに変換しようとしている
- 変換に失敗するとエラーを返し、成功すると受け取ったデータで処理できる

## JSONを返す（レスポンス）

```scala
def getJson = Action {
  val user = User(1, "ユーザー")
  Ok(Json.toJson(user))
}
```

- `Json.toJson(user)`：UserオブジェクトをJSON文字列に変換
- この結果をHTTPレスポンスで返すことで、クライアントはJSONデータを受け取る