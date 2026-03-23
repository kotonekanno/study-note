<!-- omit in toc -->
# アノテーション一覧

<!-- omit in toc -->
### 目次

- [コンポーネント定義](#コンポーネント定義)
  - [`@Controller`](#controller)
  - [`@RestController`](#restcontroller)
  - [`@Service`](#service)
  - [`@Repository`](#repository)
  - [`@Component`](#component)
  - [`@Configuration`](#configuration)
- [リクエストマッピング](#リクエストマッピング)
  - [`@RequestMapping`](#requestmapping)
  - [`@GetMapping`](#getmapping)
  - [`@PostMapping`](#postmapping)
  - [`@PutMapping`](#putmapping)
  - [`@DeleteMapping`](#deletemapping)
  - [パス指定パターン](#パス指定パターン)
- [リクエストパラメータバインド](#リクエストパラメータバインド)
  - [@RequestParam](#requestparam)
  - [`@PathVariable`](#pathvariable)
  - [`@RequestBody`](#requestbody)
  - [`@ModelAttribute`](#modelattribute)
- [バリデーション](#バリデーション)
  - [`@Valid`](#valid)
  - [`@Validated`](#validated)
  - [バリデーション制約](#バリデーション制約)
- [例外処理・レスポンス制御](#例外処理レスポンス制御)
  - [`@ExceptionHandler`](#exceptionhandler)
  - [`@ControllerAdvice`](#controlleradvice)
  - [`@ResponseStatus`](#responsestatus)

## コンポーネント定義

### `@Controller`

- Viewを返すControllerクラスを示す
- HTTPリクエストを受けて、View名を返す
- メソッドの戻り値（`String`）：テンプレート名

### `@RestController`

- API用のControllerクラスを示す
- HTTPリクエストを受けて、データ（JSON/XML/文字列）を直接返す
- `@Controller` + `@ResponceBody`の省略形

### `@Service`

- Serviceクラスを示す
- ビジネスロジックを持つ

### `@Repository`

- Repositoryクラスを示す
- DBアクセスを行う、永続化層（DAO）
- DB例外をSpringの例外に変換する
- JPA使用時は明示しないことも多い

### `@Component`

- Soring管理オブジェクト（Bean）として登録するための汎用アノテーション
- `@Service` / `@Repository` / `@Controller`の親
- 役割が明確でないクラスに使う
- 通常は専用アノテーションを優先

### `@Configuration`

- 設定クラスを示す
- `@Bean`定義をまとめる
- Spring起動時に読み込まれる
- 外部ライブラリ設定などで使用


## リクエストマッピング

### `@RequestMapping`

- HTTPリクエストと処理メソッド（またはクラス）を紐付ける
- GET / POST / PUT / DELETE全てに対応
- `@GetMapping` / `@PostMapping` / `@PutMapping` / `@DeleteMapping`の親
- クラスに付けることで共通パスを指定できる

```java
@RequestMapping("/path")

@RequestMapping(value = "/path", method = RequestMethod.POST)
```

### `@GetMapping`

- HTTP GETリクエスト専用のマッピング
- 一覧表示・詳細表示で使用
- `@RequestMapping(method = GET)`の省略形
- URL直接アクセス・リンク遷移

```java
@GetMapping("/path")
```

### `@PostMapping`

- HTTP POSTリクエスト専用のマッピング
- フォーム送信・登録処理で使用

```java
@PostMapping("/path")
```

### `@PutMapping`

- HTTP PUTリクエスト専用のマッピング
- データ更新処理で使用
- REST API向けであり、ブラウザフォームからは直接使われにくい

```java
@PutMapping("/path")
```

### `@DeleteMapping`

- HTTP DELETEリクエスト専用のマッピング
- データ削除処理で使用
- REST API向けであり、HTMLフォームではPOSTに代用されることが多い

```java
@DeleteMapping("/path")
```

### パス指定パターン

- 固定パス：`@GetMapping("/path")`
- パス変数：`@GetMapping("/path/{id}")`


## リクエストパラメータバインド

### @RequestParam

- クエリパラメータ／フォームパラメータを受け取る
- 例：`/users?id=10`

```java
@GetMapping("/users")
public String users(@RequestParam String name) {
}
```

<!-- omit in toc -->
#### パラメータ名指定

```java
@RequestParam("user_id") Long id
```

<!-- omit in toc -->
#### 任意パラメータ

```java
@RequestParam(required = false) String name
```

<!-- omit in toc -->
#### デフォルト値

```java
@RequestParam(defaultValue = "0")
```

### `@PathVariable`

- URLパスの一部を変数として受け取る
- 例：`/users/10`

```java
@GetMapping("/users/{id}")
public String user(@PathVariable Long id) {
}
```

### `@RequestBody`

- リクエストボディ（主にJSON）をオブジェクトに変換して受け取る
- 例：`{ "name": "John", "age": 20 }`
- REST API用であり、フォーム送信（HTML）では使わない

```java
@PostMapping("/users")
public void create(@RequestBody UserForm form) {
}
```

### `@ModelAttribute`

- フォームデータをオブジェクトに変換して受け取る
- `@Valid`と組み合わせる
- Modelにも自動で入る

```java
@PostMapping("/users")
public String submit(@ModelAttrivute UserForm form) {
}

// 省略形
public String submit(UserForm form)
```


## バリデーション
### `@Valid`

- Bean Validation（アノテーション検証）を実行する
- 主にフォーム入力チェックで使用
- Controllerメソッドの引数で使用
- 失敗すると、エラー情報が[`BindingResult`](classes.md#bindingresult)に入る

```java
import jakarta.validation.constraints.*;

@PostMapping("/users")
public String submit(@Valid UserForm form, BindingResult result) {
}
```

### `@Validated`

- `@Valid`の拡張版
- バリデーショングループを指定できる
- 条件別バリデーションが必要なときに使う

```java
@PostMapping("/users")
public String submit(@Validated UserForm form, BindingResult result) {
}
```
```java
// グループ指定
@Validated(Create.class)
UserForm form
```

### バリデーション制約

- `@NotBlank`：空文字不可
- `@NotNull`：`null`不可
- `@NotEmpty`：
- `@Min` / `@Max`：数値の範囲制限
- `@Size(min, max)`：文字列の長さ制限
- `@Email`：メール形式チェック
- `@Pattern(regaxp="...")`：正規パターン表現


## 例外処理・レスポンス制御

### `@ExceptionHandler`

- 特定の例外が発生したときの処理を定義する
- Controller内、または共通例外処理で使用
- 対象Controller内でのみ有効
- 返り値：通常のControllerと同じ（ViewまたはResponse）

```java
@ExceptionHandler(illegalArgumentException.class)

@ExceptionHandler({ illegalArgumentException.class, NullPointerException.class })
```

### `@ControllerAdvice`

- 例外処理を全Controller共通で適用する
- グローバル例外ハンドラ
- `@ExceptionHandler`とセットで使う

```java
@ControllerAdvice
public class GlobalExceptionHandler {
  
  @ExceptionHandler(Exception.class)
  public String handle(Exception e) {
    return "error";
  }
}
```

### `@ResponseStatus`

- HTTPステータスコードを指定する
- 例外またはメソッドに付与

```java
// 例外クラスに付ける
@ResponseStatus(HttpStatus.NOT_FOUND)
public class UserNotFoundException extends RuntimeException {
}

// 使用側
throw new UserNotFoundException();
```
```java
// メソッドに付ける
@ResponseStatus(HttpStatus.BAD_REQUEST)
@ExceptionHandler(IllegalArgumentException.class)
public void handle() {
}
```