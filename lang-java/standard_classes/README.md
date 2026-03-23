<!-- omit in toc -->
# Java標準クラス

<!-- omit in toc -->
### 目次

- [`java.lang`](#javalang)
  - [`String`](#string)
    - [インスタンスメソッド](#インスタンスメソッド)
    - [staticメソッド](#staticメソッド)
  - [`Integer`](#integer)
    - [インスタンスメソッド](#インスタンスメソッド-1)
    - [staticメソッド](#staticメソッド-1)
- [`java.util`](#javautil)
  - [`ArrayList`](#arraylist)
    - [インスタンスメソッド](#インスタンスメソッド-2)
    - [`List`のインスタンスメソッド](#listのインスタンスメソッド)
  - [`HashSet`](#hashset)
    - [インスタンスメソッド](#インスタンスメソッド-3)
    - [`Set`のインスタンスメソッド](#setのインスタンスメソッド)
  - [`HashMap<K,V>`](#hashmapkv)
    - [インスタンスメソッド](#インスタンスメソッド-4)
    - [`Map`のインスタンスメソッド](#mapのインスタンスメソッド)
    - [`Map.Entry<K,V>`](#mapentrykv)
  - [`Scanner`](#scanner)
    - [インスタンスメソッド](#インスタンスメソッド-5)

## `java.lang`

### `String`

- 不変（immutable）な文字列クラス
- 内容変更不可、変更操作は新しいStringを生成

#### インスタンスメソッド

<!-- omit in toc -->
##### 文字列の長さ

- `int length()`：文字列の長さを返す
- `boolean isEmpty()`：文字列の長さが0かどうかを返す

<!-- omit in toc -->
##### 新しい文字列

- `String substring(int beginIndex)`：beginIndex以降の範囲を切り出した新しい`String`を返す
- `String substring(int beginIndex, int endIndex)`：beginIndexからendIndex-1までの範囲を切り出した新しい`String`を返す
- `String replace(CharSequence target, CharSequence replacement)`：指定文字列を置き換えた新しい`String`を返す
- `String concat(String str)`：もとの文字列の末尾にstrを連結する
- `String[] split(String regex)`：区切り文字regexで文字列を分割する

<!-- omit in toc -->
##### 文字列と部分比較

- `char charAt(int index)`：indexの文字を返す
- `boolean contains(CharSequence s)`：文字列がsを含むかどうかを返す
- `int indexOf(String str)`：strが初めて現れるindexを返す
- `int lastIndex(String str)`：strが最後に現れるindexを返す
- `boolean startsWith(String prefix)`：文字列がprefixで始まるかどうかを返す
- `boolean endsWith(String suffix)`：文字列がsuffixで終わるかどうかを返す

<!-- omit in toc -->
##### 文字列と全体比較

- `boolean equals(Object o)`：oと同じ文字列内容かどうかを返す
- `boolean equalsIgnoreCase(String anotherString)`：anotherStringと等しいかどうかを返す（大文字小文字を無視）
- `int compareTo(String anotherString)`：anotherStringと辞書的に比較する
  - 戻り値<0：文字列はanotherStringより前
  - 戻り値=0：文字列はanotherStringと等しい
  - 戻り値>0：文字列はanotherStringより後ろ
- `int compareToIgnoreCase(String str)`：strと辞書的に比較する（大文字小文字を無視）
- `boolean contentEquals(CharSequence cs)`：csと等しいかどうかを返す

#### staticメソッド

- `String valueOf(boolean b)`：bを文字列で返す
  - `true`：`"true"`
  - `false`：`"false"`
- `String valueOf(char c)`：cを`String`にして返す
- `String valueOf(char[] data)`：dataを`String`にして返す
- `String valueOf(double d)`：dを`String`にして返す
- `String valueOf(int i)`：iを`String`にして返す
- `String valueOf(Object obj)`：objを`String`にして返す

### `Integer`

#### インスタンスメソッド

- `int compareTo(Integer anotherInteger)`：anotherIntegerと比較する
- `boolean equals(Object obj)`：objと等しいかどうかを返す

- `float floatValue()`：`float`にして返す
- `int intValue()`：`int`にして返す
- `String toString()`：`String`にして返す
- `int hashCode()`：ハッシュ値を返す

#### staticメソッド

- `int compare(int x, int y)`：xとyを比較する
  - 0：`x == y`
  - <0：`x < y`
  - >0：`x > y`

- `max(int a, int b)`：a, bで大きい方を返す
- `min(int a, int b)`：a, bで小さい方を返す
- `int sum(int a, int b)`：`a + b`を返す

- `int parseInt(String s)`：sを`int`にして返す
- `Integer decode(String nm)`：nmを`Integer`にして返す
- `String toString(int i)`：iを`String`にして返す
- `Integer valueOf(int i)`：iを`Integer`にして返す
- `Integer valueOf(String s)`：sを`Integer`にして返す


## `java.util`

### `ArrayList`

- 重複あり
- 順序あり

```java
List<String> list = new ArrayList<>();
```

#### インスタンスメソッド

<!-- omit in toc -->
##### 要素の追加・更新

- `void add(E e, int index)`：indexにeを追加
- `boolean add(E e)`：末尾にeを追加
- `void addFirst(E e)`：先頭にeを追加
- `void addLast(E e)`：末尾にeを追加
- `boolean addAll(Collection c)`：末尾にcの要素を全て追加
- `E set(int index, E e)`：indexの要素をeに変更する
  - 変更前の要素を返す

<!-- omit in toc -->
##### 要素の削除

- `void clear()`：要素を全て消す
- `E remove(int index)`：indexの要素を削除する
  - 削除した要素を返す
- `E removeFirst()`：先頭の要素を削除する
- `boolean remove(Object o)`：最初に現れるoを削除する（存在すれば）
- `boolean remoceAll(Collection c)`：cに含まれる要素を全て削除する
- `boolean retainAll(Collection c)`：cに含まれる要素以外の要素を全て削除する
- `void removeRange(int fromIndex, toIndex)`：fromIndexからtoIndexまでの要素を削除する

<!-- omit in toc -->
##### 要素の検索

- `boolean contains(Object o)`：oが含まれるかどうかを返す
- `E get(int index)`：indexの要素を返す
- `E getFirst()`：先頭の要素を返す
- `E getLast()`：末尾の要素を返す
- `int indexOf(Object o)`：oが最初に現れるindexを返す
  - 存在しない場合、`-1`を返す
- `int lastIndexOf(Object o)`：pが最後に現れるindexを返す
  - 存在しない場合、`-1`を返す

<!-- omit in toc -->
##### その他

- `int size()`：要素の数を返す
- `boolean equals(Object o)`：oと等しいかどうかを返す
- `boolean isEmpty()`：リストが空ならば`true`を返す
- `List subList(int fromIndex, int toIndex)`：fromIndexからtoIndex-1までの要素を持ったリストを返す
- `Object<> toArray()`：配列にして返す

#### `List`のインスタンスメソッド

- `boolean containsAll(Collection c)`：リストがcの要素全てを含むかどうかを返す
- `void replaceAll(operator)`：全ての要素にoperatorを適用して返す
- `List reversed()`：逆順のリストを返す
- `void sort(Comparator<? super E> c)`：cによってソートしたリストを返す


### `HashSet`

- 重複なし
- 順序なし

```java
Set<String> set = new HashSet<>();
```

#### インスタンスメソッド

<!-- omit in toc -->
##### 要素の操作

- `boolean add(E e)`：eが存在しなければ追加する
- `boolean remove(Object o)`：oを削除する

<!-- omit in toc -->
##### Setの操作

- `void clear()`：全ての要素を削除する
- `Object clone()`：コピーを返す（参照元は同じ）
- `Object[] toArray()`：全ての要素を含む配列を返す

<!-- omit in toc -->
##### その他

- `boolean contains(Object o)`：oが含まれているかどうかを返す
- `boolean isEmpty()`：要素が1つもないならば`true`を返す
- `int size()`：要素の個数を返す

#### `Set`のインスタンスメソッド

- `boolean addAll(Collection c)`：cの要素を全てコピーしてくる
- `boolean containsAll(Collection c)`：cの要素を全て含んでいれば`true`を返す
- `boolean equals(Object o)`：cと等しいかどうかを返す
- `boolean removeAll(Collection c)`：cに含まれる要素を全て削除する
- `boolean retainAll(Collection c)`：cに含まれる要素以外を削除する


### `HashMap<K,V>`

キーと値の組み合わせ
- `K`：このmapのキーの型
- `V`：このmapの値の型

```java
Map<String, Integer> map = new HashMap<>();
```

#### インスタンスメソッド

<!-- omit in toc -->
##### mapの大きさ

- `int size()`：mappingの数を返す
- `boolean isEmpty()`：mappingが1つもないならば`true`を返す

<!-- omit in toc -->
##### mapの操作

- `void clear()`：mapを空にする
- `Object clone()`：インスタンスのコピーを作る
  - キー、値の参照先は同じ
- `void putAll(Map m)`：mのmappingをすべてコピーしてくる

<!-- omit in toc -->
##### mappingの操作

- `V put(K key, V value)`：key, valueのmappingを追加する
  - すでに存在する場合は、上書きして以前の値を返す
  - 存在しなければ`null`を返す
- `boolean containsKey(Object key)`：keyを含むかどうか
- `boolean containsValue(Object value)`：valueを含むかどうか
- `V get(Object key)`：keyに対応する値を返す
  - 存在しない場合は`null`を返す
- `V remove(K key)`：keyのmappingを削除する

<!-- omit in toc -->
##### 全てのキー／値

- `Set<Map.Entry<K,V>> entrySet()`：`Map.Entry`の`Set`を返す
- `Set<K> keySet()`：キーの`Set`を返す
- `Collection<V> values()`：値のコレクションを返す

#### `Map`のインスタンスメソッド

- `boolean equals()`
- `void forEach(action)`
- `V getOrDefault(Object key, V defaultValue)`：keyの値を返し、存在しなければdefaultValueを返す
- `boolean remove(Object jey, Object value)`：keyがvalueを持っているときだけ削除する
- `V replace(K key, V value)`：keyが存在する場合のみ、valueに書き換える
- `boolean replace(K key, V oldValue, V newValue)`：keyがoldValueにmapされている場合のみ、newValueに書き換える

#### `Map.Entry<K,V>`

- `Map`の1要素を表す型
- `Map`のループ処理によく使う


### `Scanner`

```java
Scanner sc = new Scanner(System.in);
```

#### インスタンスメソッド

- `String next()`：単語を読み取る（空白まで）
- `String nextLine()`：一行読み取る
- `int nextInt()`：整数を読み取る（空白または改行まで）
- `double nextDouble()`：小数を読み取る（空白または改行まで）
- `boolean nextBoolean()`：true/falseを読み取る
- `boolean hasNext(Pattern pattern)`：次の要素がpatternに一致するかどうかを返す
- `void close()`：Scannerを閉じる