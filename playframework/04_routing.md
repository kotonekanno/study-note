# Routing

`conf/routes`ファイルで「どのURLに対してどのControllerのどのメソッドを呼ぶか」を定義

### 目次

- [基本構文](#基本構文)
- [クエリパラメータ／パスパラメータ](#クエリパラメータパスパラメータ)
  - [クエリパラメータ](#クエリパラメータ)
  - [パスパラメータ](#パスパラメータ)
  - [複数パラメータの指定例](#複数パラメータの指定例)

## 基本構文

```bash
GET     /hello           controllers.HomeController.hello
POST    /submit          controllers.FormController.submit
```

## クエリパラメータ／パスパラメータ

### クエリパラメータ

- `/user/42`
- URLに`?key=value`形式で追加情報を渡す 
- 任意要素、複数化、柔軟 

### パスパラメータ

- `/search?q=apple&page=2`
- URLの一部を変数として受け取る
- 構造の一部、必須

```routes
GET   /hello/:name     controllers.HomeController.hello(name: String)
```

- `/hello/ユーザー名`のようにアクセスすると、`name`に値が入る

### 複数パラメータの指定例

```routes
GET   /user/:id/profile/:section    controllers.UserController.profile(id: Long, section: String)
```

<br>

→[5. Model](05_model.md)