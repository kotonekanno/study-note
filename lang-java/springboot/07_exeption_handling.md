<!-- omit in toc -->
# 例外処理

<!-- omit in toc -->
### 目次

- [概要](#概要)
- [基本構文](#基本構文)
  - [REST API用のレスポンス（JSON形式）](#rest-api用のレスポンスjson形式)


## 概要

SpringBootでは、主に以下の2レイヤーで扱う

1. Service層で業務エラーを投げる（throw）
2. Controller層で例外をまとめてキャッチする（`@ControllerAdvice`）

## 基本構文

1. アプリ内で使う独自例外（カスタム例外）
   ```java
   public class UserNotFoundException extends RuntimeException {
    public UserNotFoundException(String message) {
      super(message);
    }
   }
   ```

   - `RuntimeException`：これを継承すると、Springによるロールバックなどと相性が良い

2. Service層で例外を投げる
   ```java
   @Service
   public class UserService {
    private final UserRepository repository;
    public UserService(UserRepository repository) {
      this.repository = repository;
    }

    public User findUser(Long id) {
      return repository.findById(id)
        .orElseThrow(() -> new UserNotFoundException("ユーザーが見つかりません：" + id));
    }
   }
   ```

   - `.orElseThrow()`：例外発生
   - 異常を検知したら、例外でControllerに渡す

3. Controllerで例外をまとめて処理（@ControllerAdvice）
   ```java
   import org.springframework.web.bind.annotation.*;

   @ControllerAdvice
   public class GlobalExceptionHandler {

    @ExceptionHandler(UserNotFoundException.class)
    @ResponseBody
    @ReponseStatus(code = HttpStatus.NOT_FOUND)
    public String handleUserNotFound(UserNotFoundException ex) {
      return ex.getMessage();
    }

    @ExceptionHandler(Exception.class)
    @ResponseBody
    @ResponseStatus(code = HttpStatus.INTERNAL_SERVER_ERROR)
    public String handleOtherExceptions(Exception ex) {
      return "内部エラーが発生しました";
    }
   }
   ```

   - `@ControllerAdvice`：全Controllerの例外を横断的に処理
   - `@ExceptionHandler`：特定の例外に反応
   - `@ResponseStatus`：HTTPステータスを指定
   - `@ResponseBody`：レスポンスをそのまま返す

### REST API用のレスポンス（JSON形式）

```java
public class ErrorResponse {
  private String message;
  private int code;

  public ErrorResponse(String message, int code) {
    this.message = message;
    this.code = code;
  }

  // getter / setter
}
```

```java
@ExceptionHandler(UserNotFoundException.class)
@ResponseStatus(HttpStatus.NOT_FOUND)
@ResponseBody
public ErrorResponse handleUserNotFound(UserNotFoundException ex) {
  return new ErrorResponse(ex.getMessage(), 404);
}
```