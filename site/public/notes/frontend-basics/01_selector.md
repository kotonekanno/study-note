# 1. セレクタ

### 目次

- [要素セレクタ](#要素セレクタ)
- [クラスセレクタ](#クラスセレクタ)
- [IDセレクタ](#idセレクタ)
- [ユニバーサルセレクタ（全称セレクタ）](#ユニバーサルセレクタ全称セレクタ)
- [CSSの順番](#cssの順番)

## 要素セレクタ

要素名にスタイルを適用する

```css
<style>
  p{color: blue;}
</style>

<p>Hello</p>
```

## クラスセレクタ

- クラス名にスタイルを適用する
- クラス名の前に`.`をつける
- 複数の要素に対してスタイルを適用できる

```css
<style>
  p{color: blue;}
  .special{color: green;}
</style>

<p class=”special”>Hello</p>
```

## IDセレクタ

- ID名にスタイルを適用する
- ID名の前に`#`をつける
- そのファイルの中で重複しない名前を指定

```css
<style>
  .special{color: green;}
  #unique{color: red;}
</style>

<p class=”special” id=”unique”>こんにちは</p>
```

## ユニバーサルセレクタ（全称セレクタ）

- 全ての要素にスタイルを適用する（何も指定していない要素のみ）
- セレクタ名の前に`*`をつける

```css
<style>
  p{color: blue;}
  *{color: yellow;}
</style>
```

## CSSの順番

- 同じプロパティに複数の値を定義した場合は、最後の値が有効になる
- セレクタの順番により、強さが異なる（弱→強）

1. ユニバーサルセレクタ
2. 要素セレクタ
3. クラスセレクタ
4. IDセレクタ

→[2. 継承・結合・擬似クラス](02_inheritance_combinators_pseudo.md)
