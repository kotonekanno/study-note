# 3.プロパティ

### 目次

- [文字を装飾するプロパティ](#文字を装飾するプロパティ)
  - [colorプロパティ](#colorプロパティ)
  - [font-sizeプロパティ](#font-sizeプロパティ)
  - [font-weightプロパティ](#font-weightプロパティ)
  - [font-familyプロパティ](#font-familyプロパティ)
  - [font-styleプロパティ](#font-styleプロパティ)
  - [text-decorationプロパティ](#text-decorationプロパティ)
  - [text-alignプロパティ](#text-alignプロパティ)
  - [text-indentプロパティ](#text-indentプロパティ)
  - [line-heightプロパティ](#line-heightプロパティ)
- [枠を装飾するプロパティ](#枠を装飾するプロパティ)
  - [borderプロパティ](#borderプロパティ)
  - [widthプロパティ](#widthプロパティ)
  - [heightプロパティ](#heightプロパティ)
  - [marginプロパティ](#marginプロパティ)
  - [paddingプロパティ](#paddingプロパティ)
  - [フレックスボックス](#フレックスボックス)
  - [ボックスモデル](#ボックスモデル)
- [背景を装飾するプロパティ](#背景を装飾するプロパティ)
  - [background-colorプロパティ](#background-colorプロパティ)
  - [background-imageプロパティ](#background-imageプロパティ)
  - [backgeound-sizeプロパティ](#backgeound-sizeプロパティ)
  - [background-repeatプロパティ](#background-repeatプロパティ)
  - [background-positionプロパティ](#background-positionプロパティ)
- [色の名前](#色の名前)
  - [VGAカラー](#vgaカラー)
  - [色コード](#色コード)
  - [RGB関数表記](#rgb関数表記)
- [子要素を親要素の中央に配置する方法](#子要素を親要素の中央に配置する方法)
- [値まとめ](#値まとめ)

<br>

## 文字を装飾するプロパティ

### colorプロパティ

- `color: blue;`
- 文字の色
- 値：キーワード、色コード　等（参照：[色の名前](#色の名前)）

### font-sizeプロパティ

- `font-size: 16px;`
- 文字の大きさ
- 値：px値、%値、rem値　等

### font-weightプロパティ

- `font-weight: bold;`
- 文字の太さ
- 値
  - 1～1000までの数値
  - `normal`：標準
  - `bold`：太字

### font-familyプロパティ

- `font-family: serif;`
- 文字のフォント
- 値
  - `serif`：明朝体
  - `sans-serif`：ゴシック体
  - フォント名
- 必ずしもそのフォントが使えるとは限らないので、代替フォントを用意する

### font-styleプロパティ

- `font-style: italic;`
- 文字の種類
- 値
  - `normal`：標準
  - `italic`：イタリック体
  - `oblique`：斜体

### text-decorationプロパティ

- `text-decoration: underline;`
- 装飾線
- 値
  - `none`：無効
  - `underline`：下線
  - `overline`：上線
  - `line-through`：打消し線
- 色や線種も変更できる

### text-alignプロパティ

- `text-align: center;`
- 水平方向の配置
- 値：`center`, `right`, `left`

### text-indentプロパティ

- `text-indent: 30px;`
- 字下げの幅
- 値：px値、%値　等

### line-heightプロパティ

- `line-height: 1.7;
- 1行の高さ
- 値：数字のみ（n倍）、px値、%値　等

<br>

## 枠を装飾するプロパティ

### borderプロパティ

- `border: 1px solid gray;`
- 境界・枠線
- 値：`枠線の太さ 種類 色`
- 種類
  - `solid`：実線
  - `double`：二重線
  - `dotted`：点線
  - `dashed`：破線

### widthプロパティ

- `width: 200px;`
- コンテンツの幅
- 値：px値、%値　等
- ブロック型の要素には有効
- インライン型の要素には無効だが、`img`, `input`, `select`, `textarea`には有効


### heightプロパティ

- `height: 200px;`
- コンテンツの高さ
- 値：px値、%値　等
- ブロック型の要素には有効
- インライン型の要素には無効だが、`img`, `input`, `select`, `textarea`には有効

### marginプロパティ

- `margin: 50px;`
- 枠の外側の隙間
- 値：px値、%値　等
- ブロック型の要素には有効
- インライン型の要素は白湯のみ有効

### paddingプロパティ

- `padding: 50px;`
- 枠の内側の隙間
- 値：px値、%値　等
- ブロック型の要素には有効
- インライン型の要素にも有効だが、上下は他の要素にはみ出す

### フレックスボックス

- `display: flex;`
- 要素の並べ方
- `display`：表示種別
- `flex`：伸縮

### ボックスモデル

- 要素の領域（四角形）のこと
- コンテンツ・`padding`・`border`・`margin`でできている
- 要素の枠線の外側の横幅／縦幅は、以下の合計値となる
  - コンテンツの幅／高さ（`width`）
  - 内側の隙間（`padding`）×2
  - 枠の太さ（`border`）×2
- インライン型の要素は、無効になるものがある

<br>

## 背景を装飾するプロパティ

### background-colorプロパティ

- `background-color: gray;`
- 背景の色
- 値：キーワード、色コード　等（参照：[色の名前](#色の名前)）

### background-imageプロパティ

- `background-image: url(" ");`
- 背景の画像
- 値：`url()`

### backgeound-sizeプロパティ

- 背景のサイズ
- 値：要素に対する横方向・縦方向の%、またはpx値
  - `100% 100%`：要素にぴったり収まる
  - `cover`：縦横比を保ったまま隙間のない背景となる
  - `contain`：縦横比を保ったまま全体を表示する

### background-repeatプロパティ

- `background-repeat: no-repeat;`
- 背景の繰り返し
- 値
  - `repeat`：繰り返す（初期値）
  - `no-repeat`：繰り返ししない
  - `repeat-x`：横方向にのみ繰り返す
  - `repeat-y`：縦方向にのみ繰り返す

### background-positionプロパティ

- `background-position: top;`
- 背景の位置
- 値
  - `top`, `right`, `bottom`, `left`, `center`
  - px値、%値　等

<br>

## 色の名前

### VGAカラー

### 色コード
- 光の三原色（赤、緑、青）の量の大きさを16進数で指定する
- 先頭に`#`をつける
- 例：
 - 黒：`#000000`
 - 白：`#ffffff`
- 3桁表示も可能（`#f53`）
- アルファ値を追加して半透明にすることができる（`#ff000099`）

### RGB関数表記
- 光の三原色の量の大きさを10進数で指定する（0～255）
- `rgb()`を使用する
- アルファ値を追加して半透明にすることができる（`rgba(0,0,0,0.5)`）
- 完全な透明色：`transparent`

<br>

## 子要素を親要素の中央に配置する方法

```css
#parent{
  width: 300px;
  height: 300px;
  border: 1px solid blue;
  position: reletive;
}
.child{
  width: 100px;
  height: 100px;
  border: 1px solid red;
}
.center{
  position: absolute;
  top: 0px;
  left: 0px;
  right: 0px;
  bottom: 0px
  margin: auto;
}
```

- `position`プロパティ：配置のプロパティ
  - `reletive`：通常の配置
  - `absolute`：`position: reletive;`を設定した親要素に対する絶対位置で配置

<br>

## 値まとめ

- キーワード：`red`, `top`, `left`, `anime`, `linear`, `normal`, `both`
- 数字の値
- 単位の値：`px`, `%`, `s`（`s`以外は値が0の場合省略可能）
- 16進数の値
- CSS関数
  - `transform: scale(3);`
  - `background-image: url(" ");`
  - `background: linear-gradient(white, gray);`
  - 計算
    - `margin-left: calc(50% - 50px);`
    - `width: calc(100px * cos(30deg));`

<br>

→[4. リッチなCSS](04_rich_css.md)