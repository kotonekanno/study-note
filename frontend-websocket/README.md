# WebSocket

### 目次

## WebSocketとは

- 双方向通信を維持するためのプロトコル
- クライアントとサーバーが一度接続（ハンドシェイク）をすると、接続を維持したまま双方向で自由にデータの送受信が可能
- 株価情報、ゲームの状態同期などに向いている

## ハンドシェイク

- WebSocket接続は、最初にHTTPで「アップグレード要求」を送るところから始まる
- クライアントがサーバーに`GET`リクエストを送る：
  ```
  GET /socket HTTP/1.1
  Host: localhost:9000
  Upgrade: websocket
  Connection: Upgrade
  Sec-WebSocket-Key: xxxxxxxxx
  Sec-WebSocket-Version: 13
  ```
- サーバーが承認して`101 Switching Protocols`を返す：
  ```
  HTTP/1.1 101 Switching Protocols
  Upgrade: websocket
  Connection: Upgrade
  Sec-WebSocket-Accept: yyyyyyyyy
  ```
- この時点でHTTPからWebSocketに切り替えられ、以降は双方向のバイナリ／テキストフレームで通信

## フレーム形式

WebSocketで送られるメッセージは、フレーム単位で構成されている

- FIN：最終フレームかどうか
- Opcode：データ種類（テキスト、バイナリ、制御フレーム）
- Mask：クライアントから送信時は必ずマスクされる
- Payload Length：データ長
- Payload Data：実際のメッセージ

<br>

- テキストフレーム：文字列やJSON
- バイナリフレーム：ファイルやバイナリデータ
- 制御フレーム：Ping/Pong、接続終了など

<br>

アプリ側は基本的にフレームを意識せず、文字列やJSONとして扱う

## クライアントとサーバーの流れ

```rust
Client                     Server
-------                    ------
send("Hello") -> frame -> receive frame
                             decode -> "Hello"
                             process -> "Echo: Hello"
<- frame <- send("Echo: Hello")
decode -> "Echo: Hello"
```

- フレーム化（エンコード／デコード）が必ず行われる
- クライアント→サーバーはマスク付き、サーバー→クライアントはマスクなし
- 常に接続を維持しているので、任意タイミングで送信できる

## メッセージ構造

単純テキストで良いが、JSONを使うことが多い

```json
{
  "type": "chat",
  "user": "Alice",
  "message": "Hello!"
}
```

- type：処理を分岐させる
- user：誰からのメッセージか
- message：実際の内容