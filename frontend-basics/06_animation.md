<!-- omit in toc -->
# 6. アニメーションのCSS

### 目次

- [トランジション](#トランジション)
- [アニメーション](#アニメーション)
- [三次元](#三次元)

<br>

## トランジション

`transition`プロパティ
- 要素の上にマウスを載せた際の、変化前と変化後の間を定義
- 値が数字を持つほとんどのCSSプロパティで可能
- マウスが要素の上から離れると元に戻る
- JavaScriptの表示を制御できる

```css
#child{
  transition:
    color 1s linear 0s,
    background-color 1s linear 0s;
}
#child:hover{
  color: red;
  background-color: black;
  translate: 50px;
  rotate: 30deg;
  scale: 2;
}
```

- 時間の変化
- 値：`(変化するプロパティ 遷移時間 変化のスタイル 遅延時間)`
- 変化のスタイル
  - `linear`：等速
  - `ease-in-out`：最初と最後はゆっくり
- `:hover`：その要素の上にマウスポインタが乗った時、{}内のCSSを適用する
- `transition: all`

<br>

## アニメーション

`animation`プロパティ
- Webページが開いた際の、変化前と変化後の間を定義
- 値が数字を持つほとんどのCSSプロパティで可能

```css
#child{
  animation: anime1 3s linear 0s infinite normal both;
}
@keyframes anime1{
  0%{rotate: 0deg;}
  100%{rotate: 360deg;}
}
```

- アニメーション
- 値：`(アニメーションの名前 遷移時間 変化のスタイル 遅延時間 繰り返し回数 方向 アニメーション前後の状態)`
  - アニメーションの名前：台本、名前は任意
  - 遷移時間：1つのアニメーションの時間
  - 変化のスタイル
    - `linear`：等速
    - `ease-in-out`：最初と最後はゆっくり
  - 遅延時間：ページを開いてアニメーションが開始されるまでの時間
  - 繰り返し回数
    - `infinite`：無限の繰り返し
  - 方向
    - `normal`：順方向
    - `alternate`：交互
  - アニメーション前後の状態
    - `both`：前後両方にアニメーション有効
  - `@`（アットルール）：CSSの動作を規定するもの
  - `keyframe`：主要な時間点

<br>

## 三次元

親要素に三次元のCSSを指定する

  1. `transform-style`プロパティ：子要素の次元を決める
    - `preserve-3d`：三次元に配置する値
    - `flat`：二次元に配置する値

  2. `perspective`プロパティ：子要素とユーザとの間の距離を決める（遠近感）

<br>

1. 子要素を三次元回転させる

  ```css
  #child{
    rotate: y 40deg;
  }
  ```

  - 値：`(軸 角度)`
    - 値が4つ：`(xのベクトル yのベクトル zのベクトル 回転の角度)`

2. 子要素を三次元移動させる
  
  ```css
  #child{
    translate: 100px 0px 0px;
  }
  ```

  - 値：`(x軸に沿った距離 y軸に沿った距離 z軸に沿った距離)`

3. 子要素を三次元伸縮させる
  
  ```css
  #child{
    scale: 1.5 1 1;
  }
  ```

  - 値：`(x軸方向に伸縮した倍率 y軸方向に伸縮した倍率 z軸方向に伸縮した倍率)`

<br>

→[7. ユニークなCSS](07_unique_css.md)