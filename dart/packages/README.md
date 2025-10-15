<!-- omit in toc -->
# ライブラリ

### 目次

- [`go_router`](#go_router)
- [`web_socket_channel`](#web_socket_channel)
- [`provider`](#provider)
- [`http`](#http)
- [`mysql1`](#mysql1)
- [`hive`](#hive)
- [`url_launcher`](#url_launcher)
- [`url_launcher_web`](#url_launcher_web)
- [`dio`](#dio)
- [`path_provider`](#path_provider)

## `go_router`

- 画面遷移（ルーティング）を管理
- URLベースでルーティングできる（Flutter Web対応）
- ルートごとに画面、パラメータ、認証チェックなどをまとめて定義できる

#### 基本構文

```dart
import 'package:flutter/material.dart';
import 'package:go_router/go_router.dart';

void main() {
  final router = GoRouter(
    routes: [
      GoRoute(
        path: '/',
        builder: (context, state) => const HomePage(),
      ),
      GoRoute(
        path: '/detail/:id',
        builder: (context, state) {
          final id = state.params['id']!;
          return DetailPage(id: id);
        },
      ),
    ],
  );

  runApp(MyApp(router: router));
}

class MyApp extends StatelessWidget {
  final GoRouter router;
  const MyApp({super.key, required this.router});

  @override
  Widget build(BuildContext context) {
    return MaterialApp.router(
      routerConfig: router,
    );
  }
}
```

- `GoRouter`：ルート定義
- `GoRoute`：パスと個別の画面（`builder`）を設定
- `state.params`：URLパラメータの取得
- `MaterialApp.router`：アプリ側で使う

#### 画面遷移操作

- `go()`：プログラムから指定パスに遷移
  ```dart
  GoRouter.of(context).go('/detail/42');
  ```
- `push()`
- `pop()`：画面戻る
  ```dart
  context.pop(); // Navigator.pop() と同じ
  ```

#### 参照

- [Navigator](02_widgets.md#navigator)

## `web_socket_channel`

- クライアントとサーバーが双方向でリアルタイムに通信できる
- HTTPと異なり、常に接続を維持してデータの送受信ができる

#### 基本構文

```dart
import 'package:web_socket_channel/web_socket_channel.dart';

void main() {
  final channel = WebSocketChannel.connect(
    Uri.parse('wss://echo.websocket.org'), // WebSocketサーバーのURL
  );

  // サーバーからのメッセージを受け取る
  channel.stream.listen((message) {
    print('受信: $message');
  });

  // サーバーにメッセージを送る
  channel.sink.add('Hello WebSocket');

  // 通信終了
  channel.sink.close();
}
```

- `WebSocketChannel.connect`：接続を作る
- `channel.stream.listen`：受信を監視
- `channel.sink.add`：送信
- `channel.sink.close`：接続を閉じる

<br>

- 接続先URL
  - `wss://`：暗号化
  - `ws:/`：非暗号化
- 非同期処理（`stream.listen`）：データが来たら順次処理される

## `provider`

- Flutterで状態管理を簡単にするためのパッケージ
- データの変化をUIに自動で反映させる仕組み

<br>

- [Provider](provider.md)

## `http`

#### HTTPとは

- クライアント（Flutterアプリ）からサーバー（API）にリクエストを送り、サーバーが結果をレスポンスする
- HTTPメソッド
  - `GET`：データを取得
  - `POST`：データを新しく作る
  - `PUT`：データを更新する
  - `DELETE`：データを削除する
- ステータスコード
  - `200`：成功
  - `400`：リクエストが間違っている
  - `401`：認証が必要
  - `404`：存在しないページ
  - `500`：サーバー側のエラー

#### Dartの非同期処理

- Dartは非同期（`Future`ベースで動く）
- `Future`と`async`/`await`を使ってレスポンスを待つ

```dart
import 'package:http/http.dart' as http;

void main() async {
  final url = Uri.parse('https://jsonplaceholder.typicode.com/todos/1');

  // 非同期通信
  final response = await http.get(url);

  print(response.statusCode); // 200
  print(response.body);       // レスポンスの内容
}
```

- `async`
- `await`：レスポンスが返ってくるまで待つ
- `Future`：あとで値が返ってくる

#### GET通信

```dart
final url = Uri.parse('https://jsonplaceholder.typicode.com/todos/1');
final response = await http.get(url);

if (response.statusCode == 200) {
  print('成功！レスポンス: ${response.body}');
} else {
  print('エラー: ${response.statusCode}');
}
```

- `Uri.parse`：URLを作る
- `http.get`：リクエスト
- `body`と`statuscode`を確認

<br>

- 成功ならJSON文字列が返ってくる
- エラーならステータスコードを見て原因を判断

#### POST通信

- サーバーにデータを送る

```dart
import 'dart:convert'; // JSON変換用

final url = Uri.parse('https://jsonplaceholder.typicode.com/posts');

final response = await http.post(
  url,
  headers: {'Content-Type': 'application/json'},
  body: jsonEncode({'title': 'Hello', 'body': 'World'}),
);

print(response.statusCode);
print(response.body);
```

- `headers`：
  - データの形式をサーバーに伝える
  - JSONの場合：`Content-type: application/json`
- `body`：送るデータを書き込む（文字列やJSON）

#### レスポンス処理（JSONの扱い）

- JSON文字列をDartで使える形に変換
- `Map`、`List`としてアクセスできる

## `mysql1`

- SQLを直接書いてクエリを実行できる
- 非同期処理に対応している

#### 基本構文

```dart
import 'package:mysql1/mysql1.dart';

void main() async {
  // 接続設定
  final settings = ConnectionSettings(
    host: 'localhost',
    port: 3306,
    user: 'user',
    password: 'password',
    db: 'test_db',
  );

  // 接続
  final conn = await MySqlConnection.connect(settings);

  // クエリ実行
  var results = await conn.query('SELECT id, name FROM users WHERE id = ?', [1]);
  for (var row in results) {
    print('ID: ${row[0]}, Name: ${row[1]}');
  }

  // 接続を閉じる
  await conn.close();
}
```
- 接続設定：`ConnectionSettings`（ホスト、ユーザー、パスワード、DBを指定）
- 接続：`MysqlConnection.connect(settings)`
- クエリ実行
  - `conn.query(...)`：SQLクエリを実行
  - 結果は`Results`オブジェクトで返る
  - 非同期なので、`await`で待つ必要がある
- 接続終了：`conn.close()`

#### その他

- `?`プレースホルダー：配列で値を渡す
- パラメータのバインド

## `hive`

- 軽量で高速なNoSQLデータベース
- [`Hive`](hive.md)

## `url_launcher`

- 端末の外部アプリやブラウザを開く
- 電話、メール、ブラウザ、マップなどを起動できる

#### 基本構文

```dart
import 'package:url_launcher/url_launcher.dart';

final Uri _url = Uri.parse("https://flutter.dev");

Future<void> openFlutterSite() async {
  if (await canLaunchUrl(_url)) {
    await launchUrl(_url);
  } else {
    throw '開けません: $_url';
  }
}
```

- `Uri.parse(https://example.com)`：URLを指定
- `launchUrl(url)`：指定されたURLを開く
- `canLaunchUrl`：失敗時の処理を書くことができる

#### `LaunchMode`

- `LaunchMode.platformDefault`：OSが標準で決めた方法で開く（デフォルト）
- `LaunchMode.externalApplication`：端末の外部ブラウザやアプリで開く
- `LaunchMode.inAppWebView`：
  - アプリ内WebViewで開く（Android/iOSでサポートされる場合）
  - Androidは`WebView`、iOSは`SFSafariViewController`が内部で使われる
- `LaunchMode.externalNonBrowserApplication`：ブラウザ以外のアプリ（電話、メールなど）で開く場合に使う

```dart
await launchUrl(
  _url,
  mode: LaunchMode.inAppWebView, // アプリ内で表示
);

```

## `url_launcher_web`

- `url_launcher`のWeb用の実装パッケージ
- 直接使うことはほぼなく、`url_launcher`を`import`すると自動的に内部で利用される

## `dio`

- `http`の高機能版
- [Dio](dio.md)

## `path_provider`

- デバイスのファイルパスを取得する
- どのディレクトリにファイルを保存すればいいか教えてくれる
- プラットフォームごとに異なるファイル保存場所（ドキュメントディレクトリや一時ディレクトリなど）を簡単に取得できる
- ファイルの読み書きやデータ保存の前に必須

#### 基本構文

```dart
import 'package:path_provider/path_provider.dart';
import 'dart:io';

void main() async {
  // ドキュメントディレクトリの取得
  final directory = await getApplicationDocumentsDirectory();
  print('Documents directory: ${directory.path}');

  // 一時ディレクトリの取得
  final tempDir = await getTemporaryDirectory();
  print('Temporary directory: ${tempDir.path}');

  // ファイル作成例
  final file = File('${directory.path}/example.txt');
  await file.writeAsString('Hello, Path Provider!');
  print(await file.readAsString());
}
```

- `getApplicationDocumentDirectory()`：永続的に保存できるディレクトリの取得
- `getTemporaryDirectory()`：一時的に保存するディレクトリの取得
- ファイルパスを取得したら、`dart:io`の`File`で読み書き

<br>

- ディレクトリの種類：ドキュメント／一時／キャッシュ
- ファイル操作の目的：ローカルDB、キャッシュ、設定ファイル、ログなど
- ディレクトリ取得やファイル操作は非同期で行う