<!-- omit in toc -->
# Repository

<!-- omit in toc -->
### 目次

- [役割](#役割)
- [基本構文](#基本構文)
  - [Entityクラス](#entityクラス)
  - [Repositoryクラス（JPAインターフェース）](#repositoryクラスjpaインターフェース)
- [Spring Data JPA](#spring-data-jpa-1)
- [よく使うビルドインメソッド](#よく使うビルドインメソッド)
- [カスタムクエリ](#カスタムクエリ)
  - [使用例](#使用例)
- [データベース設定（H2）](#データベース設定h2)
- [データベース接続（本格DB）](#データベース接続本格db)
  - [設定ファイルの形式](#設定ファイルの形式)
  - [設定項目](#設定項目)
  - [MySQLドライバの追加](#mysqlドライバの追加)

## 役割

- データベースへのアクセス
- Springによる例外変換（SQL例外をSpring例外に変換）
- Spring Data JPAによる自動SQL生成

<!-- omit in toc -->
#### Spring Data JPA

- データベース操作を簡単に行うために用意されている
- SQLを書かずにDB操作が可能

<!-- omit in toc -->
#### 処理の流れ

```
@Entity → @Repository → @Service → @RestController
```

## 基本構文

### Entityクラス

DBテーブルと対応

```java
package com.example.demo.entity;

import jakarta.persistence.Entity;
import jakarta.persistence.GeneratedValue;
import jakarta.persistence.GenerationType;
import jakarta.persistence.Id;

@Entity
public class User {

  @Id
  @GeneratedValue(strategy = GenerationType.IDENTITY)
  private Long id;

  private String name;

  private String email;

  // getter / setter
  public Long getId() { return id; }
  public void setId(Long id) { this.id = id; }

  public String getName() { return name; }
  public void setName(String name) { this.name = name; }

  public String getEmail() { return email; }
  public void setEmail(String email) { this.email = email; }
}
```

- `@Entity`：このクラスがDBテーブルに対応することを示す
- `@Id`：主キー
- `@GenerateValue`：主キーの自動採番

### Repositoryクラス（JPAインターフェース）

```java
package com.example.demo.repository;

import org.springframework.data.jpa.repository.JpaRepository;
import com.example.demo.entity.User;

public interface UserRepository extends JpaRepository<User, Long> {
  // これだけでCRUDメソッドが自動生成される
}
```

- `JpaRepository<T, Id>`：
  - 第1引数：Entityクラス
  - 第2引数：主キーの型
- これでCRUDメソッドが自動的に使えるようになる

## Spring Data JPA

## よく使うビルドインメソッド

- `save(entity)`：新規登録・更新
- `findAll()`：全件取得
- `findById(id)`：主キー検索
- `deleteById(id)`：削除
- `cuont()`：件数取得

## カスタムクエリ

Spring Data JPAはメソッド名でSQLを自動生成する

- `findByName(String name)`：`name`列が一致
  ```sql
  SELECT * FROM users WHERE name=?
  ```
- `findByAgeGreaterThan(int age)`：`age`列が指定より大きい
  ```sql
  SELECT * FROM users WHERE age>?
  ```
- `existByName(String name)`：存在チェック
  ```sql
  SELECT COUNT(*) > 0
  ```

### 使用例

<!-- omit in toc -->
#### Service層

```java
package com.example.demo.service;

import org.springframework.stereotype.Service;
import com.example.demo.repository.UserRepository;
import com.example.demo.entity.User;
import java.util.List;

@Service
public class UserService {

  private final UserRepository userRepository;

  public UserService(UserRepository userRepository) {
    this.userRepository = userRepository;
  }

  public List<User> getAllUsers() {
    return userRepository.findAll();
  }

  public void addUser(User user) {
    userRepository.save(user);
  }
}
```

<!-- omit in toc -->
#### Controller層

```java
package com.example.demo.controller;

import org.springframework.stereotype.Controller;
import org.springframework.ui.Model;
import org.springframework.web.bind.annotation.GetMapping;
import com.example.demo.service.UserService;

@Controller
public class UserController {

  private final UserService userService;
  public UserController(UserService userService) {
    this.userService = userService;
  }

  @GetMapping("/users")
  public String listUsers(Model model) {
    model.addAttribute("users", userService.getAllUsers());
    return "users"; // → templates/users.html
  }
}
```

## データベース設定（H2）

- **H2**：Javaで開発された軽量なRDBMS

`application.properties`：

```
spring.datasource.url=jdbc:h2:mem:testdb
spring.datasource.driver-class-name=org.h2.Driver
spring.datasource.username=sa
spring.datasource.password=
spring.jpa.hibernate.ddl-auto=update
spring.h2.console.enabled=true
```

- `spring.jpa.hibernate.dd1-auto=update`：Entity定義に合わせて自動でテーブルを作成する
- `spring.h2.console.enabled=true`：ブラウザでDBを確認可能（http://localhost:8080/h2-console）

<!-- omit in toc -->
#### H2データベース接続情報

- JDBC URL：`jdbc:h2:mem:testdb`
- User Name：`sa`
- Password：（空）

## データベース接続（本格DB）

### 設定ファイルの形式

- `application.properties`
- `application.yml`：より構造的で見やすいため、主流

### 設定項目

`application.yml`：

```yml
spring:
  datasource:
    driver-class-name: com.mysql.cj.jdbc.Driver
    url: jdbc:mysql://localhost:3306/demo_db?useSSL=false&allowPublicKeyRetrieval=true&serverTimezone=Asia/Tokyo
    username: root
    password: your_password

  jpa:
    hibernate:
      ddl-auto: update     # create / create-drop / update / validate / none
    show-sql: true          # 実行SQLをログ出力
    properties:
      hibernate:
        format_sql: true

  thymeleaf:
    cache: false            # テンプレートキャッシュ無効（開発時用）
```

- `spring.datasource.url`：接続先DBのURL
  - JDBC方式：`jdbc:mysql://…`
- `spring.datasource.username`：DBユーザー名
- `spring.datasource.password`：DBパスワード
- `spring.jpa.hibernate.ddl-auto`：スキーマ操作モード
  - `create`：アプリ起動毎にテーブルを作り直す（毎回データが消える）
  - `create-drop`
  - `update`：既存テーブルを維持しつつ差分更新（開発向け）
  - `validate`：Entity定義とDB構造の生合成をチェック
  - `none`：自動DDLを無効化（本番運用向け）
- `spring.jpa.show-sql`：SQL出力の有無（true/false）
- `spring.jpa.properties.hibernate.format_sql`：SQLを整形して出力（true）

### MySQLドライバの追加

`pom.xml`：
```xml
<dependency>
    <groupId>com.mysql</groupId>
    <artifactId>mysql-connector-j</artifactId>
</dependency>
```

<br>

→　次：[フォーム送信 / バリデーション](06_form.md)