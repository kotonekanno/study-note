# Model

- データやドメインルールを定義する
- DBとのやり取りを担当する（クエリ、保存、更新など）

### 目次

- [基本的なデータモデル](#基本的なデータモデル)
- [DBとの連携](#dbとの連携)
- [Modelの役割例](#modelの役割例)

## 基本的なデータモデル

Playでは通常、`case class`を使ってデータ構造を定義する

```scala
package models

case class User(id: Long, name: String, email: String)
```

## DBとの連携

PlayではDBアクセスにSlickライブラリがよく使われる（他にAnormなど）

```scala
class Users(tag: Tag) extends Table[User](tag, "users") {
  def id = column[Long]("id", O.PrimaryKey, O.AutoInc)
  def name = column[String]("name")
  def email = column[String]("email")
  def * = (id, name, email) <> (User.tupled, User.unapply)
}
```

## Modelの役割例

- DBのテーブル定義（ORM的）
- フィルタ、検索、保存、削除
- ドメインロジック（年齢制限、ステータス判定など）