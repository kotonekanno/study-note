<!-- omit in toc -->
# 制御構文

<!-- omit in toc -->
### 目次

- [条件分岐](#条件分岐)
  - [if式](#if式)
  - [switch文](#switch文)
- [繰り返し](#繰り返し)
  - [while文](#while文)
  - [do-while文](#do-while文)
  - [for文](#for文)
  - [拡張for文](#拡張for文)
  - [処理の中断](#処理の中断)

## 条件分岐

### if式

`boolean`型を返す式

```java
if (条件1) {
	処理;
} else if (条件2) {
  処理;
} else {
  処理;
}
```

### switch文

値の一致による分岐を明示的に整理する構文

```java
switch (値) {
  case 定数1:
    処理;
    break;
  case 定数2:
    処理;
    break;
  default:
    処理;
}
```


## 繰り返し

### while文

条件を元に先に判定（0回実行の可能性がある）

```java
while (条件式) {
  処理;
}
```

### do-while文

最低1回は実行される

```java
do {
  処理;
} while (条件式);
```

### for文

```java
for (初期化; 条件式; 更新) {
  処理;
}
```
```java
for (int i = 0; i < n; i++>) {
  処理;
}
```

### 拡張for文

```java
for (型 変数 : 配列・コレクション) {
  処理;
}
```
```java
for (int x : numbers) {
  処理;
}
```

### 処理の中断

- `break`：最も内側のループまたは`switch`を抜ける
- `continue`：現在のループを中断して次の繰り返しへ