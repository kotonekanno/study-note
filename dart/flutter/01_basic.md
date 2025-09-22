<!-- omit in toc -->
# Flutterアプリの基礎

### 目次

- [基礎](#基礎)
- [Key](#key)

## 基礎

- 必ず`main()`関数から始まり、`runApp()`に`Widget`を渡すことで画面を作る

#### 基本形

```dart
import 'package:flutter/material.dart';

void main() {
  runApp(const MyApp()); // アプリのスタート地点
}

class MyApp extends StatelessWidget {
  const MyApp({super.key}); // StatelessWidget = 状態を持たない画面

  @override
  Widget build(BuildContext context) {
    return const MaterialApp( // Flutter標準のアプリ構造
      home: Center(
        child: Text("Hello Flutter!"),
      ),
    );
  }
}
```

- `StatelessWidget`：状態を持たないWidget（固定UI）
- `const MyApp`：コンストラクタ
  - `const`がない場合は実行のたびに新しいインスタンスを作るが、ある場合は同じ内容ならば前に作ったものをそのまま使う
  - `MyApp`は`StatelessWidget`なので、インスタンスを毎回作らず定義として再利用するようにコンパイラに伝える
- `{super.key}`：親クラス（`StatelessWidget`）のコンストラクタに`key`をそのまま渡す
- `MyApp({Key? key}) : super(key: key);`の省略記法
- `@override`：
  - Dartのアノテーション
  - 親クラスのメソッドを上書き
  - 必須ではないが、つけることが推奨される
- `Widget build(BuildContext context)`：
  - Flutterが必ず呼ぶメソッド
  - この中に画面レイアウトを全て書く
  - 引数`context`：Widgetツリー上の位置やテーマにアクセスするための情報
  - 返り値：画面のルートWidgetを返す
- `home`, `child`：名前付き引数

## Key

- 画面が再描画される時、Flutterが前のWidgetと同じかどうかを比較するための識別子
- KeyなしだとWidgetをツリー上の位置から判断し、バグることがある

```dart
ListView(
  children: const [
    Text("A", key: ValueKey("A")),
    Text("B", key: ValueKey("B")),
    Text("C", key: ValueKey("C")),
  ],
)
```

- 種類
  - `ValueKey(value)`：値で識別（文字列や数字を渡すことが多い）
  - `UniqueKey()`：その場で絶対ユニークなキーを作る
  - `ObjectKey(object)`：オブジェクトそのもので識別
- 自作のWidgetクラスには`const MyWidget({super.key})`を入れておく