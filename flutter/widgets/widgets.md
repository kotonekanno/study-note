<summary>目次</summary>
<details></details>

# Stateless Widget

## Text

- 単一スタイルの文字列を表示

### プロパティ

- `String` `data`：表示するテキスト
- [`TextStyle`](#textstyle) `style`
- [`TextAlign`](#textalign) `textAlign`
- [`TextOverflow`](#textoverflow) `overflow`
- `int` `maxLines`：行数の最大値
- `bool` `softWrap`：テキストがウィジェット幅を超えるときに自動で折り返すかどうか
  - `true`（デフォルト）：改行する
  - `false`：改行しない
- `double` `textScaleFactor`：ユーザーが端末の設定で変更した文字の大きさを反映させる
  - `1.0`：標準
  - `1.2`：少し大きめ

## Icon

- アイコン表示
- https://api.flutter.dev/flutter/material/Icons-class.html

### プロパティ

- `IconData` `icon`：表示するアイコン
- `double` `size`：アイコンの大きさ
- [`Color`](#color) `color`：アイコンの色
- `String` `semanticLabel`：アクセシビリティ用の説明テキスト

# 非Widgetクラス

## ImageProvider

画像を提供する

### サブクラス

- `AssetImage(name)`：アプリに含まれる画像
  - `name`：画像のパス
- `NetworkImage(url)`：ネットワーク上の画像
  - `url`：画像のURL
- `FileImage(file)`：デバイス上のファイル
  - `file`：`File`オブジェクト

## EdgeInsets

- `EdgeInsets.all(value)`：4辺同じ余白
- `EdgeInsets.symmetric(horizontal: x, vertical: y)`：横・縦別指定
- `EdgeInsets.only(left: l, top; t, right: r, bottom: b)`：個別指定

## Color

- 公式色：`Colors.blue`
- カスタム：`Color(0xFFRRGGBB)`（16進数）
- 色の濃淡：`Colors.blue.shade200`

## Alignment

- `Alignment.center`：中央
- `Alignment.topLeft`/`Alignment.topRight`：上左／上右
- `Alignment.bottomLeft`/`Alignment.bottomRight`：下左／下右
- `Alignment.topCenter`/`Alignment.bottomCenter`：上中央／下中央
- `Alignment.centerLeft`/`Alignment.centerRight`：左中央／右中央

<br>

- `Alignment(x, y)`：x, y座標で微調整
  - `x`：横方向（-1.0~1.0）
  - `y`：縦方向（-1.0~1.0）

## BoxFit

- `BoxFit.cover`：親Widgetを埋めるように切り取り
- `BoxFit.contain`：親Wifget内に収まるように縮小
- `BoxFit.fill`：親Widgetに引き延ばす
- `BoxFit.fitWidth`/`BoxFit.fitHeight`：親Widhetの幅／高さに揃える

## BoxDecoration

背景色・角丸・影・グラデーションなどを指定できる

### プロパティ

- [`Color`](#color) `color`：背景色
- [`DecorationImage`](#decorationimage) `image`：背景画像
- [`BoxBorder`](#border) `border`：枠線
- [`BorderRadius`](#borderradius) `borderRadius`：角丸
- `List<BoxShadow>` `boxShadow`：影
- [`Gradient`](#gradient) `gradient`：グラデーション

## TextStyle

### プロパティ

- [`Color`](#color) `color`：色
- `double` `fontSize`：大きさ
- [`FontWeight`](#fontweight) `fontWeight`：太さ
- [`FontStyle`](#fontstyle) `fontStyle`：斜体
- `double` `letterSpacing`：文字間隔
- `double` `wordSpacing`：単語間隔
- [`Textdecoration`](#textdecoration) `decoration`：下線・取消線
- [`Color`](#color) `decorationColor`：下線・取消線の色
- `double` `height`：行間
- [`Color`](#color) `backgroundColor`：文字の背景色
- `String` `fontFamily`：フォントファミリー

## TextEditingController

入力文字列の取得・変更・監視

### プロパティ

- `String` `text`：現在の入力文字列の取得・設定
- [`TextSelection`](#textselection) `selection`：カーソル位置や選択範囲の取得・設定

### メソッド

- `void addListener(VoidCallback listener)`：入力内容の変更を監視を追加
- `void removeListener(VoidCallback listener)`：監視を削除
- `void clear()`：入力内容を空にする

## TextSelection

### プロパティ

- `int` `baseOffset`：選択範囲の開始位置（カーソル位置の左端）
- `int` `extendOffset`：選択範囲の終了位置（カーソル位置の右端）

## Duration

指定した時間だけ、処理や表示が持続する

### プロパティ

- `int` `days`
- `int` `hours`
- `int` `minutes`
- `int` `seconds`
- `int` `milliseconds`
- `int` `microseconds`

## BorderRadius

- `BorderRadius.circular(value)`：全角を均等に丸める
- `BorderRadius.all(Radius.circular(value))`：全角を均等に丸める
- `BorderRadius.only(topLeft: Radius.circular(value), bottomRight(value))`：特定の角だけ丸める
- `BorderRadius.vertical(top: Radius.circular(value))`：上だけ角丸
- `BorderRadius.horizontal(left: circular(value))`：左だけ角丸

## Border

- 