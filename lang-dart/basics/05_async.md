<!-- omit in toc -->
# 非同期処理

- 時間がかかる処理の完了を待たずに次の処理を実行すること
- API呼び出し、ファイル読み書き、データベース操作、画面遷移語の処理など

<!-- omit in toc -->
### 目次

- [](#)

## Future<T>

いずれT型の値が返ってくる

```dart
// Future<String> = 「いずれStringが返ってくる」
Future<String> getName() {
  return Future.delayed(
    Duration(seconds: 2),  // 2秒待つ
    () => "田中太郎",        // 2秒後にこの値を返す
  );
}
```

## async/await

- `async`：この関数は非同期処理をする
- `await`：この処理の完了を待つ

```dart
// 非同期関数の定義
Future<String> getUserData() async {
  // await = 「この処理の完了を待つ」
  String name = await getName();           // 2秒待つ
  String email = await getEmail();         // さらに1秒待つ
  return "$name ($email)";                 // 合計3秒後に返す
}

// 使用例
void main() async {
  print("開始");
  String result = await getUserData();     // 完了まで待つ
  print(result);                          // "田中太郎 (tanaka@example.com)"
  print("完了");
}
```