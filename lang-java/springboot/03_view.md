<!-- omit in toc -->
# View / テンプレートエンジン（Thymeleaf）

<!-- omit in toc -->
### 目次

- [基本構文](#基本構文)
  - [Controller側](#controller側)
  - [Thymeleaf](#thymeleaf)
- [Thymeleafの主な構文](#thymeleafの主な構文)
- [Conroller → View間の値の受け渡し](#conroller--view間の値の受け渡し)
  - [String](#string)
  - [List](#list)
  - [Object](#object)

## 基本構文

- テンプレートエンジン**Thymeleaf**を使って、ControllerからView（HTML）にデータを渡し、動的なページを作成する
- データの流れ：`Controller → Model → View`

### Controller側

```java
package com.example.demo.controller;

import org.springframework.stereotype.Controller;
import org.springframework.ui.Model;
import org.springframework.web.bind.annotation.GetMapping;

@Controller
public class GreetingController {

    @GetMapping("/greet")
    public String greet(Model model) {
        model.addAttribute("name", "ユーザーさん");
        return "greet"; // templates/greet.html を表示
    }
}
```

- `Model`：Viewに値を渡すデータのコンテナ
  - `addAttribute("key", value)`で渡す

### Thymeleaf

`greet.html`：

```java
<!DOCTYPE html>
<html xmlns:th="http://www.thymeleaf.org">
<head>
    <title>Greeting</title>
</head>
<body>
    <h1 th:text="'こんにちは、' + ${name} + '！'"></h1>
</body>
</html>
```

- 結果：`こんにちは、ユーザーさん！`

## Thymeleafの主な構文

- `th:text`：テキストを埋め込む
  ```html
  <p th:text="${msg}"></p>
  ```
- `th:href`：リンクのパスを設定
  ```html
  <a th:href="@{/home}">Home</a>
  ```
- `th:if`, `th:unless`：条件分岐
  ```html
  <p th:if="${login}">ようこそ</p>
  ```
- `th:each`：ループ
  ```html
  <li th:each="item : ${list}" th:text="${item}"></li>
  ```
- `th:<object>` / `*{}`：フォームオブジェクトを参照
  ```html
  <input th:field="*{name}">
  ```

## Conroller → View間の値の受け渡し

### String

単一の値

- Controllerでの書き方
  ```java
  model.addAttribute("msg", "Hello");
  ```

- Viewでの書き方
  ```html
  ${msg}
  ```

### List<T>

配列：リスト

- Controllerでの書き方
  ```java
  model.addAttribute("list", "users");
  ```

- Viewでの書き方
  ```html
  th:each="u : ${list}"
  ```

### Object

DTOやEntity

- Controllerでの書き方
  ```java
  model.addAttribute("user", user);
  ```

- Viewでの書き方
  ```html
  ${user.name}
  ```

<br>

→　次：[Service / DI（依存性注入）](04_service.md)