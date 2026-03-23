<!-- omit in toc -->
# フォーム送信 / バリデーション

<!-- omit in toc -->
### 目次

- [概要](#概要)
- [基本構文](#基本構文)
  - [フォームクラス定義（DTO形式）](#フォームクラス定義dto形式)
  - [Controllerでフォームを受け取る](#controllerでフォームを受け取る)
  - [サービス層で処理を実行](#サービス層で処理を実行)
  - [Thymeleafを使う場合の例](#thymeleafを使う場合の例)
- [フォームクラス定義における主なアノテーション](#フォームクラス定義における主なアノテーション)

## 概要

- フォーム送信：ユーザがWebページのフォームに入力したデータをサーバー側で受け取り、検証して処理する一連の流れのこと
- Spring Bootでは、以下の3要素で構成される
  1. Controller：フォームでデータを受け取る
  2. Model（DTP/Formクラス）：入力データの受け皿
  3. Validation：入力値のチェック（`@Valid`/`@NotBlank`など）

<!-- omit in toc -->
#### 処理の流れ

```
HTMLフォーム → DTO（Formクラス） → Controller → Service → Repository
```

<!-- omit in toc -->
#### バリデーションの流れ

1. `@Valid`で自動検証
2. エラーがあれば`BidingResult`に格納
3. 問題なければService層へ

## 基本構文

### フォームクラス定義（DTO形式）

```java
import jakarta.validation.constraints.*;

public class UserForm {

  @NotBlank(message = "名前を入力してください")
  private String name;

  @Min(value = 0, message = "年齢は0以上でなければなりません")
  @Max(value = 120, message = "年齢は120以下でなければなりません")
  private int age;

  @Email(message = "メールアドレスの形式が不正です")
  private String email;

  // getter / setter 省略
}
```

- `@NotBlank`：空文字不可（`null`と空白の両方を弾く）
- `@Email`：形式チェック
- `@Min` / `@Max`：数値の範囲制限

### Controllerでフォームを受け取る

```java
import org.springframework.validation.BindingResult;
import org.springframework.web.bind.annotation.*;

@RestController
@RequestMapping("/users")
public class UserController {

  private final UserService userService;
  public UserController(UserService userService) {
    this.userService = userService;
  }

  // POSTフォーム受け取り
  @PostMapping("/register")
  public String registerUser(@RequestBody @Valid UserForm form, BindingResult result) {
    if (result.hasErrors()) {
      // バリデーションエラー内容を返す
      return result.getAllErrors().toString();
    }
    userService.createUser(form);
    return "登録成功！";
  }
}
```

- `@Valid`：自動でフォームの値を検証
- `BindingResult`：エラー結果を受け取るオブジェクト

### サービス層で処理を実行

```java
import org.springframework.stereotype.Service;

@Service
public class UserService {

  private final UserRepository repository;
  public UserService(UserRepository repository) {
    this.repository = repository;
  }

  public void createUser(UserForm form) {
    User user = new User();
    user.setName(form.getName());
    user.setAge(form.getAge());
    user.setEmail(form.getEmail());
    repository.save(user);
  }
}
```

### Thymeleafを使う場合の例

```html
<form th:action="@{/users/register}" method="post" th:object="${userForm}">
  <input type="text" th:field="*{name}" placeholder="名前">
  <input type="number" th:field="*{age}" placeholder="年齢">
  <input type="email" th:field="*{email}" placeholder="メール">
  <button type="submit">送信</button>

  <div th:if="${#fields.hasErrors('*')}">
    <ul>
      <li th:each="err : ${#fields.errors('*')}" th:text="${err}"></li>
    </ul>
  </div>
</form>
```

## フォームクラス定義における主なアノテーション

- `@NotBlank`：空文字不可
- `@NotNull`：`null`不可
- `@Min` / `@Max`：数値の範囲制限
- `@Size(min, max)`：文字列の長さ制限
- `@Email`：メール形式チェック
- `@Pattern(regaxp="...")`：正規パターン表現

<br>

→　次：[例外処理](07_exeption_handling.md)