# Controllerの書き方と役割

Controllerとは  
  - リクエストを受けて処理の流れを制御する  
  - 必要に応じてModelを呼び、Viewにデータを渡す  
  
### 目次

- [Controllerの基本構文（Play + Scala）](#controllerの基本構文play--scala)
  - [Viewを返すパターン](#viewを返すパターン)

## Controllerの基本構文（Play + Scala）

ファイル例：` app/controllers/HomeController.scala`
```scala
package controllers

import javax.inject._
import play.api.mvc._

@Singleton
class HomeController @Inject()(cc: ControllerComponents) extends AbstractController(cc) {

  def index() = Action {
    Ok("Hello, Play Framework!")
  }
}
```

- ` @Singleton`：このクラスはアプリ全体で1つだけ使われる
- ` @Inject()`：DI（依存性注入）で必要な部品（ここではCC）を受け取る
- ` ControllerComponents`：コントローラに必要な共通機能のセット
- ` Action { ... }`：HTTPリクエストに対するアクション定義
- ` Ok(...)`：HTTP200レスポンスを返す

### Viewを返すパターン
```scala
def hello(name: String) = Action {
  Ok(views.html.hello(name))
}
```

- ` views.html.hello`は` app/views/hello.scala.html`に対応
- ScalaテンプレートエンジンTwirlでHTMLを生成