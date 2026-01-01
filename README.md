<!-- omit in toc -->
# Study Note

Github Pagesで見る：<a herf="https://kotonekanno.github.io/study-note/" target="_blank" rel="noopener noreferrer">https://kotonekanno.github.io/study-note/</a>

### 目次

- [概要](#概要)
- [学習トピック](#学習トピック)
  - [プログラミング言語](#プログラミング言語)
  - [ツール・その他技術](#ツールその他技術)
- [ディレクトリ構成](#ディレクトリ構成)


## 概要

このリポジトリは、私が学習した知識をまとめた学習ノートです。<br>
自分の理解のために最もわかりやすい形で整理したメモを公開しています。


## 学習トピック

### プログラミング言語

- [**HTML/CSS**](frontend-basics/)：Webページの構造と見た目を作る基礎技術
- [**JavaScript関連技術**](lang-javascript/)
  - [**JavaScript**](lang-javascript/basics/)：ブラウザで動作する主要なプログラミング言語
  - [**CoffeeScript**](lang-javascript/coffeescript/)：JavaScriptを簡潔に書くための派生言語
  - [**JQuery**](lang-javascript/jquery/)：JavaScriptを便利に扱うためのライブラリ
- [**Java関連技術**](lang-java/)
  - [**Spring Boot**](lang-java/springboot/)：
- [**Scala関連技術**](lang-scala/)
  - [**Scala**](lang-scala/basics/)：JVM上で動作する静的型付けの汎用言語
  - [**Play Framework**](lang-scala/playframework/)：ScalaでWebアプリを簡単に作るためのフレームワーク
  - [**Akka**](lang-scala/akka/)：並行処理や非同期処理を簡単に扱うためのライブラリ
- [**Dart関連技術**](lang-dart/)
  - [**Dart**](lang-dart/basics/)：Googleが開発したプログラミング言語
  - [**パッケージ**](lang-dart/packages)
  - [**Flutter**](lang-dart/flutter/)：Dartを使用した、iOS・Android・Web・デスクトップ向けのアプリを作れるUIフレームワーク
- その他学習済み言語
  - Java
  - Python
  - C言語

### ツール・その他技術

- [**SQL**](lang-sql/)：データベースから情報を取得・操作するための言語
- [**GitBash**](tool-git/)：Gitをコマンドラインで操作するための言語
- [**Bash**](tool-bash/)：コマンドラインで操作するシェルスクリプト言語

## ディレクトリ構成

```
study-note
├── frontend-basics/    # HTML/CSS
├── lang-javascript/
│   └── basics/         # JavaScript
│   └── coffeescript/   # CoffeeScript
│   └── jquery/         # JQuery
├── lang-scala/
│   └── basics/         # Scala
│   └── playframework/  # PlayFramework
│   └── akka/           # Akka
├── lang-sql/                # SQL
├── lang-dart/
│   └── basics/         # Dart
│   └── packages/       # パッケージ
│   └── flutter/        # Flutter
└── README.md
```