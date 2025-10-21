<!-- omit in toc -->
# 例外処理

基本構文：`try-catch-finally`

<!-- omit in toc -->
### 目次

- [基本形](#基本形)
- [スタックトレース](#スタックトレース)

### 基本形

```dart
try {
  // エラーが起きる可能性のある処理
  var result = await riskyOperation();
  print(result);
} catch (e) {
  // エラーが起きた時の処理
  print('エラー: $e');
} finally {
  // 成功・失敗に関わらず必ず実行される処理
  print('処理完了');
}
```

### スタックトレース

エラーが発生した際に、その時点までに呼び出された関数・メソッドの実行履歴を時系列で一覧表示するもの

```dart
try {
  await riskyOperation();
} catch (e, stackTrace) {
  print('エラー: $e');
  print('スタックトレース: $stackTrace');
}
```

## 例外タイプ

- `SocketException`：ネットワーク接続エラー
- `HttpException`：HTTPエラー
- `TimeoutException`：タイムアウト
- `FileSystemException`：ファイル関連エラー
- `FormatException`：JSON解析関連／型変換関連エラー

## カスタム例外

```dart
// カスタム例外クラス
class UserNotFoundException implements Exception {
  final String message;
  UserNotFoundException(this.message);
  
  @override
  String toString() => 'UserNotFoundException: $message';
}

class ValidationException implements Exception {
  final List<String> errors;
  ValidationException(this.errors);
  
  @override
  String toString() => 'ValidationException: ${errors.join(', ')}';
}

// 使用例
Future<User> getUser(int id) async {
  if (id <= 0) {
    throw ValidationException(['IDは1以上である必要があります']);
  }
  
  var userData = await fetchUserData(id);
  if (userData == null) {
    throw UserNotFoundException('ID:$id のユーザーが見つかりません');
  }
  
  return User.fromJson(userData);
}

// エラーハンドリング
try {
  var user = await getUser(-1);
} on ValidationException catch (e) {
  showValidationErrors(e.errors);
} on UserNotFoundException catch (e) {
  showUserNotFoundMessage(e.message);
} catch (e) {
  showGenericError('予期しないエラーが発生しました');
}
```