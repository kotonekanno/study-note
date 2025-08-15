# 9. 非同期処理

### 目次

- [Future](#future)
- [Futureの使い方](#futureの使い方)

<br>

## Future

- 将来のある時点で値を返す約束（非同期計算の結果）
- ブロックの処理を待たずに次の処理へ進める
- 完了後にコールバックやマップで処理を続けられる

<br>

## Futureの使い方

```scala
import scala.concurrent._
import ExecutionContext.Implicits.global
import scala.util.{Success, Failure}

val f: Future[Int] = Future {
  // 重い計算やI/O処理を非同期に実行
  Thread.sleep(1000)
  42
}

f.onComplete {
  case Success(value) => println(s"Got the result: $value")
  case Failure(e) => println(s"Failed with $e")
}
```

- `Future { ... }`ブロック内の処理は別スレッドで非同期実行
- `onComplete`で成功・失敗をハンドル

<br>

- `import ExecutionContext.Implicits.global`でスレッドプールの設定が必要
- `Await.result`で同期的に結果を待てるが、多様は避ける
参照：[サンプルコード](00_sample_codes.md#9-非同期処理)