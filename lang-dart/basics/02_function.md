<!-- omit in toc -->
# 関数

<!-- omit in toc -->
### 目次

- [名前付き引数](#名前付き引数)
- [無名関数](#無名関数)

## 名前付き引数

```dart
myFunc({String name});
```

- 関数を呼び出す時、名前を指定して引数に値を入れることができる
- 引数の順番に影響されない

#### 呼び出し先

```dart
myFunc(name: "John");
```

#### 必ず引数の最後に置く

```dart
myFunc(String first, String last, {String middle});
```

#### デフォルト値指定

```dart
myFunc({String name = "John"});
```

#### null許容

```dart
myFunc({String? name});
```

#### required

絶対に必要な引数（指定しないとコンパイルエラー）

```dart
myFunc({required name});
```

## 無名関数

```dart
var add = (int a, int b) => a + b;
```