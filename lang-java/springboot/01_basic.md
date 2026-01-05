<!-- omit in toc -->
# 基礎

<!-- omit in toc -->
### 目次

- [概要](#概要)
- [起動の仕組み](#起動の仕組み)
- [スターター](#スターター)
- [プロジェクト作成方法](#プロジェクト作成方法)
- [プロジェクト構造](#プロジェクト構造)
  - [pom.xmlの基本構成](#pomxmlの基本構成)
- [起動方法](#起動方法)
- [アプリの全体構造](#アプリの全体構造)

## 概要

- JavaのSpring Frameworkを簡単に扱えるようにしたフレームワーク
- サーバー設定や依存関係の管理を自動化し、最小構成でアプリが起動できるように作られている

<!-- omit in toc -->
#### 機能

- 自動設定
- 組み込みサーバー：Tomcatなどのサーバーを自動で内蔵し、jar実行だけで起動できる
- 依存性管理：ライブラリのバージョンを自動で管理
- スターターパッケージ：`spring-boot-starter-web`など、よく使う依存をまとめたパッケージが提供される

## 起動の仕組み

```java
@SpringBootApplication
public class Application {
  public static void main(String[] args) {
      SpringApplication.run(Application.class, args);
  }
}
```

- `@SpringBootApplication`：設定スキャン、自動設定、Bean登録をまとめて実行
- `SpringApplication.run()`：内部でTomcatを立ち上げ、Webアプリを動かす

## スターター

- Webアプリ：`spring-boot-starter-web`
- テンプレートエンジン：`spring-boot-starter-thymeleaf`
- DB接続：`spring-boot-starter-data-jpa`
- セキュリティ：`spring-boot-starter-security`
- テスト：`spring-boot-starter-test`

## プロジェクト作成方法

`Spring Initializr`という公式ジェネレーターにより、Webブラウザで生成

1. https://start.spring.io
2. 設定
   - Project: Maven Project（またはGradle）
   - Language: Java
   - Spring Boot: 安定版
   - Projet Metadata: groupId, artifactId, nameなどを設定
   - Packaging: Jar
   - Java: 17または21
   - Dependencies: 必要なものを洗濯
3. Generateボタンを押すと、zipがダウンロードされる

## プロジェクト構造

```
project-root/
├─ src/
│  ├─ main/
│  │  ├─ java/
│  │  │  └─ com.example.demo/
│  │  │      └─ DemoApplication.java  # mainクラス
│  │  ├─ resources/
│  │  │  ├─ application.properties    # 設定ファイル
│  │  │  ├─ static/                   # 静的ファイル(css, js, img)
│  │  │  └─ templates/                # Thymeleafテンプレート
│  └─ test/
│     └─ java/                        # テストコード
└─ pom.xml                            # 依存関係定義
```

### pom.xmlの基本構成

```
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0
         http://maven.apache.org/xsd/maven-4.0.0.xsd">

    <modelVersion>4.0.0</modelVersion>

    <groupId>com.example</groupId>
    <artifactId>demo</artifactId>
    <version>0.0.1-SNAPSHOT</version>
    <name>demo</name>

    <parent>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-parent</artifactId>
        <version>3.3.5</version>
    </parent>

    <dependencies>
        <!-- Webアプリ開発 -->
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-web</artifactId>
        </dependency>

        <!-- テンプレートエンジン -->
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-thymeleaf</artifactId>
        </dependency>

        <!-- テスト用 -->
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-test</artifactId>
            <scope>test</scope>
        </dependency>
    </dependencies>

    <build>
        <plugins>
            <plugin>
                <groupId>org.springframework.boot</groupId>
                <artifactId>spring-boot-maven-plugin</artifactId>
            </plugin>
        </plugins>
    </build>
</project>
```

## 起動方法

- アプリ実行
  ```bash
  mvn spring-boot:run
  ```
- Jarをビルドして起動
  ```bash
  java ^jar target/demo-0.0.1-SNAPSHOT.jar
  ```

## アプリの全体構造

Spring Bootアプリは、基本的に**三層構造**（**MVC**）で作られる

```
com.example.demo
├─ DemoApplication.java     # エントリーポイント（main）
├─ controller/              # Webリクエストを受け取る層
├─ service/                 # ビジネスロジックを扱う層
└─ repository/              # データアクセスを扱う層（DB関連）
```

```
Controller → Service → Repository → Database
```

- `Controller`：画面やAPIからのリクエストを受け取る
- `Service`：ビジネスロジック（処理の中心）を記述する
- `Repository`：データアクセス（DB操作）を担当

<br>

→　次：[Controller](02_controller.md)