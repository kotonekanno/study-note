<details>
<summary>目次</summary>

- [StatelessWidget](#statelesswidget)
  - [Text](#text)
  - [Icon](#icon)
  - [Card](#card)
  - [Material](#material)
  - [Divider](#divider)
  - [CircleAvatar](#circleavatar)
  - [Tooltip](#tooltip)
  - [FloatingActionButton](#floatingactionbutton)
  - [ElevatedButton](#elevatedbutton)
  - [TextButton](#textbutton)
  - [IconButton](#iconbutton)
  - [ListTile](#listtile)
- [StatefulWidget](#statefulwidget)
  - [Scaffold](#scaffold)
  - [AppBar](#appbar)
  - [BottomNavigationBar](#bottomnavigationbar)
  - [Form](#form)
  - [TextField](#textfield)
  - [TextFormField](#textformfield)
  - [CheckBox](#checkbox)
  - [Switch](#switch)
  - [Radio](#radio)
  - [ListView](#listview)
  - [GridView](#gridview)
  - [SingleChildrenScrollView](#singlechildrenscrollview)
  - [ValueListenableBuilder](#valuelistenablebuilder)
- [RenderObjectWidget/SingleRenderObjectWidget](#renderobjectwidgetsinglerenderobjectwidget)
  - [Container](#container)
  - [Padding](#padding)
  - [Center](#center)
  - [Align](#align)
  - [SizedBox](#sizedbox)
  - [Expanded](#expanded)
  - [Flexible](#flexible)
  - [Positioned](#positioned)
  - [Visibility](#visibility)
- [RenderObjectWidget/MultiChildRenderOvjectWidget](#renderobjectwidgetmultichildrenderovjectwidget)
  - [Row](#row)
  - [Column](#column)
  - [Stack](#stack)
  - [Spacer](#spacer)
- [ProxyWidget](#proxywidget)
  - [InheritedWidget](#inheritedwidget)
  - [ParentDataWidget](#parentdatawidget)
- [PrefferedSizeWidget](#prefferedsizewidget)
  - [AppBar(inplements)](#appbarinplements)
- [その他のクラス](#その他のクラス)
  - [Navigator](#navigator)
  - [GestureDetector](#gesturedetector)
  - [StreamBuilder](#streambuilder)
- [非Widgetクラス](#非widgetクラス)
  - [ImageProvider](#imageprovider)
  - [EdgeInsets](#edgeinsets)
  - [Color](#color)
  - [Alignment](#alignment)
  - [BoxFit](#boxfit)
  - [BoxDecoration](#boxdecoration)
  - [TextStyle](#textstyle)
  - [TextEditingController](#texteditingcontroller)
  - [TextSelection](#textselection)
  - [Duration](#duration)
  - [BorderRadius](#borderradius)
  - [Border](#border)
  - [BorderSide](#borderside)
  - [BoxShadow](#boxshadow)
  - [Gradient](#gradient)
  - [ShapeBorder](#shapeborder)
- [enum系](#enum系)
  - [MainAxisAlignment](#mainaxisalignment)
  - [CrossAxisAlignment](#crossaxisalignment)
  - [TextDirection](#textdirection)
  - [FlexFit](#flexfit)
  - [StackFit](#stackfit)
  - [Clip](#clip)
  - [Axis](#axis)
  - [ScrollPhysics](#scrollphysics)
  - [TextInputType](#textinputtype)
  - [BlendMode](#blendmode)
  - [ImageRepeat](#imagerepeat)
- [Generic系](#generic系)

</details>

# StatelessWidget

## Text

- 単一スタイルの文字列を表示

#### プロパティ

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

#### プロパティ

- `IconData` `icon`：表示するアイコン
- `double` `size`：アイコンの大きさ
- [`Color`](#color) `color`：アイコンの色
- `String` `semanticLabel`：アクセシビリティ用の説明テキスト

## Card

- 完成されたのカードUI
- 角丸や影がデフォルトで設定されている

#### プロパティ

- Widget child
- [`Color`](#color) `color`：背景色
- `double` `elevation`：影の高さ
- [`ShapeBorder`](#shapeborder) `shape`：枠の形状
- [`EdgeInets](#edgeinsets) `margin`
- [`Clip`](#clip) `clipBehavior`：はみ出しの処理

## Material

- マテリアルデザインの土台を提供
- `Card`や`InkWell`の動作に必要

#### プロパティ

- Widget child
- [`Color`] `color`：背景色
- `double` `elevation`：影の高さ
- [`ShapeBorder`](#shapeborder) `shape`：枠の形状
- [`BorderRadius`](#borderradius) `borderRadius`：角丸の半径

## Divider

- 水平線で区切る
- リストやセクションの区切りに使う

#### プロパティ

- `double` `height`：余白込みの高さ
- `double` `thickness`：線の太さ
- [`Color`](#color) `color`：線の色
- `double` `indent`：左側の余白
- `double` `endIndent`：右側の余白

## CircleAvatar

- 丸い画像や文字の表示用
- プロフィール写真やユーザーアイコンに使う

#### プロパティ

- `double` `radius`：半径
- [`Color`](#color) `backgroundColor`：背景色
- [`ImageProvider`](#imageprovider) `backgroundImage`：丸い画像を表示
- `Widget` `child`：画像がない場合の代替表示（文字、アイコンなど）

## Tooltip

- マウスホバーや長押しで表示される補助テキストをWidgetに追加
- ボタンやアイコンの説明に使う

#### プロパティ

- `String` `message`：表示するテキスト
- `Widget` `child`
- `double` `height`
- [`EdgeInsetsGeometry`](#edgeinsetsgeometry) `padding`/`margin`
- `bool` `preferBelow`：この下に表示するかどうか
- [`Duration`](#duration) `waitDuration`：表示するまでの待機時間
- [`Duration`](#duration) `showDuration`：表示される時間

## FloatingActionButton

- 画面上に浮かぶ丸いボタン
- [`Scaffold`](#scaffold)の`floatingActionButton`プロパティで配置

#### プロパティ

- `VoidCallback` `onPressed`：タップ時の処理
- `Widget` `child`
- `String` `tooltip`：長押しで表示する説明
- [`Color`](#color) `backgroundColor`：ボタンの背景色
- [`Color`](#color) `foregroundColor`：アイコンや文字の色
- `double` `elevation`：影の高さ
- `bool` `mini`：小さいサイズにするかどうか
- [`ShapeBorder`](#shapeborder) `shape`：ボタンの形状

## ElevatedButton

- 立体感のあるボタン

#### プロパティ

- `void Function()` `onPressed`：押した時の処理
- `Widget` `child`
- [`ButtonStyle`](#buttonstyle) `style`：ボタンのデザイン

## TextButton

- フラット（影なし）のシンプルなボタン

#### プロパティ

- `VoidCallback` `onPressed`：押した時の処理
- `Widget` `child`
- [`ButtonStyle`](#buttonstyle) `style`：ボタンのデザイン

## IconButton

- アイコンのみのボタン
- `AppBar`や`Card`の操作に使う

#### プロパティ

- `void Function()` `onPressed`：押した時の処理
- `Widget` `icon`：表示するアイコン
- `String` `tooltip`：長押し・ホバー時に表示する説明
- [`Color`](#color) `color`：アイコンの色
- `double` `iconSize`：アイコンのサイズ

## ListTile

- 一般的なリストアイテム用
  - 左側：アイコン
  - 中央：タイトル・サブタイトル
  - 右側：操作用ウィジェット
- `ListView`内でよく使う

#### プロパティ

- `Widget` `leading`：左側の表示（アイコン、画像など）
- `Widget` `title`：主タイトル
- `Widget` `subtitle`：サブタイトル
- `Widget` `trailing`：右側の表示（操作用ウィジェット）
- `VoidCallback` `onTap`：タップ時の処理
- `VoidCallback` `onLongPress`：長押し時の処理

# StatefulWidget

## Scaffold

- 画面の基本レイアウトを提供する土台
- `AppBar`, `Body`, `ButtonNavigationBar`などをまとめて管理

#### プロパティ

- [`AppBar`](#appbar) `appBar`：画面上部のバー
- `Widget` `body`：メインの表示領域
- [`BottomNavigateionBar`](#bottomnavigationbar) `bottomNavigationBar`：株のナビゲーションバー
- [`Drawer`](#drawer) `drawer`：横から出てくるメニュー
- [`Color`](#color) `backgroundColor`：背景色

## AppBar

- 画面上部のタイトルバーを提供

#### プロパティ

- `Widget` `title`：タイトル
- `List<Widget>` `actions`：右側に配置（アイコンボタンなど）
- `Widget` `leading`：左側に配置（戻るボタンなど）
- `Color`(#color) `backgroundColor`：背景色
- `double` `elevation`：影の高さ

## BottomNavigationBar

- 画面下部のタブ切り替えナビゲーションバー

#### プロパティ

- [`List<BottomNavigationBarItem>`](#bottomnavigationbaritem) `items`：タブのリスト
- `int` `currentIndex`：選択されているタブの番号
- `void Function(int)` `onTap`：タブが押された時の処理
- [`BottomNavigationBarType`](#bottomnavigationbartype) `type`：固定／シフト表示
- [`Color`](#color) `backgroundColor`：背景色
- [`Color`](#color) `selectedItemColor`：選択中の色
- [`Color`](#color) `unselectedItemColor`：非選択の色

## Form

- 複数の入力フィールドを1つのまとまりとして管理
- バリデーション（入力チェック）に便利

#### プロパティ

- `Widget` `child`：`Column`や`ListView`で複数配置
- `GlobalKey<FormState>` `key`：フォーム全体を管理するキー

## TextField

- ユーザー空文字入力を受け取る
- 拡張版：[`TextFormField`](#textformfield)

#### プロパティ

- [`TextEditingController`](#texteditingcontroller) `controller`：入力内容を管理・取得
- [`InputDecoration`](#inputdecoration) `decoration`：見た目（ラベル、枠、ヒントなど）
- [`TextInputType`](#textinputtype) `keyboardType`：入力タイプ（数字、メールなど）
- `bool` `obscureText`：`true`なら文字を伏せる（パスワード入力）
- `int` `maxLength`：最大文字数
- `bool` `enabled`：入力可否
- `void Function(String)` `onChanged`：入力内容が変わった時の処理

## TextFormField

- 入力欄用
- `TextField`を拡張したフォーム対応版
- バリデーションや状態管理に便利
- フォームの一部として使う場合、[`Form`](#form)と組み合わせる

#### プロパティ

- [`TextEditingCotroller`](#texteditingcontroller) `controller`：入力内容の取得・変更に使うコントローラー
- [`InputDecoration`](#inputdecoration) `decoration`：入力欄の見た目（ラベル、ヒントなど）
- [`TextInputType`](#textinputtype) `keyboardType`：入力するキーボードの種類
- `bool` `obscureText`：`true`で文字を伏せる（パスワード入力）
- `String Function(String)` `validator`：バリデーション関数
- `void Function(String)` `onChanged`：入力内容が変わった時の処理

## CheckBox

- ユーザーのオン／オフ状態を操作する
- チェックボックス

#### プロパティ

- `bool` `value`：チェック状態（`true`でチェック済み）
- `void Function(bool)` `onChanged`：状態変更時の処理
- [`Color`](#color) `activeColor`：チェック時の色
- [`Color`](#color) `checkColor`：チェックマークの色
- `bool` `tristate`：`null`状態を許可するか

## Switch

- ユーザーのオン／オフ状態を操作する
- スライド型トグル

#### プロパティ

- `bool` `value`：オン／オフ状態（`true`でオン）
- `void Function(bool)` `onChanged`：状態変更時の処理
- [`Color`](#color) `activateColor`：オン時の色
- [`Color`](#color) `inactiveThumbColor`：オフ時のつまみの色
- [`Color`](#color) `inactiveTrackColor`：オフ時の背景の色

## Radio<T>

- ユーザーの選択状態を操作する
- ラジオボタン

#### プロパティ

- `T` `value`：このラジオボタンの値
- `T` `groupValue`：グループで選択されている値
- `void Function<T>` `onChanged`：選択時のコールバック
- [`Color`](#color) `activeColor`：選択時の色

## ListView

- 子Widgetを縦／横にスクロール可能なリストとして表示

#### プロパティ

- `List<Widget>` `children`
- [`Axis`](#axis) `scrollDirection`：スクロール方向
- [`EdgeInsets`](#edgeinsets) `padding`：リスト全体の内側余白
- `bool` `reverse`：`true`で逆順に表示
- `bool` `shrinkWrap`：`true`でこのサイズに合わせてリストサイズを縮小
- [`ScrollPhysics`](#scrollphysics) `physics`：スクロールの動き方を制御

## GridView

- 縦横にグリッド表示するスクロール可能なレイアウト

#### プロパティ

- `List<Widget>` `children`
- [`SliverGridDelegate`](#slivergriddelegate) `gridDelegate`：グリッドの列数、比率、勧角などを指定
- [`Axis`](#axis) `scrollDirection`：スクロールの方向
- [`EdgeInsetsGeometry`](#edgeinsetsgeometry) `padding`：グリッド全体の内側余白

## SingleChildrenScrollView

- 子Widgetが親Widgetのサイズを超える場合にスクロールさせる

#### プロパティ

- `Widget` `child`
- [`Axis`](#axis) `scrollDirection`：スクロールの方向
- `bool` `reverse`：`true`で逆順にスクロール
- [`EdgeInsets`](#edgeinsets) `padding`
- [`ScrollPhysics`] `physics`：スクロールの動き方を制御
- [`Clip`](#clip) `clipBehavior`：はみ出し部分の処理

## ValueListenableBuilder<T>

- [`ValueNotifier`](#valuenotifier) `valueListenable`：監視対象のオブジェクト
- `Widget Function(BuildContext, T, Widget)` `builder`：値が変わった時に再描画するWidgetを返す関数
- `Widget` `child`：再描画されない固定部分のWidget

# RenderObjectWidget/SingleRenderObjectWidget

## Container

- サイズ、余白、色、枠線、角丸、影などを付けられる箱
- 子Widgetを1つだけ内包できる

#### プロパティ

- `Widget` `child`
- `double` `width`/`height`
- [`EdgeInsets`](#edgeinsets) `padding`/`margin`
- [`Color`](#color) `color`：背景色
- [`BoxDecoration`](#boxdecoration) `decoration`：装飾全般
- [`Alignment`](#alignment) `alignment`：子Widgetの配置

<br>

- `color`と`decoration`は同時に使えない
- `decoration`を使う場合、`color`は`decoration.color`に統合

## Padding

- 子Widgetに内側余白をつける
- `Container`の`padding`より軽量

#### プロパティ

- [`EdgeInsets`](#edgeinsets) `padding`
- `Widget` `child`

## Center

- 子Widgetを親Widgetの中央に配置する
- `Row`/`Column`内または単独で使える

#### プロパティ

- `Widget` `child`
- `double` `WidthFactor`：親Widgetの幅に対する拡大率
- `double` `heightFactor`：親Widgetの高さに対する拡大率

## Align

- 子を中に並べる

#### プロパティ

- [`AlignmentGeometry`] `alignment`：子Widgetの並べ方
- `Widget` `child`
- `double` `WidthFactor`：子Widgetに対する幅の比率

## SizedBox

- 固定サイズの空間を作る、または子Widgetのサイズを固定
- 縦横のスペーサーとしても使う

#### プロパティ

- `double` `width`
- `double` `height`
- `Widget` `child`

## Expanded

- `Row`/`Column`内でこの幅や高さを柔軟に調整
- 親Widgetの空間を可能な限り埋める
- 参照：[`Flexible`](#flexible)

#### プロパティ

- `int` `flex`：親Widgetの空間を分ける比率を指定
- [`FlexFit`](#flexfit) `fit`：常に`FlexFit.tight`
- `Widget` `child`

## Flexible

- `Row`/`Column`内でこの幅や高さを柔軟に調整
- サイズ調整が自由
- 参照：[`Expanded`](#expanded)

#### プロパティ

- `int` `flex`：親Widgetの空間を分ける比率を指定
- [`FlexFit`](#flexfit) `fit`：サイズの埋め方
- `Widget` `child`

## Positioned

- `Stack`内で絶対位置に子Widgetを配置する
- `Stack`とセットで使うことが前提

#### プロパティ

- `double` `left`/`top`/`right`/`bottom`：左／上／右／下端からの距離
- `double` `width`/`height`：幅／高さを固定
- `Widget` `child`

## Visibility

- Widgetの表示・非表示を切り替える
- レイアウトに残すかどうか制御可能

#### プロパティ

- `bool` `visible`：`true`で表示、`false`で非表示
- `Widget` `replacement`：非表示時に置き換えるWidget
- `bool` `maintainState`：Widgetの状態を保持するか
- `bool` `maintainSize`：レイアウト上のスペースを保持するか
- `bool` `maintainAnimation`：アニメーションを保持するか
- `bool` `maintainSemantics`：アクセシビリティ情報を保持するか
- `bool` `maintainInteractivity`：タッチや操作を保持するか

# RenderObjectWidget/MultiChildRenderOvjectWidget

## Row

- 横方向にWidgetを並べる
- `mainAxis`：横方向
- `crossAxis`：縦方向

#### プロパティ

- `List<Widget>` `children`
- [`MainAxisAlignment`](#mainaxisalignment) `mainAxisAlignment`：主軸方向のWidgetの配置
- [`CrossAxisAlignment`](#crossaxisalignment) `crossAxisAlignment`：交差軸方向のWidgetの配置
- [`MainAxisSize`](#mainaxissize) `mainAxisSize`：
- [`TextDirection`](#textdirection) `textDirection`：横並び方向の制御
- [`VerticalDirection`](#verticaldirection) `verticalDirection`：

## Column

- 横方向にWidgetを並べる
- `mainAxis`：縦方向
- `crossAxis`：横方向

#### プロパティ

- `List<Widget>` `children`
- [`MainAxisAlignment`](#mainaxisalignment) `mainAxisAlignment`：主軸方向のWidgetの配置
- [`CrossAxisAlignment`](#crossaxisalignment) `crossAxisAlignment`：交差軸方向のWidgetの配置
- [`MainAxisSize`](#mainaxissize) `mainAxisSize`：
- [`VerticalDirection`](#verticaldirection) `verticalDirection`：上下の順番制御

## Stack

- 子Widgetを重ねて表示する
- 上下関係や重なり順を制御する

#### プロパティ

- `List<Widget>` `children`
- [`Alignment`](#alignment) `alignment`：この重なり（デフォルトは`topStart`）
- [`StackFit`](#stackfit) `fit`
- [`Clip`](#clip) `clipBehivior`

## Spacer

- `Row`/`Column`内で余白を自動調整する
- `Flexible`と一緒に使うことが多い

#### プロパティ

- `int` `flex`：`Row`/`Column`内の比率

# ProxyWidget

## InheritedWidget

- アプリ全体でデータを共有

## ParentDataWidget

# PrefferedSizeWidget

## AppBar(inplements)

# その他のクラス

## Navigator

- 画面遷移のエンジン
- システムクラス
- 機能
  - 画面のスタック管理
  - 画面間のデータ受け渡し
  - 戻るボタンの制御
  - ルート管理

#### プロパティ

- [`Clip`](#clip) `clipBehavior`：はみ出しの処理
- `String` `initialRoute`：最初に表示するルートの名前
- `List<NavigatorObserver>` `observers`：このナビゲーターのオブザーバーのリスト
- [`DidRemovePageCallback`](#didremovepagecallback) `onDidRemovePage`：ページがナビゲーターから`remove`された時に呼ばれる
- [`RouteListFactory`](#routelistfactory) `onGenerateInitialRoutes`：

## GestureDetector

- タップ・スワイプ・菜蒼紫など、ユーザーのジェスチャーを検知する
- `StatelessWidget`
- 見た目を持たない（子Widgetを包む）
- ボタン以外の場所でもインタラクションを追加できる

#### プロパティ

- `VoidCallback` `onTap`：タップ時に呼ばれる関数
- `VoidCallback` `onDoubleTap`：ダブルタップ時に呼ばれる関数
- `VoidCallback` `onLongPress`：長押し時に呼ばれる関数
- `void Function(DragUpdateDetails)` `onPanUpdate`：ドラッグ時に呼ばれる関数
- `Widget` `child`

#### 参照

- [`DragUpdateDetails`](#deagupdatedetails)

## StreamBuilder

- `Stream`（非同期イベントの流れ）を監視してWidgetを再描画
- `StatefulWidget`
- ネットワークや非同期データ取得に便利

#### プロパティ

- `Stream<T>` `stream`：監視する非同期データの流れ
- `Widget Function(BuildContext, AsyncSnapshot<T>)` `???`：`Stream`の状態に応じたWidgetを返す関数
- `T` `initialData`：最初に表示す値

# 非Widgetクラス

## ImageProvider

画像を提供する

#### サブクラス

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
- `BoxFit.contain`：親Widget内に収まるように縮小
- `BoxFit.fill`：親Widgetに引き延ばす
- `BoxFit.fitWidth`/`BoxFit.fitHeight`：親Widhetの幅／高さに揃える

## BoxDecoration

背景色・角丸・影・グラデーションなどを指定できる

#### プロパティ

- [`Color`](#color) `color`：背景色
- [`DecorationImage`](#decorationimage) `image`：背景画像
- [`BoxBorder`](#border) `border`：枠線
- [`BorderRadius`](#borderradius) `borderRadius`：角丸
- `List<BoxShadow>` `boxShadow`：影
- [`Gradient`](#gradient) `gradient`：グラデーション

## TextStyle

#### プロパティ

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

#### プロパティ

- `String` `text`：現在の入力文字列の取得・設定
- [`TextSelection`](#textselection) `selection`：カーソル位置や選択範囲の取得・設定

#### メソッド

- `void addListener(VoidCallback listener)`：監視を追加
- `void removeListener(VoidCallback listener)`：監視を削除
- `void clear()`：入力内容を空にする

## TextSelection

#### プロパティ

- `int` `baseOffset`：選択範囲の開始位置（カーソル位置の左端）
- `int` `extendOffset`：選択範囲の終了位置（カーソル位置の右端）

## Duration

指定した時間だけ、処理や表示が持続する

#### プロパティ

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

#### 参照

- [`Radius`](#radius)

## Border

- 全辺：`Border.all(color: Colors.black)`
  - [`Color`](#color) `color`
  - `double` `width`
  - [`BorderStyle`](#borderstyle) `style`
- 縦／横：`Border.symmetric(vertical: BorderSide(color: Colors.red), horizontal: BorderSide(color: Colors.blue),)`
- 個別指定：`Border(left: BorderSide(color: Colors.green),right: BorderSide(color: Colors.red),)`

#### 参照

- [`BorderSide`](#borderside)

## BorderSide

#### プロパティ

- [`Color`](#color) `color`
- `double` `width`
- [`BorderStyle`](#borderstyle) `style`

## BoxShadow

#### プロパティ

- [`Color`](#color) `color`
- `double` `blueRadius`
- [`Offset`](#offset) `offset(dx, dy)`

## Gradient

線形・放射状グラデーションを指定

#### プロパティ

- [`[Color, Color, ...]`](#color) `colors`
- [`Alignment`](#alignment) `begin`
- [`Alignment`](#alignment) `end`

## ShapeBorder

#### サブクラス

- `RoundedRectangleBorder`：角丸長方形
- `CircleBorder`：円形
- `StadiumBorder`：両端が丸いカプセル型

#### プロパティ

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
- `FlexFit.loose`：子Widgetの最小サイズで留める

## StackFit

- `StackFit.loose`：子Widgetのサイズを優先し、親Widgetのサイズは制約しない
- `StackFit.expand`：子Widgetのサイズを親Widgetのサイズいっぱいに広げる
- `StackFit.passthrough`：親Widgetのサイズ制御なしで、子Widgetのサイズそのままにする

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

#### サブクラス

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

# Generic系

