<!-- omit in toc -->
# クラス

<!-- omit in toc -->
### 目次

- [コンストラクタ](#コンストラクタ)
  - [ゲッターの省略記法](#ゲッターの省略記法)
  - [factory](#factory)
  - [名前付きコンストラクタ](#名前付きコンストラクタ)

# コンストラクタ

## ゲッターの省略記法

名前付き引数を利用することでゲッターを省略できる

```dart
class Person {
  final String name;
  final int age;
  
  Person({
    required this.name,
    required this.age,
  });
}

// 使用
var person = Person(name: "太郎", age: 25);
print(person.name);
```

- `final String name`：フィールド宣言
  - データの保存先を用意
- `this.name`：コンストラクタ引数
  - 外部からデータを受け取ってフィールドに代入
  - 「引数受け取り+フィールドに代入」の省略系

## factory

#### 概要

- 特殊なコンストラクタ
- 通常のコンストラクタではできない柔軟なオブジェクト生成ができる
- どのようにインスタンスを作るか自由に書くことができる

<br>

- JSONをパースして初期化する処理などに便利
- 名前付きコンストラクタとして使われることが多い

#### 特徴

- 戻り値は<クラス名>型
  - 通常のコンストラクタは`return`を書かなくてもインスタンスが作れるが、`factory`では明示的に`return`する必要がある
- インスタンス生成の柔軟性
  - 既存のキャッシュを返すこともできる
  - サブクラスを返すこともできる

#### サンプルコード

```dart
class MyClass {
  final String name;
  final String age;

  MyClass({
    required this.name,
    required this.age,
  });

  factory MyClass.fromJson(Map<String, Int> json) {
    return MyClass(
      name: json['name'],
      age: json['age'],
    );
  }
}
```

## 名前付きコンストラクタ

- `ClassName.name()`とすることで、任意の名前をつけて作れるコンストラクタ
- 同じクラスでインスタンスの作り方を複数用意したい時に便利

#### サンプルコード

```dart
class Point {
  int x, y;

  Point(this.x, this.y);        // 通常のコンストラクタ
  Point.origin() : x = 0, y = 0; // 名前付きコンストラクタ
}

void main() {
  var p1 = Point(3, 5);   // 通常コンストラクタ
  var p2 = Point.origin(); // 名前付きコンストラクタ
}
```

```dart
class User {
  String name;
  int age;

  User(this.name, this.age);           // 普通のコンストラクタ
  User.anonymous() : name = '匿名', age = 0; // 名前付きコンストラクタ
}
```