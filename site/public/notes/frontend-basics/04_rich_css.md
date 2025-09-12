# 4. リッチなCSS

### 目次

- [影のプロパティ](#影のプロパティ)
- [角丸のプロパティ](#角丸のプロパティ)
- [グラデーション](#グラデーション)

<br>

## 影のプロパティ

1. `box-shadow`プロパティ
  
  ```css
  div{
    box-shadow: 10px 10px 10px gray;
  }
  ```

  - 要素の周囲の影
  - 値：`(横方向のずれ具合 縦方向のずれ具合 ぼかし具合 [影の大きさの増分] 色)`
  - `inset`：内側の影
  - 複数の影：値を`,`で区切る

2. `text-shadow`プロパティ
  
  ```css
  div{
    text-shadow: 3px 3px 2px gray;
  }
  ```

  - 文字の周囲の影
  - 値：`(横方向のずれ具合 縦方向のずれ具合 ぼかし具合 [影の大きさの増分] 色)`
  - 複数の影：値を`,`で区切る

<br>

## 角丸のプロパティ

`border-radius`プロパティ

```css
div{
  border-radius: 10px;
}
```

- 境界の角を丸める
- 値：丸みの半径（borderの太さの中間から数える）
  - 値が4つ：上下左右の半径
- 正円：`border-radius: 50%;`
- 楕円：`width`を指定

<br>

## グラデーション

`background`プロパティ

1. `linear-gradient()`：直線的なグラデーションの値
  
  ```css
  div{
    background: linear-gradient(white, gray);
  }
  ```

  - `(white 50%, gray 80%)`：開始点（中心）から終了点までの相対的な距離
  - `(45deg, white, gray)`：回転角度（指定の値+180）

2. `radial-gradient()`：放射状のグラデーションの値
  
  ```css
  div{
    background: radial-gradient(white, gray);
  }
  ```

  - `(white 50%, gray 80%)`：開始点から終了点までの相対的な距離
  - `(at top, white, gray)`：開始点の位置（`%`, `px`でも指定可能）
  - `(circle at top, white, gray)`：円形の状態を保つ

3. `conic-gradient()`：扇形（円錐）のグラデーションの値
  
  ```css
  div{
    background: conic-gradient(white, gray);
  }
  ```

  - `(white 0%, gray 25% 50%, white 50% 75%, gray 76% 100%)`：開始点から終了点までの相対的な距離

<br>

→[5. コンテンツを変形するCSS](05_transform.md)