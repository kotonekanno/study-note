<!-- omit in toc -->
# Javaにおける正規表現

<!-- omit in toc -->
### 目次

- [注意点](#注意点)

## 注意点

- `\`はJavaでもエスケープ文字であるため、`\\`と書く

## 基本構文

```java
Pattern p = Pattern.compile("\\d+");
Matcher m = p.matcher("123abc");

if (m.find()) {
    System.out.println(m.group());
}
```

## 関連メソッド

- `Matcher.find()`：部分一致
- `Matcher.matches()`：完全一致
- `String.matches()`：完全一致

## フラグ指定

`Pattern.compile()`の第2引数に指定する

- 大文字無視：`CASE_INSENSITIVE`

## グループ取得

```
(m.group(1))
```

- `group(0)`：全体
- `group(n)`：n個目のグループ