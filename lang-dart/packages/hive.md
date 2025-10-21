<!-- omit in toc -->
# Hive

### 目次

## Box

- データを保存する最小単位
- テーブルやキー／バリューの倉庫

<br>

- Key-Valueストア
  ```dart
  var box = await Hive.openBox('myBox');
  box.put('name', 'Alice');
  print(box.get('name')); // Alice
  ```

- 型指定も可能
  ```dart
  var box = await Hive.openBox<int>('numbers');
  box.add(42);
  ```

- アプリを閉じてもデータは端末に保存される
- DBの複数テーブルのように、複数のBoxを持てる

## model

```dart
import 'package:hive/hive.dart';

part 'word.g.dart';

@HiveType(typeId: 0)
class Word extends HiveObject {
  @HiveField(0)
  String mainKey;

  @HiveField(1)
  String subKey;

  Word({required this.mainKey, required this.subKey});
}
```

- `var box = await Hive.openBox<Word>('words');`
  - HiveにWord型専用のBoxを'words'という名前で開く（存在しなければ作る）
  - これを通してデータの読み書きができるようになる
  - 返り値は`Box<Word>`型
- `part 'word.g.dart';`
  - Hiveの`TypeAdapter`を自動生成するために必要
  - シリアライズ／デシリアライズ（データの保存／取得）を自動で行う
- `@HiveType(typeId: 0)`
  - このクラスをHiveである買う方として登録するためのアノテーション
  - `typeId`：Hive内でクラスを識別する一位の番号
- `HiveObject`
  - 継承クラスをHiveの保存可能オブジェクトとして定義
  - メソッド：`save()`/`delete()`/`refresh()`など
- `@HiveField(0)`
  - クラスのフィールドをHiveに保存可能にするためのアノテーション
  - `(n)`：
    - フィールドのIDで、0から始まる必要がある
    - 途中で番号を変えると、過去のフィールドが読み込めなくなってしまうため注意
- フィールド定義
  ```dart
  String mainKey;
  String subKey;
  ```
- コンストラクタ
  ```dart
  Word({required this.mainKey, required this.subKey});
  ```