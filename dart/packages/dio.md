<!-- omit in toc -->
# dio

- `http`パッケージの高機能版
- リクエスの設定やレスポンスの受け取りを柔軟にできる
- タイムアウト、エラー処理、リクエストの共通ヘッダー設定などが用意
- Cookie管理、インターセプター（リクエスト・レスポンスの前後に処理を挟む）に対応

<!-- omit in toc -->
### 目次

- [基本構文](#基本構文)
- [リクエスト設定](#リクエスト設定)
- [タイムアウト／エラー処理](#タイムアウトエラー処理)
- [Cookie/共通ヘッダー／インターセプター](#cookie共通ヘッダーインターセプター)

## 基本構文

```dart
import 'package:dio/dio.dart';

void main() async {
  final dio = Dio(); // Dioインスタンスを作成

  try {
    final response = await dio.get('https://jsonplaceholder.typicode.com/todos/1');
    print(response.statusCode); // 200
    print(response.data);       // JSONがMap/Arrayとして返る
  } catch (e) {
    print('エラー: $e');
  }
}
```

- `dio.get`/`dio.post`：`http`と同様
- `responce.data`：JSONを自動で`Map`/`Array`に変換
- `try`/`catch`でエラーを拾う

## リクエスト設定

- ヘッダー設定（`Authorization`、`Content-Type`など）
  ```dart
  final response = await dio.get(
    'https://example.com/api',
    options: Options(
      headers: {'Authorization': 'Bearer token123'}
    ),
  );
  ```
- POSTでJSON送信
  ```dart
  dio.options.connectTimeout = 5000; // 接続タイムアウト5秒
  dio.options.receiveTimeout = 3000; // 受信タイムアウト3秒

  try {
    final response = await dio.get('https://example.com/api');
  } on DioError catch (e) {
    if (e.type == DioErrorType.connectTimeout) {
      print('接続タイムアウト');
    } else if (e.type == DioErrorType.receiveTimeout) {
      print('受信タイムアウト');
    } else {
      print('その他エラー: ${e.message}');
    }
  }
  ```

## タイムアウト／エラー処理

```dart
dio.options.connectTimeout = 5000; // 接続タイムアウト5秒
dio.options.receiveTimeout = 3000; // 受信タイムアウト3秒

try {
  final response = await dio.get('https://example.com/api');
} on DioError catch (e) {
  if (e.type == DioErrorType.connectTimeout) {
    print('接続タイムアウト');
  } else if (e.type == DioErrorType.receiveTimeout) {
    print('受信タイムアウト');
  } else {
    print('その他エラー: ${e.message}');
  }
}
```

- `DioErrorType`：エラーの種類を判定
- `http`では単に例外で止まるが、`dio`では細かく種類を分けられる

## Cookie/共通ヘッダー／インターセプター

- Cookie管理や共通ヘッダーをまとめて設定可能
- `Interceptor`でリクエスト前後に自動処理を挟める

```dart
dio.interceptors.add(InterceptorsWrapper(
  onRequest: (options, handler) {
    print('リクエスト前: ${options.uri}');
    return handler.next(options);
  },
  onResponse: (response, handler) {
    print('レスポンス受信: ${response.statusCode}');
    return handler.next(response);
  },
));
```
