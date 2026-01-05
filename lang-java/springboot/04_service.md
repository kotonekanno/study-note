<!-- omit in toc -->
# Service / DI（依存性注入）

<!-- omit in toc -->
### 目次

- [基本構文](#基本構文)
- [ControllerでServiceを使う](#controllerでserviceを使う)
- [DI（依存性注入）とは](#di依存性注入とは)
  - [依存性注入方法の種類](#依存性注入方法の種類)
  - [Beanの範囲](#beanの範囲)

## 基本構文

```java
package com.example.demo.service;

import org.springframework.stereotype.Service;

@Service
public class GreetingService {

  public String getMessage(String name) {
    return "こんにちは、" + name + "さん！";
  }
}
```

- `@Service`：
  - このクラスがサービスそうであると伝えるアノテーション
  - このクラスは自動的にSpring管理下に置かれる（Bean登録）

## ControllerでServiceを使う

```java
package com.example.demo.controller;

import org.springframework.stereotype.Controller;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.ui.Model;
import com.example.demo.service.GreetingService;

@Controller
public class GreetingController {

  private final GreetingService greetingService;

  // 依存性注入（コンストラクタによるDI）
  public GreetingController(GreetingService greetingService) {
    this.greetingService = greetingService;
  }

  @GetMapping("/service")
  public String greeting(Model model) {
    String message = greetingService.getMessage("ユーザー");
    model.addAttribute("msg", message);
    return "service";
  }
}
```

- Springが`GreetingService`のインスタンスを自動で作り、`GreetingController`に注入する

## DI（依存性注入）とは

- **DI**
  - Dependency Injection、依存性注入
  - オブジェクト同士の依存関係をSpringが自動的に管理してくれる仕組み
  - Springが自動で`new`を差し込む
- **Bean**
  - Springが作った共有オブジェクト
  - これを書くと、Springは
    - 起動時に`new`する
    - インスタンス（Bean）をメモリに1個だけ作る
    - 以降は使いまわす

### 依存性注入方法の種類

1. コンストラクタ注入：`public Controller(Service s)`
   - 最も推奨される
   - 不変
   - テストしやすい
2. フィールド注入：`@Autowired private Service s;`
   - 簡単だが非推奨
   - テストしにくい
3. Setter注入：`@Autowired public void setService(Setvice s)`
   - 状況によっては使用可

### Beanの範囲

- `@Conponent`：汎用Bean
- `@Service`：ビジネスロジック層
- `@Repository`：データアクセス層
- `@Controller`：Web層（HTML返却、MVC用）
- `@RestController`：Web層（JSON返却、API用）
- `@Configuration`：設定クラス

<br>

→　次：[Repository](05_repository.md)