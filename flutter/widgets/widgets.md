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

- 4辺同じ余白：`EdgeInsets.all(value)`
- 横・縦別指定：`EdgeInsets.symmetric(horizontal: x, vertical: y)`
- 個別指定：`EdgeInsets.only(left: l, top; t, right: r, bottom: b)`

## Color

- 公式色：`Colors.blue`
- カスタム：`Color(0xFFRRGGBB)`（16進数）
- 色の濃淡：`Colors.blue.shade200`

## Alignment

- 中央：`Alignment.center`
- 上左／上右：`Alignment.topLeft`/`Alignment.topRight`
- 下左／下右：`Alignment.bottomLeft`/`Alignment.bottomRight`
- 上中央／下中央：`Alignment.topCenter`/`Alignment.bottomCenter`
- 左中央／右中央：`Alignment.centerLeft`/`Alignment.centerRight`

<br>

- x, y座標で微調整：`Alignment(x, y)`
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

- `void addListener(VoidCallback listener)`：監視を追加
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

- 全角：`BorderRadius.circular(value)`
- 全角：`BorderRadius.all(Radius.circular(value))`
- 個別指定：`BorderRadius.only(topLeft: Radius.circular(value), bottomRight(value))`
- 上／下だけ：`BorderRadius.vertical(top: Radius.circular(value))`/`BorderRadius.vertical(bottom: Radius.circular(value))`
- 左／右だけ：`BorderRadius.horizontal(left: circular(value))`/`BorderRadius.horizontal(right: circular(value))`

<br>

### 参照

- [`Radius`](#radius)

## Border

- 全辺：`Border.all(color: Colors.black)`
  - [`Color`](#color) `color`
  - `double` `width`
  - [`BorderStyle`](#borderstyle) `style`
- 縦／横：`Border.symmetric(vertical: BorderSide(color: Colors.red), horizontal: BorderSide(color: Colors.blue),)`
- 個別指定：`Border(left: BorderSide(color: Colors.green),right: BorderSide(color: Colors.red),)`

### 参照

- [`BorderSide`](#borderside)

## BorderSide

### プロパティ

- [`Color`](#color) `color`
- `double` `width`
- [`BorderStyle`](#borderstyle) `style`

## BoxShadow

### プロパティ

- [`Color`](#color) `color`
- `double` `blueRadius`
- [`Offset`](#offset) `offset(dx, dy)`

## Gradient

線形・放射状グラデーションを指定

### プロパティ

- [`[Color, Color, ...]`](#color) `colors`
- [`Alignment`](#alignment) `begin`
- [`Alignment`](#alignment) `end`

## ShapeBorder

### サブクラス

- `RoundedRectangleBorder`：角丸長方形
- `CircleBorder`：円形
- `StadiumBorder`：両端が丸いカプセル型

### プロパティ

- [`BorderRadius`](#borderradius) `borderRadius`
- [`BorderSide`](#borderside) `side`

# enum系

## MainAxisAlignment

主軸方向のWidgetの配置

<br>

- `MainAxisAlignment.center`：中央揃え
- `MainAxisAlignment.start`：軸の先頭に寄せる
- `MainAxisAlignment.end`：軸の末尾に寄せる
- `MainAxisAlignment.spaceBetween`：両端を揃え、均等配置
- `MainAxisAlignment.spaceAround`：均等配置（両端に半分の余白）
- `MainAxisAlignment.spaceEvenly`：完全な均等配置

## CrossAxisAlignment

交差軸方向のWidgetの配置

<br>

- `CrossAxisAlignment.center`：中央揃え
- `CrossAxisAlignment.start`：軸の先頭に寄せる
- `CrossAxisAlignment.end`：軸の末尾に寄せる
- `CrossAxisAlignment.stretch`：最大幅／高さまで伸ばす
- `CrossAxisAlignment.baseline`：テキストのベースラインに揃える（`Row`限定）

## TextDirection

テキストの横並びの方向

<br>

- `TextDirection.ltr`：Left to Right（左から右）
- `TextDirection.rtl`：Right to Left（右から左）

## FlexFit

サイズの埋め方

<br>

- `FlexFit.tight`：できるだけ埋める
- `FlexFit.loose`：子の最小サイズで留める

## StackFit

- `StackFit.loose`：子のサイズを優先し、親のサイズは制約しない
- `StackFit.expand`：子のサイズを親のサイズいっぱいに広げる
- `StackFit.passthrough`：親のサイズ制御なしで、子のサイズそのままにする

## Clip

はみ出しのクリップ方法

<br>

- `Clip.none`：はみ出しても切らない
- `Clip.hardEdge`：はみ出し部分をカット（パフォーマンス重視）
- `ClipantiAlias`：アンチエイリアス付きでカット（見た目重視）
- `Clip.antiAliasWithSaveLayer`：保存レイヤー付きでカット（重いが高品質）

## Axis

- `Axis.vertical`：縦方向スクロール
- `Axis.horizontal`：横方向スクロール

## ScrollPhysics

### サブクラス

- `BouncingScrollPhysics()`：iOS風のバウンス
- `ClampingScrollPhysics()`：Android風のストップ
- `NeverScrollableScrollPhysics()`：スクロール禁止

## TextInputType

入力タイプ

<br>

- `TextInputType.text`：通常の文字
- `TextInputType.number`：数字入力
- `TextInputType.emailAddress`：メール用キーボード
- `TextInputType.phone`：電話番号入力

## BlendMode

- `BlendMode.multiply`：元の色*上塗りの色（暗くなることが多い）
- `BlendMode.overlay`：乗算+スクリーン合成（コントラストが強くなる）

## ImageRepeat

- `ImageRepeat.repeat`
- `ImageRepeat.noRepeat`