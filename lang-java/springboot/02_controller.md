<!-- omit in toc -->
# Controller

<!-- omit in toc -->
### 目次

- [基本構文](#基本構文)
- [画面を返す場合](#画面を返す場合)

## 基本構文

```java
package com.example.demo.controller;

import org.springframework.stereotype.Controller;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.ResponseBody;

@Controller
public class HelloController {

    @GetMapping("/hello")
    @ResponseBody
    public String hello() {
      return "Hello, Spring Boot!";
    }
}
```

- `@Controller`：ControllerクラスであることをSpringに明示する
- `@GetMapping("/hello")`：`GET /hello`にアクセスされたときに実行される
- `@ResponseBody`：戻り値をHTMLではなくそのまま文字列として返す（API向け）

## 画面を返す場合

- HTMLテンプレートを使う場合、`@ResponceBody`を外し、`resource/templates/`配下に`.html`ファイルを配置する

```java
@Controller
public class PageController {

    @GetMapping("/home")
    public String home() {
        return "home"; // → templates/home.html を探して返す
    }
}
```

- `/home`にアクセスすると、Thymeleafがテンプレートを解釈してHTMLを返す

<br>

→　次：[View / テンプレートエンジン（Thymeleaf）](03_view.md)