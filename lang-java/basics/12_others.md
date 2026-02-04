<!-- omit in toc -->
# その他言語仕様

<!-- omit in toc -->
### 目次

- [`enum`（列挙型）](#enum列挙型)
- [`record`](#record)

## `enum`（列挙型）

- 定数表現
- 取りうる値を有限集合として型で表現する仕組み
- クラスの一種
- インスタンス数が固定

```java
enum Day {
  MON, TUE, WED
}
```

<!-- omit in toc -->
### メソッド

- `values()`：定義されている前提数を、定義順で返す（配列）
- `valueOf(String)`：指定した定数名と一致する定数を返す
  - 一致しない場合、例外
- `name()`：その`enum`定数がソースコード上で定義されている名前（`String`）を返す
- `ordinal()`：その`enum`定数が定義された順番を返す
  - 最初は0
  - 並び変更に弱いため非推奨

<!-- omit in toc -->
### フィールド/メソッドを持つ`enum`

```java
enum Status {
  OK(200), NG(500);

  private final int code;

  Status(int code) {
    this.code = code;
  }

  int getCode() {
    return code;
  }
}
```


## `record`

```java
record Point(int x, int y) {}
```

- 不変データを簡潔に表現するための構文糖
- 自動生成される要素
  - フィールド（`private`/`final`）
  - コンストラクタ
  - getter
  - `equals` / `hashCode`
  - `toString`
- 制約
  - 継承不可
  - フィールドは不変
- 用途：DTO・値オブジェクト
