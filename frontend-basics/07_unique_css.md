<!-- omit in toc -->
# 7. ユニークなCSS

### 目次

- [疑似要素](#疑似要素)
- [画像加工](#画像加工)
- [レスポンシブWebデザイン](#レスポンシブwebデザイン)
  - [viewport](#viewport)
  - [メディアクエリ](#メディアクエリ)
  - [画像](#画像)

<br>

## 疑似要素

特定の要素の特定の部分にスタイルをつける

<br>

1. `::first-letter`：ブロック型の要素の最初の行の最初の文字
2. `::first-line`：ブロック型の要素の最初の行
3. `::before`：要素の最初の子要素
4. `::after`：要素の最後の子要素

<br>

## 画像加工

- 画像、拝啓、教会の描画の調整
- `filter`プロパティ：画像加工のプロパティ

<br>

属性
- `drop-shadow(3px 3px 2px black)`：
  - 画像の輪郭に影
  - 値：`(x軸の影の長さ y軸の影の長さ ぼかし)`
- `grayscale(100%)`：グレースケール
- `sepia(100%)`：セピア調
- `opacity(50%)`：透過率
- `blur(10px)`：ぼかし
- `brightness(200%)`：明暗
- `contrast(200%)`：コントラスト
- `saturate(200%)`：彩度
- `hue-rotate(120deg)`：色相角度
- `invert(100%)`：色の反転

<br>

## レスポンシブWebデザイン

### viewport

```html
<meta name="viewport" content="width=device-width">
```

- ブラウザ内の表示領域
- 現在表示されているのがスマホかPC化を判別するためにブラウザの幅を利用する
- 正しく幅の値を得るために必要（得られない場合、980pxと認識）

### メディアクエリ

```css
  @media(max-width:800px){
    #wrap{
      width: 100%;
    }
  }
```

- ブラウザの幅の値（ブレイクポイント）によって適用するCSSを切り替える
- 上記の場合、ブラウザのビューポートの横幅が800px以下なら{}内のCSSを適用

### 画像

- `background-size`プロパティ
  - `background: cover;`：要素の大きさに応じて、縦横比を変えずかつすき間が生じないように画像を表示
  - `background: contain;`：画像の大きさに応じて縦横比を変えずかつ画像の隠れる部分が生じないように画像を表示
- `background-position: center;`：起点を真ん中にすることができる