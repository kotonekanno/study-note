<!-- omit in toc -->
# 5. コンテンツを変形するCSS

### 目次

- [回転のプロパティ](#回転のプロパティ)
- [伸縮のプロパティ](#伸縮のプロパティ)
- [移動のプロパティ](#移動のプロパティ)

<br>

## 回転のプロパティ

1. `rotate`プロパティ
  
  ```css
  #child{
    rotate: 30deg;
  }
  ```

  - 回転する
  - 値：角度

2. `transform`プロパティ
  
  ```css
  #child{
    transform: rotate(03deg);
  }
  ```

  - 変形のプロパティ
  - `transform-origin`プロパティ：中心位置の変更

<br>

## 伸縮のプロパティ

1. `scale`プロパティ
  
  ```css
  #child{
    scale: 2 1;
  }
  ```

  - 伸縮する
  - 値：倍率（単位なし）、`%`値（`-`で反転）
  - 値が2つ：`横の値 縦の値`

2. `transform`プロパティ
  
  ```css
  #child{
    transform: scale(2, 1);
  }
  ```

  - 変形のプロパティ
  - 値：倍率（単位なし）、`%`値（`-`で反転）
  - 値が2つ：`横の値 縦の値`
  - `transform-origin`プロパティ：中心位置の変更

<br>

## 移動のプロパティ

1. `translate`プロパティ
  
  ```css
  #child{
    translate: 100px 100px;
  }
  ```

  - 移動する
  - 値：距離（`px`等）、`%`値
  - 値が1つ：横方向に移動
  - 値が2つ：`横の値 縦の値`

2. `transform`プロパティ
  
  ```css
  #child{
    transform: translate(100px, 100px);
  }
  ```

  - 変形のプロパティ
  - 値：距離（`px`等）、`%`値
  - 値が1つ：横方向に移動
  - 値が2つ：`横の値 縦の値`
  - `skew()`：歪みの値
    - 値が1つ：横方向の歪み
    - 値が2つ：`横方向 縦方向`の歪み

<br>

→[6. アニメーションのCSS](06_animation.md)