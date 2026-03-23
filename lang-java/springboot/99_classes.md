<!-- omit in toc -->
# 頻出クラス一覧

<!-- omit in toc -->
### 目次

- [フォーム・バインディング](#フォームバインディング)
  - [`Model`](#model)
  - [`BindingResult`](#bindingresult)
- [HTTP / Webレスポンス](#http--webレスポンス)
  - [`HttpStatus`](#httpstatus)
  - [`Response Entity<T>`](#response-entityt)
- [例外処理（Exception）](#例外処理exception)
  - [`Exception`](#exception)
  - [`RuntimeException`](#runtimeexception)
  - [`ResponseStatusException`](#responsestatusexception)
  - [まとめ](#まとめ)
- [Java標準コレクション](#java標準コレクション)
  - [`List<E>`](#liste)
  - [`Optional<T>`](#optionalt)
- [JPA / 永続化（Entity）](#jpa--永続化entity)
  - [`Entity`](#entity)
  - [`Id`](#id)
  - [`Generated Value`](#generated-value)

## フォーム・バインディング

### `Model`

- `org.springframework.ui.Model`
- ControllerからViewにデータを渡すコンテナ
- Controllerメソッド内で、主に`@GetMapping`, `@PostMapping`の引数として使う
- 追加したデータはテンプレート側で参照可能になる
- HTML（Thymeleaf）を返す場合のみ使い、`@RestController`では基本的に使わない

<!-- omit in toc -->
#### 基本構文

```java
@GetMapping("/user")
public String user(Model model) {
  model.addAttribute("users", users);
  return "user";
}
```

- `model.addAttribute("key", value);`
  - key：HTML側で参照する名前
  - value：Javaオブジェクト（List, Entity, Formなど）
- `return "template";`：テンプレート名を返す

<!-- omit in toc -->
#### 特徴

- リクエストスコープ（1リクエストで消える）
- セッションには保存されてない
- 同じキー名を使うと上書きされる

<!-- omit in toc -->
#### 関連クラス

- `Model`：最もシンプル、推奨
- `ModelMap`：Map実装
- `ModelAndView`：View名も一緒に持つ（古）


### `BindingResult`

- `org.springframework.validation.BindingResult`
- バリデーション結果を保持するオブジェクト
- エラー有無／内容を取得できる

<!-- omit in toc -->
#### 基本構文

```java
public String submit(
  @Valid UserForm form,
  BindingResult result
) {
}
```

- 必ず`@Valid`（または`@Validated`）の直後に置く

<!-- omit in toc -->
#### メソッド

- `result.hasErrors()`
- `result.getAllErrors()`
- `result.getFieldErrors()`


## HTTP / Webレスポンス

### `HttpStatus`

- `org.springframework.http.HttpStatus`
- HTTPステータスコードを表すenum
- Springのレスポンス制御全体で使われる
- 使用する場所：
  - `ResponseEntity`
  - `@ResponseStatus`
  - `ResponseStatusException`
  - テストコード

<!-- omit in toc -->
#### ステータス

- `OK`：`200`　成功
- `CREATED`：`201`　作成成功
- `BAD_REQUSET`：`400`　リクエスト不正
- `UNAUTHORIZED`：`401`　認証失敗
- `FORBIDDEN`：`403`　権限なし
- `NOT_FOUND`：`404`　見つからない
- `CONFLICT`：`409`　競合
- `INTERNAL_SERVER_ERROR`：`500`　サーバーエラー

<!-- omit in toc -->
#### 基本構文

```java
// ResponseEntityと一緒に使う
return new ResponseEntity<>(user, HttpStatus.OK);
```
```java
// @ResponseStatusで使う
@ResponseStatus(HttpStatus.NOT_FOUND)
public class UserNotFoundException extends RuntimeExceptoin {
}
```

<!-- omit in toc -->
#### メソッド

- 数値の取得：`HttpStatus.OK.value();`


### `Response Entity<T>`

- `org.springframework.http.ResponseEntity`
- HTTPレスポンス全体を表すクラス
- レスポンスボディ、ステータスコード、ヘッダーをまとめて制御できる
- 使用する場所：
  - `@RestController`
  - `@Controller` + `@ResponseBody`
  - API実装時の標準

<!-- omit in toc -->
#### 基本構文

```java
return new ReponseEntity<T>(body, HttpStatus.OK)
```

- `body`：レスポンス本文（JSONなど）
- `HttpStatus`：ステータスコード
- `<T>`：レスポンスボディの型

<!-- omit in toc -->
#### Builder形式

<!-- omit in toc -->
##### ステータス（`200 OK`） + ボディを返す

```java
return ResponseEntity.ok(user);
```
- `.ok(T body)`：
  - GETの成功レスポンス
  - ステータス（`200 OK`） + ボディを返す

<!-- omit in toc -->
##### 任意のステータス + ボディを返す

```java
return ResponseEntity
  .status(HttpStatus.CREATED)
  .body(user);
```
- `.status(HttpStatus status)`
  - 任意のステータスを指定する
  - POST / PUT成功時など

<!-- omit in toc -->
##### ボディなしレスポンス

```java
return ResponseEntity.noContent().build();
```
- `.noContent()`：
  - `204 No Content`
  - DELETE成功時によく使う

```java
ResponseEntity.notFound().build();
```

- `.notFound()`：
  - 404 Not Found
  - リソースが存在しない場合

<!-- omit in toc -->
##### ヘッダーを設定する

```java
return ResponseEntity
  .ok()
  .header("X-My-Header", "value")
  .body(user);
```
- `.header(String name, string value)`：レスポンスヘッダーを追加

```java
// Locationヘッダー付き
ResponseEntity.created(uri).body(body);
```
- `.created(URI lcoation)`：
  - `021 Created`
  - 新規リソース作成時
  - `Location`ヘッダー自動付与

<!-- omit in toc -->
##### エラー時レスポンス

```java
ResponseEntity.badRequest().body("Invalid Request");
```

- `.badRequest()`
  - `400 Bad Request`
  - バリデーションエラーなど

```java
ResponseEntity.status(HttpStatus.UNAUTHORIZED).build();
```

- `.status(HttpStatus status)`：
  - 認証・認可エラーなど
  - 401, 403系


## 例外処理（Exception）

### `Exception`

- `java.lang.Exception`
- Javaにおけるチェック例外の基底クラス
  - 発生する可能性をコンパイル時に強制的に意識させる
  - `throws`または`try-catch`が必須
- 使用する場所
  - ファイル操作
  - IO
  - 外部API連携
  - 明示的に「呼び出し元で対処させたい」場合
- Spring MVCでは余り多用されない
- 必ずハンドリングが必要
- Controllerそうでは扱いづらい
- Webアプリでは上長になりがち

<!-- omit in toc -->
#### 基本構文

```java
public void read() throws Exception {
}
```
```java
try {
  read();
} catch (Exception e) {
}
```

<!-- omit in toc -->
#### 独自例外

```java
public class MyException extends Exception {
  public MyException(String message) {
    super(message);
  }
}
```


### `RuntimeException`

- `java.lang.RuntimeException`
- 非チェック例外の基底クラス
  - `throws` / `try-catch`が必須ではない
  - 実行時エラーを表現
- 使用する場所
  - 業務ロジックエラー
  - 不正状態
  - 想定外のケース
- Springアプリで主流
- Controllerでの扱い
  1. そのまま投げる
  2. `@ExceptionHandler`や`@ControllerAdvice`で処理 

<!-- omit in toc -->
#### 基本構文

```java
throw new RuntimeException("Error occurred");
```

<!-- omit in toc -->
#### 独自例外

```java
public class UserNotFoundException extends RuntimeException {
  public UserNotFoundException(String message) {
    super(message);
  }
}
```


### `ResponseStatusException`

- `org.springframework.web.server.ResponseStatusException`
- HTTPステータス付き例外
  - 例外を投げるだけでHTTPレスポンスを制御できる
  - `HttpStatusとセットで使用`
- 使用する場所
  - REST API
  - Controller / Service層
  - シンプルなエラー処理

<!-- omit in toc -->
#### 基本構文

```java
throw new ResponseStatusException(
  HttpStatus.NOT_FOUND,
  "User not found"
);
```

### まとめ

- `Exception`：
  - チェック例外の基底クラス
  - Java基盤処理
- `RuntimeException`：
  - 非チェック例外の基底クラス
  - 業務エラー
- `ResponseStatusException`
  - HTTPステータスを伴う例外
  - APIで即HTTP返却


## Java標準コレクション

### `List<E>`

- `java.util.List`
- 順序を持つコレクション（配列の上位互換）
  - 同じ型の要素を複数保持
  - インデックスでアクセス可能

```java
List<String> name;
List<User> users;

// 生成方法
List<String> list = new ArrayList<>();
List<String> list = List.of("A", "B", "C");

// 要素の追加・取得
list.add("A");
String value = list.get(0);

// ループ処理
for (User user : users) {
}
```


### `Optional<T>`

- `java.util.Optional`
- 「値が存在しない可能性」を表現するラッパー
- フィールドや引数には非推奨
- Repositoryの戻り値でよく使う

```java
Optional<User> user;

// 生成方法
Optional.of(value);       // null不可
Optional.ofNullable(val); // null可
Optional.empty();         // 空

// 値の取得
user.get();               // 非推奨（値がないと例外になる）

if (user.isPresent()) {   // 存在チェック
  User.u = user.get
}

// 値がなければ代替
User u = user.orElse(defaultUser);

// なければ例外
User u = user.orElseThrow();

User u = user.orElseThrow(
  () -> new RuntimeException("User not found")
);
```


## JPA / 永続化（Entity）

### `Entity`

- `jakarta.persistence.Entity`
- このクラスが「DBテーブルに対応するエンティティ」であることを示す
  - JPAによる永続化対象
  - クラスとテーブルの対応付け
  - Repositoryで扱えるようになる
- 使用する場所
  - DBと紐づくクラス
  - `@Repository`から操作されるクラス
- 引数なしコンストラクタ必須
- `final`クラスは不可
- フィールドは基本`private`

<!-- omit in toc -->
#### 基本構文

```java
@Entity
public class User {
}
```

<!-- omit in toc -->
#### テーブル名を指定

```java
@Entity
@Table(name = "users")
public class User {
}
```
- 省略するとクラス名がテーブル名になる


### `Id`

- `jakarta.persistence.Id`
- 主キーを表す
- `@Entity`クラスに必須
- 1クラスに1つだけ

<!-- omit in toc -->
#### 基本構文

```java
@Id
private Long id;
```

<!-- omit in toc -->
#### よく使われる型

- `Long`：最もよく使われる
- `Integer`
- `String`
- `UUID`


### `Generated Value`

- `jakarta.persistence.GeneratedValue`
- 主キーの自動生成方法を指定
- `@Id`とセットで使う

<!-- omit in toc -->
#### 基本構文

```java
@Id
@GeneratedValue(strategy = GenerationType.IDENTITY)
private Long id;
```

<!-- omit in toc -->
#### `strategy`の種類

- `GenerationType.IDENTITY`：DBのAUTO_INCREMENT（MySQL, H2）
- `GenerationType.AUTO`：JPAに任せる
- `GenerationType.SEQUENCE`：シーケンス使用（PostgreSQL等）
- `GenerationType.TABLE`：管理テーブル方式（非推奨）