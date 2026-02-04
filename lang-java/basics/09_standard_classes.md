<!-- omit in toc -->
# 標準クラス

<!-- omit in toc -->
### 目次

- [概要](#概要)
- [`java.lang`パッケージ](#javalangパッケージ)
  - [`Object`クラス](#objectクラス)
  - [`String`クラス](#stringクラス)
- [ラッパークラス](#ラッパークラス)
- [コレクションフレームワーク](#コレクションフレームワーク)
  - [概要](#概要-1)
  - [`List`](#list)
  - [`Set`](#set)
  - [`Map`](#map)
- [`Optional`クラス](#optionalクラス)

## 概要

標準クラスとは

- Java言語に標準で用意されているクラス群
- JDKに含まれる
- 追加ライブラリ不要


## `java.lang`パッケージ

- `import`不要
- 最も基礎的なクラス群

### `Object`クラス

全てのクラスの親クラス

<!-- omit in toc -->
#### メソッド

- `toString()`：文字列を返す
- `equals(Object)`：等価比較
- `hashCode()`：ハッシュ値（`int`）を返す
- `getClass()`：実行時に属しているクラスを返す
- `clone()`：同じ内容を持つ別インスタンスを作って返す

<!-- omit in toc -->
#### `equals`と`hashCode`

- `equals`が`true`ならば`hashCode`も一致すべき
- 主にコレクションで使用

### `String`クラス

- 不変（immutable）な文字列クラス
- 内容変更不可、変更操作は新しいStringを生成

<!-- omit in toc -->
#### メソッド

- `length()`：文字数（`int`）を返す
- `isEmpty()`：文字列の長さが0かどうか（`boolean`）を返す
- `substring(int begin, int end)`：`begin`以上`end`未満の範囲を切り出した新しい`String`を返す
- `equals(Object)`：同じ文字列内容か（`boolean`）を返す
- `contains(CharSequence)`：指定した文字列が中に含まれているか（`boolean`）を返す
- `replace(CharSequence target, CharSequence replacement)`：指定文字列を置き換えた新しい`String`を返す


## ラッパークラス

- プリミティブ型をオブジェクトとして扱うためのクラス

<!-- omit in toc -->
### プリミティブ型との対応

- `int`: `Integer`
- `long`: `Long`
- `double`: `Double`
- `boolean`: `Boolean`

<!-- omit in toc -->
#### オートボクシング

```java
Integer i = 10;
int x = 1;
```

- 自動変換
- 実体はオブジェクト


## コレクションフレームワーク

### 概要

- `Collection`
  - `List`
    - `ArrayList`
  - `Set`
    - `HashSet`
  - `Queue`
- `Map`
  - `HashMap`

### `List`

```java
List<String> list = new ArrayList<>();
```

- 順序あり・重複あり

<!-- omit in toc -->
#### メソッド

- `add(E)`：要素の追加
- `get(int)`：要素の取得
- `size()`：要素数（`int`）の取得
- `remove(int)`：要素の削除

<br>

- `System.arraycopy(コピー元, コピー元の開始位置, コピー先, コピー先の開始位置, コピーする要素数)`

<!-- omit in toc -->
#### 補足

- `オブジェクト型[]`とすることで、同じ親クラスを持つ子クラスを、親型でリストにできる
- 繰り返しの際は、`list[i]`とするより、`for-each`構文を用いると良い

### `Set`

```java
Set<String> set = new HashSet<>();
```

- 重複なし・順序なし

<!-- omit in toc -->
#### メソッド

- `add(E)`：要素の追加
- `contains(E)`：存在確認
- `size()`：要素数（`int`）の取得

### `Map`

```java
Map<String, Integer> map = new HashMap<>();
```

- キーと値の対応表

<!-- omit in toc -->
#### メソッド

- `put(K,V)`：指定したキーに値を関連付けて登録
  - すでに存在する場合は、上書きして以前の値を返す
  - 存在しなければ`null`を返す
- `get(K)`：指定したキーに対応する値を取得
  - 存在しない場合は`null`を返す
- `containsKey(K)`：存在したキーが含まれているかどうか（`boolean`）を返す
- `keySet()`：含まれる全てのキーの集合（`Set<K>`）を取得する


## `Optional`クラス

`null`の可能性を型として表現するためのラッパー

```java
Optional<String> opt;
```

<!-- omit in toc -->
### 生成メソッド

- `of(T)`：非`null`の値から`Optional`を生成する
- `ofNullable(T)`：値が`null`でも生成できる`Optional`
  - `null`の場合は空の`Optional`
- `empty()`：値を持たない空の`Optional`を生成する

<!-- omit in toc -->
### 操作メソッド

- `isPresent()`：値を保持しているかどうか（`boolean`）を判定する
- `get()`：保持している値を取得する
  - 値がない場合、`NoSuchElementException`
- `orElse(T)`：値があればそれを返し、なければ指定した代替値を返す
- `ifPresent(Consumer<? super T>)`値が存在する場合のみ、その値を使って処理を実行する（戻り値なし）