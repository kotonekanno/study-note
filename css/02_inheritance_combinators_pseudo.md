# 2. 継承・結合子・擬似クラス

### 目次

## 継承

```css
<div id=”parent”>親要素
  <div id=”child”>子要素
    <div id=”grandchild”>孫要素</div>
  </div>
</div>
```

- 継承されるプロパティ：文字色、文字サイズ等
- 継承されないプロパティ：`border`, `margin`, `padding`, `background-image`等

## 結合子

```css
<style>
  div{border: 1px solid gray;>
</style>

<div id=”parent”>親要素
  <div id=”child”>子要素
    <div id=”grandchild”>孫要素</div>
  </div>
</div>
<div id=”sibling1”>次兄弟要素</div>
<div id=”sibling2”>後続兄弟要素</div>
```

- `#parent div`：子要素、孫要素に適用
- `#parent > div`：子要素に適用
- `#parent + div`：次兄弟要素に適用
- `#parent ~ div`：次兄弟要素m、後続兄弟要素に適用

## 擬似クラス

- セレクタに対して特定の動作を指定する
- `:`を付加する

<br>

- `:hover`：ポインタが要素の上に乗った時
- `:first-of-type`/`last-of-type`：最初・最後の要素
- `:nth-of-type`：特定の型に一致したら

```css
<style>
  p:hover{color: red;}
  p:first-of-type{color: blue;}
  p:nth-of-type(2){color:green;}
</style>
```

→[3. プロパティ](#03_property.md)
