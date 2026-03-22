<!-- omit in toc -->
# 例外処理

<!-- omit in toc -->
### 目次

- [概要](#概要)
- [基本構文](#基本構文)
- [例外クラス](#例外クラス)
- [検査例外／非検査例外](#検査例外非検査例外)
  - [検査例外（checked exception）](#検査例外checked-exception)
  - [非検査例外（unchecked exception）](#非検査例外unchecked-exception)
- [構文例](#構文例)
  - [基本構文](#基本構文-1)
  - [マルチcatch](#マルチcatch)
  - [finallyブロック](#finallyブロック)
  - [throws句](#throws句)
  - [throw文](#throw文)
  - [独自例外クラス](#独自例外クラス)
  - [try-with-resources](#try-with-resources)

## 概要

- Javaでは例外は、値ではなくオブジェクト
- 制御構文ではなく言語機構

## 基本構文

`try-catch-finally`

```java
try {
	// 例外が発生する可能性のある処理
} catch (例外名 変数名) {
	// 例外発生時の処理
} finally {
	// 必ず実行される処理
}
```

## 例外クラス

```
Throwable
 ├─ Error
 └─ Exception
     ├─ RuntimeException
     └─ （その他）
```

- `Throwable`：例外の最上位
- `Error`：致命的（原則捕捉しない）
- `Exception`：アプリで扱う例外
  - `RuntimeException`：実行時例外

## 検査例外／非検査例外

### 検査例外（checked exception）

- コンパイル時に処理を強制される例外
- 例：`IOException`, `SQLException`

### 非検査例外（unchecked exception）

- 実行時に発生しうるが、強制されない例外
- 例：`NullPointerException`, `IllegalArgumentException`


## 構文例

### 基本構文

```java
try {
  処理;
} catch (IOException e) {
  処理A;
} catch (Exception e) {
  処理B;
}
```

- 具体的な例外を先に書く
- 上位クラスを後に書く

### マルチcatch

```java
catch (IOException | SQLException e) {
  処理;
}
```

- 共通処理向け

### finallyブロック

- 例外の有無に関わらず必ず実行されるブロック
- 用途：リソース解放、後処理

### throws句

```java
void f() throws IOException {
	処理;
}
```

- `throws`：このメソッドは例外を投げる可能性がある、という宣言
- 用途：例外の伝播
- 処理せず、呼び出し元に責任を移譲

### throw文

```java
throw new IllegalArgumentException("message");
```

- `throw`：例外オブジェクトを明示的に発生させる

### 独自例外クラス

```java
class MyException extends Exception {
	MyException(String msg) {
		super(msg);
	}
}
```

- 業務／仕様を表現するために使う
- `RuntimeException`を継承する設計が多い

### try-with-resources

```java
try (Resource r = new Resource()) {
	処理;
}
```

- 自動で`close()`される構文
- `AutoClosable`を実装したクラスが対象
- `finally`が不要