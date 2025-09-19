# Provider

#### 目次

## `ChangeNotifier`

- リスナーに状態の変化を通知する状態管理用クラス
- `ViewModel`や状態保持クラスで継承する

#### 基本構文

```dart
class AuctionViewModel extends ChangeNotifier {
  // 状態（プロパティ）
  int _count = 0;
  int get count => _count;

  // 状態を変更するメソッド
  void increment() {
    _count++;
    notifyListeners(); // ここでリスナーに通知
  }
}
```

#### メソッド

- `notifyListeners()`：
  - 登録されているリスナーに状態が変わったことを通知
  - `listen`中のWidgetが再ビルドされる
- `addListener(VoidCallback listeners)`：外部からカスタムリスナーを登録
- `removeListener(VoidCallback listeners)`：登録したリスナーを解除
- `dispose()`：クリーンアップ処理（`ChangeNotifierProvider`が自動で呼ぶことが多い）

## Provider系クラス

#### `Provider<T>`

- 下位Widgetにオブジェクトを提供する
- 上位にオブジェクトを置いて、下位のWidgetから`Provider.of<T>(context)`で取り出せるようにする箱
- 定数やサービスクラスを提供するだけで、通知は不要な場合に使う

```dart
Provider<T>(
  create: (context) => Tのインスタンス,
  child: Widget,
)
```

#### `ChangeNotifierProvider<T extends ChangeNotifier>`

- `ChangeNotifier`を継承したクラスを提供し、変更通知に対応
- オブジェクトを流し、そのオブジェクトの状態が変化したら通知して、画面を再ビルドする
- `ViewModel`を使った状態管理のための`Provider`

```dart
ChangeNotifierProvider<T>(
  create: (context) => Tのインスタンス,
  child: Widget,
)
```

#### `MultiProvider`

- `Provider`を複数まとめて登録

```dart
MultiProvider(
  providers: [
    ChangeNotifierProvider(create: (_) => ViewModelA()),
    Provider(create: (_) => ServiceB()),
  ],
  child: Widget,
)
```

## データの取得

#### `Provider.of<T>(context, {listen = true})`

- 登録された`T`を取得する
- 戻り値：`T`型のインスタンス

```dart
Provider.of<T>(context, listen: true/false)
```

- `listen`
  - `true`：値が変わるとこのWidgetも再ビルドされる
  - `false`：単発で値を参照するのみ

#### `context.read<T>()`

- `listen`しないで値を取得する
- 戻り値：`T`型のインスタンス
- `Provider.of<T>(context, listen: false)`の糖衣構文

#### `context.watch<T>`

- `listen`する値を取得する
- 戻り値：`T`型のインスタンス
- `Provider.of<T>(context, listen: true)`の糖衣構文
- `T`全体を監視するため、`T`内のどのフィールドが変わっても再ビルドされる

#### `context.select<T, R>(R selector(T value))`

- 特定のフィールドだけ監視する
- 戻り値：`R`型（特定の値）

```dart
context.select<T, R>(
	(value) => value.someField
)
```

- `T`の中から特定の値`R`（`someField`）だけを取り出して監視する
  - `T`：`Provider`で流している型
  - `R`：取り出したいフィールドや計算結果の型（戻り値の型）
- `someField`が変化した時だけ再ビルドされる

## Widgetでの監視（画面更新）

#### `Selector<T, R>`

- `Consumer`と`select`の組み合わせ
- 特定のWidgetに特定のフィールドを`listen`させる

```dart
Selector<T, R>(
  selector: (context, value) => value.someField,
  builder: (context, field, child) {
    return Widget;
  },
)
```

#### `Consumer<T>`

- 特定のWidgetだけを`listen`させる
- Widget全体ではなく一部だけ再ビルド可能

```dart
Consumer<T>(
  builder: (context, value, child) {
    return Widget;
  },
)
```

## サンプルコード

```dart
import 'package:flutter/material.dart';
import 'package:provider/provider.dart';

void main() {
  runApp(
    ChangeNotifierProvider(
      create: (_) => MyModel(),
      child: MyApp(),
    ),
  );
}

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
        body: Center(
          child: Consumer<MyModel>(
            builder: (context, model, child) {
              return Text('Count: ${model.count}');
            },
          ),
        ),
        floatingActionButton: FloatingActionButton(
          onPressed: () => context.read<MyModel>().increment(),
          child: Icon(Icons.add),
        ),
      ),
    );
  }
}
```

- `ChangeNotifierProvider`で`MyModel`を提供
- `Consumer<MyModel>`で`notifyListeners()`に反応してUI更新
- `context.read<Mymodel>`で状態を操作

## 流れまとめ


1. `Model`（状態を持つクラス）作成
  ```dart
  import 'package:flutter/material.dart';

  class Counter extends ChangeNotifier {
    int _count = 0;

    int get count => _count;

    void increment() {
      _count++;
      notifyListeners(); // UIに変更を通知
    }
  }
  ```
2. `Provider`で包む
  ```dart
  import 'package:provider/provider.dart';

  void main() {
    runApp(
      ChangeNotifierProvider(
        create: (_) => Counter(),
        child: const MyApp(),
      ),
    );
  }
  ```
3. UIで使う
  ```dart
  class CounterPage extends StatelessWidget {
    const CounterPage({super.key});

    @override
    Widget build(BuildContext context) {
      final counter = context.watch<Counter>(); // データの購読

      return Scaffold(
        body: Center(
          child: Text('Count: ${counter.count}'),
        ),
        floatingActionButton: FloatingActionButton(
          onPressed: () => counter.increment(),
          child: const Icon(Icons.add),
        ),
      );
    }
  }
  ```