<!-- omit in toc -->
# Widget／クラス

<details>
<summary>目次</summary>

- [`StatelessWidget`](#statelesswidget)
  - [`Text`](#text)
  - [`Icon`](#icon)
  - [`Card`](#card)
  - [`Material`](#material)
  - [`Divider`](#divider)
  - [`CircleAvatar`](#circleavatar)
  - [`Tooltip`](#tooltip)
  - [`FloatingActionButton`](#floatingactionbutton)
  - [`ElevatedButton`](#elevatedbutton)
  - [`TextButton`](#textbutton)
  - [`IconButton`](#iconbutton)
  - [`ListTile`](#listtile)
  - [`InkWell`](#inkwell)
  - [`Image`](#image)
  - [`LayoutBuilder`](#layoutbuilder)
- [`StatefulWidget`](#statefulwidget)
  - [`Scaffold`](#scaffold)
  - [`AppBar`](#appbar)
  - [`SliverAppBar`](#sliverappbar)
  - [`BottomNavigationBar`](#bottomnavigationbar)
  - [`Form`](#form)
  - [`TextField`](#textfield)
  - [`TextFormField`](#textformfield)
  - [`CheckBox`](#checkbox)
  - [`Switch`](#switch)
  - [`Radio<T>`](#radiot)
  - [`ListView`](#listview)
  - [`GridView`](#gridview)
  - [`SingleChildScrollView`](#singlechildscrollview)
  - [`StreamBuilder<T>`](#streambuildert)
  - [`ValueListenableBuilder<T>`](#valuelistenablebuildert)
- [`SingleChildRenderObjectWidget`](#singlechildrenderobjectwidget)
  - [`Container`](#container)
  - [`Padding`](#padding)
  - [`Center`](#center)
  - [`Align`](#align)
  - [`SizedBox`](#sizedbox)
  - [`Expanded`](#expanded)
  - [`Flexible`](#flexible)
  - [`Positioned`](#positioned)
  - [`Visibility`](#visibility)
- [`MultiChildRenderObjectWidget`](#multichildrenderobjectwidget)
  - [`Row`](#row)
  - [`Column`](#column)
  - [`Stack`](#stack)
  - [`Spacer`](#spacer)
- [`ProxyWidget`](#proxywidget)
  - [`InheritedWidget`](#inheritedwidget)
  - [`ParentDataWidget`](#parentdatawidget)
- [`PreferredSizeWidget`](#preferredsizewidget)
  - [`AppBar`(inplements)](#appbarinplements)
  - [`PreferredSize`](#preferredsize)
- [値クラス・装飾クラス](#値クラス装飾クラス)
  - [`Color`](#color)
  - [`Colors`](#colors)
  - [`Size`](#size)
  - [`Offset`](#offset)
  - [`Duration`](#duration)
  - [`EdgeInsets`](#edgeinsets)
  - [`Alignment`](#alignment)
  - [`BoxFit`](#boxfit)
  - [`BoxDecoration`](#boxdecoration)
  - [`Border`](#border)
  - [`BorderSide`](#borderside)
  - [`BorderStyle`](#borderstyle)
  - [`BorderRadius`](#borderradius)
  - [`Radius`](#radius)
  - [`DecorationImage`](#decorationimage)
  - [`BoxShadow`](#boxshadow)
  - [`Gradient`](#gradient)
  - [`ShapeBorder`](#shapeborder)
  - [`ImageProvider<T>`](#imageprovidert)
  - [`BlendMode`](#blendmode)
  - [`ImageRepeat`](#imagerepeat)
  - [`VerticalDecoration`](#verticaldecoration)
- [テキスト関連](#テキスト関連)
  - [`TextStyle`](#textstyle)
  - [`FontWeight`](#fontweight)
  - [`FontStyle`](#fontstyle)
  - [`TextDecoration`](#textdecoration)
  - [`TextAlign`](#textalign)
  - [`TextTheme`](#texttheme)
  - [`InputDecoration`](#inputdecoration)
- [入力・コントローラー系](#入力コントローラー系)
  - [`TextEditingController`](#texteditingcontroller)
  - [`TextSelection`](#textselection)
  - [`ScrollPhysics`](#scrollphysics)
  - [`TextInputType`](#textinputtype)
  - [`ValueListenable<T>`](#valuelistenablet)
  - [`ValueNotifier<T>`](#valuenotifiert)
  - [`AsyncSnapshot<T>`](#asyncsnapshott)
  - [`State<T>`](#statet)
- [レイアウト制御用enum](#レイアウト制御用enum)
  - [`MainAxisAlignment`](#mainaxisalignment)
  - [`CrossAxisAlignment`](#crossaxisalignment)
  - [`MainAxisSize`](#mainaxissize)
  - [`FlexFit`](#flexfit)
  - [`StackFit`](#stackfit)
  - [`Axis`](#axis)
  - [`Clip`](#clip)
  - [`TextDirection`](#textdirection)
  - [`Curves`](#curves)
- [Material/Theme系](#materialtheme系)
  - [`Theme`](#theme)
  - [`ThemeData`](#themedata)
  - [`AppBarTheme`](#appbartheme)
  - [`CardTheme`](#cardtheme)
  - [`VisualDencity`](#visualdencity)
  - [`ButtonStyle`](#buttonstyle)
  - [`ButtonStyleFrom`](#buttonstylefrom)
  - [`styleFrom`](#stylefrom)
  - [`MaterialStateProperty<T>`](#materialstatepropertyt)
  - [`MaterialState`](#materialstate)
  - [`MaterialApp`](#materialapp)
  - [`NavigationDestination`](#navigationdestination)
  - [`MediaQuery`](#mediaquery)
  - [`ColorScheme`](#colorscheme)
- [Navigator/ジェスチャー関連](#navigatorジェスチャー関連)
  - [`Navigator`](#navigator)
  - [`GestureDetector`](#gesturedetector)
  - [`DragUpdateDetails`](#dragupdatedetails)
- [Sliver/Delegate系](#sliverdelegate系)
  - [`SliverGridDelegate`](#slivergriddelegate)
    - [`SliverGridDelegateWithFixedCrossAxisCount`](#slivergriddelegatewithfixedcrossaxiscount)
    - [`SliverGridDelegateWithMaxCrossAxisExtent`](#slivergriddelegatewithmaxcrossaxisextent)
- [BottomNavigation系](#bottomnavigation系)
  - [`BottomNavigationBarType`](#bottomnavigationbartype)
  - [`BottomNavigationBarItem`](#bottomnavigationbaritem)
- [未分類](#未分類)
  - [`RoundedRectangleBorder`](#roundedrectangleborder)
  - [`Brightness`](#brightness)
  - [`TextOverFlow`](#textoverflow)
  - [`EdgeInsetsGeometry`](#edgeinsetsgeometry)
  - [`EdgeInsetsDirectional`](#edgeinsetsdirectional)
  - [`AlignmentGeometry`](#alignmentgeometry)
  - [`BoxConstraints`](#boxconstraints)
  - [`showModalBottomSheet`](#showmodalbottomsheet)

</details>

# `StatelessWidget`

状態を持たないWidget

#### 基本構文

```dart
class クラス名 extends StatelessWidget {
  // 1. プロパティの宣言
  final 型 プロパティ名1;
  final 型 プロパティ名2;
  // ...

  // 2. コンストラクタ
  クラス名({
    required this.プロパティ名1,
    required this.プロパティ名2,
    // ...
  });

  // 3. buildメソッド（必須）
  @override
  Widget build(BuildContext context) {
    return 何らかのWidget;  // ← ここが必ずreturn
  }
}
```

- `build`メソッド：Widgetを作って返す関数

## `Text`

- 単一スタイルの文字列を表示

#### プロパティ

- `String` `data`：表示するテキスト
- [`TextStyle`](#textstyle) `style`
- [`TextAlign`](#textalign) `textAlign`
- [`TextOverflow`](#textoverflow) `overflow`
- `int` `maxLines`：行数の最大値
- `bool` `softWrap`：テキストがWidget幅を超えるときに自動で折り返すかどうか
  - `true`（デフォルト）：改行する
  - `false`：改行しない
- `double` `textScaleFactor`：ユーザーが端末の設定で変更した文字の大きさを反映させる
  - `1.0`：標準
  - `1.2`：少し大きめ

## `Icon`

アイコン表示

#### プロパティ

- `IconData` `icon`：表示するアイコン
- `double` `size`：アイコンの大きさ
- [`Color`](#color) `color`：アイコンの色
- `String` `semanticLabel`：アクセシビリティ用の説明テキスト

#### 値

参照：<a herf="https://api.flutter.dev/flutter/material/Icons-class.html" target="_blank" rel="noopener noreferrer">https://api.flutter.dev/flutter/material/Icons-class.html</a>

<br>

- `Icons.home`：ホームアイコン
- `Icons.search`：検索アイコン
- `Icons.add`：プラスアイコン
- `Icons.arrow_back`：戻るアイコン
- `Icons.adaptive.arrow_back`：プラットフォーム適応

## `Card`

- 完成されたのカードUI
- 角丸や影がデフォルトで設定されている

#### プロパティ

- Widget child
- [`Color`](#color) `color`：背景色
- `double` `elevation`：影の高さ
- [`ShapeBorder`](#shapeborder) `shape`：枠の形状
- [`EdgeInets`](#edgeinsets) `margin`
- [`Clip`](#clip) `clipBehavior`：はみ出しの処理

## `Material`

- マテリアルデザインの土台を提供
- `Card`や`InkWell`の動作に必要

#### プロパティ

- Widget child
- [`Color`](#color) `color`：背景色
- `double` `elevation`：影の高さ
- [`ShapeBorder`](#shapeborder) `shape`：枠の形状
- [`BorderRadius`](#borderradius) `borderRadius`：角丸の半径

## `Divider`

- 水平線で区切る
- リストやセクションの区切りに使う

#### プロパティ

- `double` `height`：余白込みの高さ
- `double` `thickness`：線の太さ
- [`Color`](#color) `color`：線の色
- `double` `indent`：左側の余白
- `double` `endIndent`：右側の余白

## `CircleAvatar`

- 丸い画像や文字の表示用
- プロフィール写真やユーザーアイコンに使う

#### プロパティ

- `double` `radius`：半径
- [`Color`](#color) `backgroundColor`：背景色
- [`ImageProvider<T>`](#imageprovidert) `backgroundImage`：丸い画像を表示
- `Widget` `child`：画像がない場合の代替表示（文字、アイコンなど）

## `Tooltip`

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

## `FloatingActionButton`

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

## `ElevatedButton`

立体感のあるボタン

#### プロパティ

- `void Function()` `onPressed`：押した時の処理
- `Widget` `child`
- [`ButtonStyle`](#buttonstyle) `style`：ボタンのデザイン
- [`Color`](#color) `backgroundColor`：背景色
- [`Color`](#color) `foregroundColor`：テキスト色
- `double` `elevation`：影の高さ
- [`RoundedRectangleBorder`](#roundedrectangleborder) `shape`：形状
- [`EdgeInsets`](#edgeinsets) `padding`：内側余白
- [`Size`](#size) `minimumSize`：最小サイズ

## `TextButton`

フラット（影なし）のシンプルなボタン

#### プロパティ

- `VoidCallback` `onPressed`：押した時の処理
- `Widget` `child`
- [`ButtonStyle`](#buttonstyle) `style`：ボタンのデザイン

#### メソッド

- `TextButton.styleFrom(...)`
  - [`styleFrom`](#stylefrom)

## `IconButton`

- アイコンのみのボタン
- `AppBar`や`Card`の操作に使う

#### プロパティ

- `void Function()` `onPressed`：押した時の処理
- `Widget` `icon`：表示するアイコン
- `String` `tooltip`：長押し・ホバー時に表示する説明
- [`Color`](#color) `color`：アイコンの色
- `double` `iconSize`：アイコンのサイズ

#### メソッド

- IconButton.styleFrom(...)
  - [`styleFrom`](#stylefrom)

## `ListTile`

- 一般的なリストアイテム用
  - 左側：アイコン
  - 中央：タイトル・サブタイトル
  - 右側：操作用Widget
- `ListView`内でよく使う

#### プロパティ

- `Widget` `leading`：左側の表示（アイコン、画像など）
- `Widget` `title`：主タイトル
- `Widget` `subtitle`：サブタイトル
- `Widget` `trailing`：右側の表示（操作用Widget）
- `VoidCallback` `onTap`：タップ時の処理
- `VoidCallback` `onLongPress`：長押し時の処理

## `InkWell`

- タップ時に水の波紋（Ink Ripple）を表示する
- `GestureDetector`と異なり、見た目に波紋エフェクトが出る

#### プロパティ

- `Widget` `child`：タップ可能にする子Widget
- `void Function()` `onTap`：タップ時の処理
- `void Function()` `onLongPress`：長押し時の処理
- [`BorderRadius`](#borderradius) `borderRadius`：波紋の角丸
- [`Color`](#color) `splashColor`：波紋の色
- [`Color`](#color) `highlightColor`：タップ時の強調色

## `Image`

- 画像を表示
- ネットワーク画像、アセット画像、メモリやファイルからの画像に対応

#### コンストラクタ

- `Image.asset('assets/images/logo.png', ...)`：
  - アセット画像（プロジェクト内）
  - `public.yaml`で登録が必要
- `Image.network('https://example.com/image.png', ...)`：ネットワーク画像
- `Image.file(File('/path/to/image.png'))`：デバイスのファイル
- `Image.memory(bytes)`：メモリ上のバイトデータ

#### プロパティ

- `double` `width`/`height`
- [`BoxFit`](#boxfit) `fit`
- [`AlignmentGeometry`](#alignmentgeometry) `alignment`
- [`Color`](#color) `color`：画像に色を重ねる場合
- [`BlendMode`](#blendmode) `colorBlendMode`
- [`ImageRepeat`](#imagerepeat) `repeat`
- `bool` `gaplessPlayback`：`true`でリロード時のちらつきを防ぐ

## `LayoutBuilder`

- 親Widgetの`constraints`（制約）を取得して、それに応じたWidgetを構築
- 画面サイズや親Wigetのサイズに応じてレイアウトを切り替えるときに使う
- `constraints`：親Widgetから渡される、サイズの上限・下限情報

#### 基本構文

```dart
LayoutBuilder(
  builder: (BuildContext context, BoxConstraints constraints) {
    // constraints.maxWidth / maxHeight などを見てWidgetを返す
    return Widget();
  },
)
```

#### プロパティ

- `Widget Function(BuildContext, BoxConstraints)` `builder`：`constraints`を見てWidgetを作る
  - `BuildContext` `context`：Widgetツリーの現在位置
  - [`BoxConstraints`](#boxconstraints) `constraints`：親Widgetから渡されたサイズ制約

#### `constraints`のメソッド

- `constraints.maxWidth`/`constraints.maxHeight`
- `constraints.minWidth`/`constraints.minHeight`
- `constraints.hasBoundedWidth`：幅が有限かどうか
- `constraints.hasBoundedHeight`：高さが有限かどうか

# `StatefulWidget`

- ユーザー操作や非同期処理などで変化するデータを持つWidget
- 画面更新の仕組みの一つで、状態を持つ

#### 基本的な流れ

1. 変数を書き換える
2. `setState`を呼ぶ
3. 呼ばれた`StatefulWidget`は変数の変更を知る

#### メソッド

- `setState()`：
  - 自分の子Widgetを任意のタイミングで再レイアウト・再描画する機能
  - `setState`を呼ぶ時に画面表示に使われれる情報の一部を書き換えておくと、画面もその情報に書き換わる
- `createState()`：
  ```dart
  _MyApp createState() => _MyApp();
  ```
  - `State`インスタンスを生成するメソッド
  - FlutterがWidgetをツリーに追加する時に呼ばれる
  - このWidget用の状態管理クラス（`_MyApp`）を作るという意味
  - `_MyApp`の中で`build()`メソッドを書き、ユーザー操作やデータの変化に応じて画面を更新する

## `Scaffold`

- 画面の基本レイアウトを提供する土台
- `AppBar`, `Body`, `ButtonNavigationBar`などをまとめて管理

#### プロパティ

- [`AppBar`](#appbar) `appBar`：画面上部のバー
- `Widget` `body`：メインの表示領域
- [`BottomNavigateionBar`](#bottomnavigationbar) `bottomNavigationBar`：下部のナビゲーションバー
- [`Drawer`](#drawer) `drawer`：横から出てくるメニュー
- [`Color`](#color) `backgroundColor`：背景色

## `AppBar`

画面上部のタイトルバーを提供

#### プロパティ

- `Widget` `title`：タイトル
- `List<Widget>` `actions`：右側に配置（アイコンボタンなど）
- `Widget` `leading`：左側に配置（戻るボタンなど）
- [`Color`](#color) `backgroundColor`：背景色
- `double` `elevation`：影の高さ

## `SliverAppBar`

- `AppBar`の拡張版
- スクロール可能領域専用のヘッダー（[`CustomScrollView`](#customscrollview)）
- スクロールに応じて、伸縮・固定・消える・出るなどの動作ができる
- `flexibleSpace`を使って自由なレイアウトを配置できる

#### プロパティ

- `Widget` `title`
- `double` `expandedHeight`：最大展開時の高さ
- `double` `collapsedHeight`：閉じた時の高さ
- `bool` `pinned`：スクロールしても上部に固定するかどうか
- `bool` `floating`：下からスクロールした時即座に表示するかどうか
- `bool` `snap`：`true`の時スナップ表示する（スクロールを止めると自動的に開閉）
- `Widget` `flexibleSpace`：展開部分に表示する自由なレイアウト
- [`Color`](#color) `backgroundColor`

## `BottomNavigationBar`

画面下部のタブ切り替えナビゲーションバー

#### プロパティ

- [`List<BottomNavigationBarItem>`](#bottomnavigationbaritem) `items`：タブのリスト
- `int` `currentIndex`：選択されているタブの番号
- `void Function(int)` `onTap`：タブが押された時の処理
- [`BottomNavigationBarType`](#bottomnavigationbartype) `type`：固定／シフト表示
- [`Color`](#color) `backgroundColor`：背景色
- [`Color`](#color) `selectedItemColor`：選択中の色
- [`Color`](#color) `unselectedItemColor`：非選択の色

## `Form`

- 複数の入力フィールドを1つのまとまりとして管理
- バリデーション（入力チェック）に便利

#### プロパティ

- `Widget` `child`：`Column`や`ListView`で複数配置
- `GlobalKey<FormState>` `key`：フォーム全体を管理するキー

## `TextField`

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

## `TextFormField`

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

## `CheckBox`

- ユーザーのオン／オフ状態を操作する
- チェックボックス

#### プロパティ

- `bool` `value`：チェック状態（`true`でチェック済み）
- `void Function(bool)` `onChanged`：状態変更時の処理
- [`Color`](#color) `activeColor`：チェック時の色
- [`Color`](#color) `checkColor`：チェックマークの色
- `bool` `tristate`：`null`状態を許可するか

## `Switch`

- ユーザーのオン／オフ状態を操作する
- スライド型トグル

#### プロパティ

- `bool` `value`：オン／オフ状態（`true`でオン）
- `void Function(bool)` `onChanged`：状態変更時の処理
- [`Color`](#color) `activateColor`：オン時の色
- [`Color`](#color) `inactiveThumbColor`：オフ時のつまみの色
- [`Color`](#color) `inactiveTrackColor`：オフ時の背景の色

## `Radio<T>`

- ユーザーの選択状態を操作する
- ラジオボタン

#### プロパティ

- `T` `value`：このラジオボタンの値
- `T` `groupValue`：グループで選択されている値
- `void Function<T>` `onChanged`：選択時のコールバック
- [`Color`](#color) `activeColor`：選択時の色

## `ListView`

- 子Widgetを縦／横にスクロール可能なリストとして表示

#### プロパティ

- `List<Widget>` `children`
- [`Axis`](#axis) `scrollDirection`：スクロール方向
- [`EdgeInsets`](#edgeinsets) `padding`：リスト全体の内側余白
- `bool` `reverse`：`true`で逆順に表示
- `bool` `shrinkWrap`：`true`でこのサイズに合わせてリストサイズを縮小
- [`ScrollPhysics`](#scrollphysics) `physics`：スクロールの動き方を制御

## `GridView`

- 縦横にグリッド表示するスクロール可能なレイアウト

#### プロパティ

- `List<Widget>` `children`
- [`SliverGridDelegate`](#slivergriddelegate) `gridDelegate`：グリッドの列数、比率、勧角などを指定
- [`Axis`](#axis) `scrollDirection`：スクロールの方向
- [`EdgeInsetsGeometry`](#edgeinsetsgeometry) `padding`：グリッド全体の内側余白

## `SingleChildScrollView`

- 子Widgetが親Widgetのサイズを超える場合にスクロールさせる

#### プロパティ

- `Widget` `child`
- [`Axis`](#axis) `scrollDirection`：スクロールの方向
- `bool` `reverse`：`true`で逆順にスクロール
- [`EdgeInsets`](#edgeinsets) `padding`
- [`ScrollPhysics`](#scrollphysics) `physics`：スクロールの動き方を制御
- [`Clip`](#clip) `clipBehavior`：はみ出し部分の処理

## `StreamBuilder<T>`

- `Stream`（非同期イベントの流れ）を監視してWidgetを再描画
- `StatefulWidget`
- ネットワークや非同期データ取得に便利

#### プロパティ

- `Stream<T>` `stream`：監視する非同期データの流れ
- `Widget Function(BuildContext, AsyncSnapshot<T>)` `???`：`Stream`の状態に応じたWidgetを返す関数
- `T` `initialData`：最初に表示す値

## `ValueListenableBuilder<T>`

- [`ValueNotifier<T>`](#valuenotifiert) `valueListenable`：監視対象のオブジェクト
- `Widget Function(BuildContext, T, Widget)` `builder`：値が変わった時に再描画するWidgetを返す関数
- `Widget` `child`：再描画されない固定部分のWidget

# `SingleChildRenderObjectWidget`

実際に画面の描画する低レベルなWidget

## `Container`

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

## `Padding`

- 子Widgetに内側余白をつける
- `Container`の`padding`より軽量

#### プロパティ

- [`EdgeInsets`](#edgeinsets) `padding`
- `Widget` `child`

## `Center`

- 子Widgetを親Widgetの中央に配置する
- `Row`/`Column`内または単独で使える

#### プロパティ

- `Widget` `child`
- `double` `WidthFactor`：子Widgetの幅*数値=親要素の幅
- `double` `heightFactor`：子Widgetの高さ*数値=親要素の幅

## `Align`

- 子を中に並べる

#### プロパティ

- [`AlignmentGeometry`](#alignmentgeometry) `alignment`：子Widgetの並べ方
- `Widget` `child`
- `double` `WidthFactor`：子Widgetの幅*数値=親要素の幅

## `SizedBox`

- 固定サイズの空間を作る、または子Widgetのサイズを固定
- 縦横のスペーサーとしても使う

#### プロパティ

- `double` `width`
- `double` `height`
- `Widget` `child`

#### コンストラクタ

- `SizedBox.shrink()`：最小サイズ
- `SizedBox.expand()`：最大サイズ
- `SizedBox.square(50)`：正方形
- `SizedBox.fromSize(Size(100, 50))`：サイズ指定

## `Expanded`

- `Row`/`Column`内でこの幅や高さを柔軟に調整
- 親Widgetの空間を可能な限り埋める
- 参照：[`Flexible`](#flexible)

#### プロパティ

- `int` `flex`：親Widgetの空間を分ける比率を指定
- [`FlexFit`](#flexfit) `fit`：常に`FlexFit.tight`
- `Widget` `child`

## `Flexible`

- `Row`/`Column`内でこの幅や高さを柔軟に調整
- サイズ調整が自由
- 参照：[`Expanded`](#expanded)

#### プロパティ

- `int` `flex`：親Widgetの空間を分ける比率を指定
- [`FlexFit`](#flexfit) `fit`：サイズの埋め方
- `Widget` `child`

## `Positioned`

- `Stack`内で絶対位置に子Widgetを配置する
- `Stack`とセットで使うことが前提

#### プロパティ

- `double` `left`/`top`/`right`/`bottom`：左／上／右／下端からの距離
- `double` `width`/`height`：幅／高さを固定
- `Widget` `child`

## `Visibility`

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

# `MultiChildRenderObjectWidget`

実際に画面の描画する低レベルなWidget

## `Row`

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

## `Column`

- 横方向にWidgetを並べる
- `mainAxis`：縦方向
- `crossAxis`：横方向

#### プロパティ

- `List<Widget>` `children`
- [`MainAxisAlignment`](#mainaxisalignment) `mainAxisAlignment`：主軸方向のWidgetの配置
- [`CrossAxisAlignment`](#crossaxisalignment) `crossAxisAlignment`：交差軸方向のWidgetの配置
- [`MainAxisSize`](#mainaxissize) `mainAxisSize`：
- [`VerticalDirection`](#verticaldirection) `verticalDirection`：上下の順番制御

## `Stack`

- 子Widgetを重ねて表示する
- 上下関係や重なり順を制御する

#### プロパティ

- `List<Widget>` `children`
- [`Alignment`](#alignment) `alignment`：この重なり（デフォルトは`topStart`）
- [`StackFit`](#stackfit) `fit`
- [`Clip`](#clip) `clipBehivior`

## `Spacer`

- `Row`/`Column`内で余白を自動調整する
- `Flexible`と一緒に使うことが多い

#### プロパティ

- `int` `flex`：`Row`/`Column`内の比率

# `ProxyWidget`

他のWidgetをラップして機能を追加

## `InheritedWidget`

アプリ全体でデータを共有

## `ParentDataWidget`

# `PreferredSizeWidget`

## `AppBar`(inplements)

## `PreferredSize`

- 子Widgetに希望するサイズを教えるラッパーWidget
- [`PreferredSizeWidget`](#preferredsizewidget)を期待する場所で指定する
- このサイズに合わせて`AppBar`などのサイズを決めたいときに使う

#### プロパティ

- [`Size`](#size) `preferredSize`
- `Widget` `child`

# 値クラス・装飾クラス

## `Color`

#### 値

- `Colors.blue`：公式色
  - [`Colors`](#colors)
  - 色の濃淡：`Colors.blue.shade200`
- `Color(0xFFRRGGBB)`：カスタム（16進数）

#### メソッド

- `Color.fromARGB(255, 100, 150, 200)`：ARGB値から 
- `Color.fromRGBO(100, 150, 200, 0.8)`：RGBA値から

## `Colors`

#### 値

- `Colors.<color>`：指定された単色
- `Colors.transparent`：透明色
- `Colors.<color><opacity>`：濃淡
  - `opacity`：0〜100の段階的な不透明度
  - 例：`Colors.black87`, `Colors.white54`
- `Colors.<color>.shade<100-900>`：明度
  - `shade<100-900>`：数値が大きいほど暗い
  - 例：`Colors.red.shade.100`, `Colors.red.shade900`
- `Colors.lerp(Color a, Color b, double t)`：中間色
  - `a`と`b`の間の色を補完
  - `t`：0.0〜1.0
  - 例：`Colors.lerp(Colors.red, Colors.blue, 0.5)`

## `Size`

## `Offset`

2次元座標やベクトルを表す

#### プロパティ

- `double` `dx`：x軸方向の距離
- `double` `dy`：y軸方向の距離

## `Duration`

指定した時間だけ、処理や表示が持続する

#### プロパティ

- `int` `days`
- `int` `hours`
- `int` `minutes`
- `int` `seconds`
- `int` `milliseconds`
- `int` `microseconds`

## `EdgeInsets`

余白設定

#### コンストラクタ

- 4辺同じ余白：`EdgeInsets.all(value)`
- 横・縦別指定：`EdgeInsets.symmetric(horizontal: x, vertical: y)`
- 個別指定：`EdgeInsets.only(left: l, top; t, right: r, bottom: b)`
- LTBE順に指定：`EdgeInsets.fromLTRB(left: l, top; t, right: r, bottom: b)`
- 余白なし：`EdgeInsets.zero`

## `Alignment`

- `Alignment.center`：中央
- `Alignment.topLeft`/`Alignment.topRight`：上左／上右
- `Alignment.bottomLeft`/`Alignment.bottomRight`：下左／下右
- `Alignment.topCenter`/`Alignment.bottomCenter`：上中央／下中央
- `Alignment.centerLeft`/`Alignment.centerRight`：左中央／右中央
- `Alignment(x, y)`：座標指定
  - `x`：横方向（-1.0~1.0）
  - `y`：縦方向（-1.0~1.0）

## `BoxFit`

- `BoxFit.cover`：親Widgetを埋めるように切り取り
- `BoxFit.contain`：親Widget内に収まるように縮小
- `BoxFit.fill`：親Widgetに引き延ばす
- `BoxFit.fitWidth`/`BoxFit.fitHeight`：親Widhetの幅／高さに揃える

## `BoxDecoration`

背景色・角丸・影・グラデーションなどを指定できる

#### プロパティ

- [`Color`](#color) `color`：背景色
- [`DecorationImage`](#decorationimage) `image`：背景画像
- [`BoxBorder`](#border) `border`：枠線
- [`BorderRadius`](#borderradius) `borderRadius`：角丸
- `List<BoxShadow>` `boxShadow`：影
- [`Gradient`](#gradient) `gradient`：グラデーション

## `Border`

- 全辺：`Border.all(color: Colors.black)`
  - [`Color`](#color) `color`
  - `double` `width`
  - [`BorderStyle`](#borderstyle) `style`
- 縦／横：`Border.symmetric(vertical: BorderSide(color: Colors.red), horizontal: BorderSide(color: Colors.blue),)`
- 個別指定：`Border(left: BorderSide(color: Colors.green),right: BorderSide(color: Colors.red),)`

#### 参照

- [`BorderSide`](#borderside)

## `BorderSide`

線の設定（色、太さ、種類など）

#### プロパティ

- [`Color`](#color) `color`
- `double` `width`
- [`BorderStyle`](#borderstyle) `style`
- `double` `strokeAlign`：線の位置調整

## `BorderStyle`

#### 値

- `solid`：実線
- `none`：線なし（透明）

## `BorderRadius`

#### コンストラクタ

- 全角：`BorderRadius.circular(value)`
- 全角：`BorderRadius.all(Radius.circular(value))`
- 個別指定：`BorderRadius.only(topLeft: Radius.circular(value), bottomRight(value))`
- 上／下だけ：`BorderRadius.vertical(top: Radius.circular(value))`/`BorderRadius.vertical(bottom: Radius.circular(value))`
- 左／右だけ：`BorderRadius.horizontal(left: circular(value))`/`BorderRadius.horizontal(right: circular(value))`

#### 参照

- [`Radius`](#radius)

## `Radius`

## `DecorationImage`

背景画像を指定

#### プロパティ

- [`ImageProvider<T>`](#imageprovidert) `image`
- [`BoxFit`](#boxfit) `fit`

## `BoxShadow`

#### プロパティ

- [`Color`](#color) `color`
- `double` `blueRadius`
- [`Offset`](#offset) `offset(dx, dy)`

## `Gradient`

線形・放射状グラデーションを指定

#### プロパティ

- [`[Color, Color, ...]`](#color) `colors`
- [`Alignment`](#alignment) `begin`
- [`Alignment`](#alignment) `end`

## `ShapeBorder`

#### サブクラス

- `RoundedRectangleBorder`：角丸長方形
- `CircleBorder`：円形
- `StadiumBorder`：両端が丸いカプセル型

## `ImageProvider<T>`

画像を提供する

#### サブクラス

- `AssetImage(name)`：アプリに含まれる画像
  - `name`：画像のパス
- `NetworkImage(url)`：ネットワーク上の画像
  - `url`：画像のURL
- `FileImage(file)`：デバイス上のファイル
  - `file`：`File`オブジェクト

## `BlendMode`

#### 値

- `BlendMode.multiply`：元の色*上塗りの色（暗くなることが多い）
- `BlendMode.overlay`：乗算+スクリーン合成（コントラストが強くなる）

## `ImageRepeat`

#### 値

- `ImageRepeat.repeat`
- `ImageRepeat.noRepeat`

## `VerticalDecoration`

`Column`で縦の並びの順番を制御

#### 値

- `VerticalDecoration.down`：上から下
- `VerticalDecoration.up`：下から上

# テキスト関連

## `TextStyle`

#### プロパティ

- [`Color`](#color) `color`：テキスト色
- `double` `fontSize`：大きさ
- [`FontWeight`](#fontweight) `fontWeight`：太さ
- [`FontStyle`](#fontstyle) `fontStyle`：斜体
- `double` `letterSpacing`：文字間隔
- `double` `wordSpacing`：単語間隔
- [`TextDecoration`](#textdecoration) `decoration`：下線・取消線
- [`Color`](#color) `decorationColor`：下線・取消線の色
- `double` `height`：*フォントサイズで、行間
- [`Color`](#color) `backgroundColor`：文字の背景色
- `String` `fontFamily`：フォントファミリー

#### メソッド

- `TextStyle.lerp(style1, style2, t)`：`style1`と`style2`の中間
  - `t`：0〜1の値
- `TextStyle(fontSize: 16).copyWith(...)`：既存スタイルをコピー
- `TextStyle.inherit`：`true`（デフォルト）の時、[`DefaultTextStyle`](#defaulttextstyle)と`style`引数の統合になる

## `FontWeight`

#### 値

- `FontWeight.normal`：標準（400）
- `FontWeight.bold`：太字（700）
- `FontWeight.w<100-900>`：数値で指定（100刻み）

## `FontStyle`

#### 値

- `FontStyle.normal`：標準
- `FontStyle.italic`：斜体

## `TextDecoration`

#### 値

- `TextDecoration.none`：なし
- `TextDecoration.underline`：下線
- `TextDecoration.lineThrough`：取消線

## `TextAlign`

#### 値

- `TextAlign.center`：中央揃え
- `TextAlign.left`：左揃え
- `TextAlign.right`：右揃え
- `TextAlign.justify`：両端揃え

## `TextTheme`

#### プロパティ

型はすべて[`TextStyle`](#textstyle)

<br>

- Display系：`displayLarge`/`displayMedium`/`displaySmall`）
  - 見出し・キャッチコピーなど、画面を埋めるような大きな文字
- Headeline系：`headlineLarge`/`headlineMedium`/`headlineSmall`
  - セクションの見出しに使う、やや大きめの文字
- Title系：`titleLarge`/`titleMedium`/`titleSmall`
  - タイトルやカードの見出しなど、中サイズの文字
- Body系：`bodyLarge`/`bodyMedium`/`bodySmall`
  - 本文に使う標準的な文字
- Label系：`labelLarge`/`labelMedium`/`labelSmall`
  - ボタンや小さなラベル、キャプション用の文字

## `InputDecoration`

入力フィールドの見た目（ラベル、枠、ヒントなど）

#### プロパティ

- `String` `labelText`：フィールド上のラベル
- `String` `hintText`：入力前のヒント
- [`OutlinedInputBorder`](#outlinedinputborder) `border`：枠を追加
- [`Icon`](#icon) `prefixIcon`：入力欄の左にアイコン
- [`Icon`](#icon) `suffixIcon`：入力欄の右にアイコン

#### メソッド

- `InputDecoration.collapsed(...)`
  - `String` `hintText`

# 入力・コントローラー系

## `TextEditingController`

入力文字列の取得・変更・監視

#### プロパティ

- `String` `text`：現在の入力文字列の取得・設定
- [`TextSelection`](#textselection) `selection`：カーソル位置や選択範囲の取得・設定

#### メソッド

- `void addListener(VoidCallback listener)`：監視を追加
- `void removeListener(VoidCallback listener)`：監視を削除
- `void clear()`：入力内容を空にする

## `TextSelection`

#### プロパティ

- `int` `baseOffset`：選択範囲の開始位置（カーソル位置の左端）
- `int` `extendOffset`：選択範囲の終了位置（カーソル位置の右端）

#### プロパティ

- [`BorderRadius`](#borderradius) `borderRadius`
- [`BorderSide`](#borderside) `side`

## `ScrollPhysics`

#### サブクラス

- `BouncingScrollPhysics()`：iOS風のバウンス
- `ClampingScrollPhysics()`：Android風のストップ
- `NeverScrollableScrollPhysics()`：スクロール禁止

## `TextInputType`

入力タイプ

#### 値

- `TextInputType.text`：通常の文字
- `TextInputType.number`：数字
- `TextInputType.emailAddress`：メール
- `TextInputType.phone`：電話番号
- `TextInputType.url`：URL

## `ValueListenable<T>`

- 値の変化を監視できる
- 主にサブクラス[`ValueNotifier<T>`](#valuenotifiert)が使われる

## `ValueNotifier<T>`

- 状態を持つ箱
- その値が変わると通知を送ってUIを再描画する
- [~valueListenableBuilder`](#valuelistenablebuildert)などからUIで使える

<br>

- `setState`を使わずにUIを更新できる
- 小規模の状態管理に便利
- `Provider`や`Riverpod`よりシンプルで軽量

#### メソッド

- `value`：現在の値にアクセス
- `value = newValue;`：値を更新するとリスナーに通知される
- `addListener`：リスナー追加
- `removeListener`：リスナー削除

## `AsyncSnapshot<T>`

`Stream`の現在状態を表す

#### プロパティ

- `T` `data`：`Stream`の現在状態を表す
- `Object` `error`：エラー情報
- [`ConnectionState`](#connectionstate)：接続状態
  - `waiting`：待機中
  - `active`：データ到着中
  - `done`：完了

## `State<T>`

- `StatefulWidget`の状態（データ）とUI更新のロジックを持つクラス
- `T`：`StatefulWidget`を継承したクラス
- Widget自体は不変で、状態の変化は`State`が担当

#### 基本構文

```dart
class MyWidget extends StatefulWidget {
  const MyWidget({super.key});

  @override
  _MyWidgetState createState() => _MyWidgetState();
}

class _MyWidgetState extends State<MyWidget> {
  int counter = 0; // 状態を持つ

  @override
  Widget build(BuildContext context) {
    return Column(
      children: [
        Text('Counter: $counter'),
        ElevatedButton(
          onPressed: () => setState(() => counter++),
          child: Text('Increment'),
        ),
      ],
    );
  }
}
```

- `counter`：状態
- `build()`：Widgetを構築
- `setState()`：状態を変更し、画面を再描画

#### メソッド

- `initState()`：`State`作成直後に一度だけ呼ばれる初期化処理
- `build(BuildContext context)`：状態が変わるたびに呼ばれるWidgetの描画処理
- `setState(VoidCallback fn)`：状態を変更して画面を再ビルド
- `dispose()`：`State`が破棄されるときのクリーンアップ処理

#### StatefulWidgetとの関係

- `StatefulWidget`：外側の不変データ
- `State`：可変データ（状態）と描画ロジック
- `State`から`widget.プロパティ名`で`StatefulWidget`本体の値を参照できる

# レイアウト制御用enum

## `MainAxisAlignment`

主軸方向のWidgetの配置

#### 値

- `MainAxisAlignment.center`：中央揃え
- `MainAxisAlignment.start`：軸の先頭に寄せる
- `MainAxisAlignment.end`：軸の末尾に寄せる
- `MainAxisAlignment.spaceBetween`：両端を揃え、均等配置
- `MainAxisAlignment.spaceAround`：均等配置（両端に半分の余白）
- `MainAxisAlignment.spaceEvenly`：完全な均等配置

## `CrossAxisAlignment`

交差軸方向のWidgetの配置

#### 値

- `CrossAxisAlignment.center`：中央揃え
- `CrossAxisAlignment.start`：軸の先頭に寄せる
- `CrossAxisAlignment.end`：軸の末尾に寄せる
- `CrossAxisAlignment.stretch`：最大幅／高さまで伸ばす
- `CrossAxisAlignment.baseline`：テキストのベースラインに揃える（`Row`限定）

## `MainAxisSize`

主軸方向の占有サイズを制御

#### 値

- `MainAxisSize.max`：親Widgetいっぱいに広げる（デフォルト）
- `MainAxisSize.min`：最小限に抑える（子Widgetの合計サイズ）

## `FlexFit`

サイズの埋め方

#### 値

- `FlexFit.tight`：できるだけ埋める
- `FlexFit.loose`：子Widgetの最小サイズで留める

## `StackFit`

#### 値

- `StackFit.loose`：子Widgetのサイズを優先し、親Widgetのサイズは制約しない
- `StackFit.expand`：子Widgetのサイズを親Widgetのサイズいっぱいに広げる
- `StackFit.passthrough`：親Widgetのサイズ制御なしで、子Widgetのサイズそのままにする

## `Axis`

#### 値

- `Axis.vertical`：縦方向スクロール
- `Axis.horizontal`：横方向スクロール

## `Clip`

はみ出しのクリップ方法

#### 値

- `Clip.none`：はみ出しても切らない
- `Clip.hardEdge`：はみ出し部分をカット（パフォーマンス重視）
- `ClipantiAlias`：アンチエイリアス付きでカット（見た目重視）
- `Clip.antiAliasWithSaveLayer`：保存レイヤー付きでカット（重いが高品質）

## `TextDirection`

テキストの横並びの方向

#### 値

- `TextDirection.ltr`：Left to Right（左から右）
- `TextDirection.rtl`：Right to Left（右から左）

## `Curves`

アニメーション用のイージング曲線定義

#### メソッド

- `Curves.easeIn`：ゆっくり始まる
- `Curves.easeOut`：ゆっくり終わる
- `Curves.easeInOut`：ゆっくり始まってゆっくり終わる
- `Curves.bounceOut`：バウンス効果

# Material/Theme系

## `Theme`

#### メソッド

テーマ情報取得
- `Theme.of(context).primaryColor`：プライマリ色
- `Theme.of(context).scaffoldBackgroundColor`：背景色
- `Theme.of(context).textTheme.<body>`：見出しなどごとのスタイル
  - 参照：[`TextTheme`](#texttheme)

## `ThemeData`

- アプリのデザインをまとめて管理するためのクラス
- 色、フォント、スタイルを一括管理できる

#### プロパティ

- [`MaterialColor`](#materialcolor) `primarySwatch`：メインカラー（色のトーン一式を指定）
- [`ColorScheme`](#colorscheme) `colorScheme`：色の組み合わせを体系的に管理
- [`Color`](#color) `scaffoldBackgroundColor`：画面背景色
- [`TextTheme`](#texttheme) `textTheme`：見出しや本文のテキストスタイル
- [`AppBarTheme`](#appbartheme) `appBarTheme`
- [`ButtonThemeData`](#buttonthemedata) `buttonTheme`
- [`ElevatedButtonThemeData`](#elevatedbuttonthemedata) `elevatedButtonTheme`
- [`TextButtonThemeData`](#textbuttonthemedata) `textButtonTheme`

#### メソッド

- `ThemeData.light().copyWith`
- `ThemeData.dark().copyWith`

## `AppBarTheme`

#### プロパティ

- [`Color`](#color) `backgroundColor`：背景色
- [`Color`](#color) `foregroundColor`：テキスト色
- `double` `elevation`：影の高さ
- [`TextStyle`](#textstyle) `titleTextStyle`：スタイル
- [`IconThemeData`](#iconthemedata) `iconTheme`：アイコン

## `CardTheme`

#### プロパティ

- [`Color`](#color) color
- `double` `elevation`
- [`ShapeBorder`](#shapeborder) `shape`
- [`EdgeInsets`](#edgeinsets) `margin`

## `VisualDencity`

#### プロパティ

- `double` `horizontal`
- `double` `vertical`

## `ButtonStyle`

ボタンのデザイン（色、サイズなど）

#### プロパティ

- [`MaterialStateProperty<Color>`](#materialstatepropertyt) `foregroundColor`：テキストやアイコンの色
- [`MaterialStateProperty<Color>`](#materialstatepropertyt) `backgroundColor`：ボタンの背景色
- [`MaterialStateProperty<EdgeInsetsGeometry>`](#materialstatepropertyt) `padding`：内側余白
- [`MaterialStateProperty<OutlinedBorder>`](#materialstatepropertyt) `shape`：ボタンの角丸や枠線

## `ButtonStyleFrom`

## `styleFrom`

- 主にButton系で使われる、複雑な設定オブジェクトを簡単に作るためのヘルパーメソッド
- 他に`AppBar`, `FloatingActionButton`, `Chip`など
- 条件分岐など複雑な状態別スタイルの場合、`styleFrom`ではなく`style: ButtonStyle`を使う

#### プロパティ

- [`Color`](#color) `backgroundColor`：背景色
- [`Color`](#color) `foregroundColor`：テキスト・アイコン色
- [`Color`](#color) `disabledBackgroundColor`：無効時の背景色
- [`Color`](#color) `disabledForegroundColor`：無効時のテキスト・アイコン色
- `double` `elevation`：影の高さ
- [`EdgeInsetsGeometry`](#edgeinsetsgeometry) `padding`：内側余白
- [`Size`](#size) `minimumSize`/`maximumSize`：最小／最大サイズ
- [`Size`](#size) `fixedSize`：固定サイズ
- [`RoundedRectangleBorder`](#roundedrectangleborder) `shape`：形状
- [`BorderSide`](#bordersize) `side`：枠線
- [`TextStyle`](#bordersize) `textStyle`：テキストスタイル
- [`Duration`](#duration) `animationDuration`：アニメーション時間

## `MaterialStateProperty<T>`

- UIWidgetの状態に応じて値を変えられるラッパーオブジェクト
- [`MaterialState`](#materialstate)と一緒に使う

```dart
ButtonStyle(
  backgroundColor: MaterialStateProperty.resolveWith((states) {
    if (states.contains(MaterialState.pressed)) {
      return Colors.red;   // 押されたとき
    }
    if (states.contains(MaterialState.hovered)) {
      return Colors.blue;  // ホバー時
    }
    return Colors.green;   // 通常時
  }),
)
```

## `MaterialState`

#### 値

- `MaterialState.all`
- `MaterialState.enabled`：通常
- `MaterialState.hovered`：ホバー中
- `MaterialState.pressed`：押されている
- `MaterialState.disabled`：無効

## `MaterialApp`

マテリアルデザインベースのアプリの土台

#### プロパティ

- `Widget` `home`：最初に表示する画面
- `String` `title`：アプリのタイトル
- [`ThemeData`](#themedata) `theme`：アプリ全体のテーマ
- [`ThemeData`](#themedata) `darkTheme`
- [`ThemeMode`](#thememode) `themeMode`
- [`Locale`](#locale) `locale`：ロケール設定

## `NavigationDestination`

- ボトムナビゲーションの1つの項目を表すクラス
- 主に[`NavigationBar`](#navigationbar)の`destinations`プロパティにリストで渡す

#### プロパティ

- `Widget` `icon`：デフォルトのアイコン
- `Widget` `selectedIcon`：選択されているときのアイコン
- `String` `label`：項目のラベル
- `String` `tooltip`：ホバー時のツールチップ

## `MediaQuery`

画面情報取得

#### メソッド

- `MediaQuery.of(context).size.width`：画面幅
- `MediaQuery.of(context).size.height`：画面高さ
- `MediaQuery.of(context).padding.top`：ステータスバー高さ
- `MediaQuery.of(context).viewInsets.bottom`：キーボード高さ
- `MediaQuery.sizeOf(context)`：サイズのみ取得

## `ColorScheme`

色の組み合わせを体系的に管理

#### プロパティ

- [`Brightness`](#brightness) `brightness`
- [`Color`](#color) `primary`
- [`Color`](#color) `onPrimary`
- [`Color`](#color) `secondary`
- [`Color`](#color) `onSecondary`
- [`Color`](#color) `background`
- [`Color`](#color) `onBackground`
- [`Color`](#color) `surface`
- [`Color`](#color) `onSurface`
- [`Color`](#color) `error`
- [`Color`](#color) `onError`

# Navigator/ジェスチャー関連

## `Navigator`

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

#### メソッド

- `Navigator.of(context).push(route)`：画面追加
- `Navigator.of(context).pop()`：画面を戻る
- `Navigator.of(context).pushReplacement(route)`：画面置換
- `Navigator.pushNamed(context, '/route')`：名前付きルートで遷移
- `Navigator.pop(context)`：簡易版

## `GestureDetector`

- タップ・スワイプ・菜蒼紫など、ユーザーのジェスチャーを検知する
- `StatelessWidget`
- 見た目を持たない（子Widgetを包む）
- ボタン以外の場所でもインタラクションを追加できる

#### プロパティ

- `VoidCallback` `onTap`：タップ時に呼ばれる関数
- `VoidCallback` `onDoubleTap`：ダブルタップ時に呼ばれる関数
- `VoidCallback` `onLongPress`：長押し時に呼ばれる関数
- `void Function(DragUpdateDetails)` `onPanUpdate`：ドラッグ時に呼ばれる関数
  - [`DragUpdateDetails`](#deagupdatedetails)
- `Widget` `child`

## `DragUpdateDetails`

`onPanUpdate`で渡される詳細情報オブジェクト

#### プロパティ

- [`Offset`](#offset) `delta`：前回の位置からの移動量（x, y）
- [`Offset`](#offset) `globalPosition`：画面全体の絶対座標
- [`Offset`](#offset) `localPosition`：`GestureDetector`内での相対座標

# Sliver/Delegate系

## `SliverGridDelegate`

グリッドの列や比率を決める

### `SliverGridDelegateWithFixedCrossAxisCount`

#### プロパティ

- `int` `crossAxisCount`
- `double` `mainAxisSpacing`
- `double` `crossAxisSpacing`
- `double` `childAspectRatio`

### `SliverGridDelegateWithMaxCrossAxisExtent`

#### プロパティ

- `double` `maxCrossAxisExtent`
- `double` `mainAxisSpacing`
- `double` `crossAxisSpacing`
- `double` `childAspectRatio`

# BottomNavigation系

[BottomNavigationBar](#bottomnavigationbar)

## `BottomNavigationBarType`

固定／シフト表示

#### 値

- `BottomNavigationBarType.fixed`：全タブを均等に表示
- `BottomNavigationBarType.shifting`：選択中タブが強調され、他は小さくなる

## `BottomNavigationBarItem`

#### プロパティ

- [`Icon`](#icon) `icon`：タブのアイコン
- `String` `label`：タブのラベル

# 未分類

## `RoundedRectangleBorder`

ボタンやカードの角丸

#### プロパティ

- [`BorderSide`](#borderside) `side`：枠線の太さや色
- [`BorderRadiusGeometry`](#borderradiusgeometry) `borderRadius`：角丸の半径

## `Brightness`

#### 値

- `light`
- `dark`

## `TextOverFlow`

- `Text`で文字列が指定された領域からはみ出すときの挙動を指定
- `maxLines`と組み合わせて使う

#### 値

- `TextOverFlow.clip`：テキストを単純に切り捨てる
- `TextOverFlow.fade`：
  - 末尾がフェードアウトして徐々に透明になる
  - `softWrap: false`と組み合わせると綺麗に動作する
- `TextOverFlow.ellipsis`：末尾を「`…`」で省略表示（最もよく使われる）
- `TextOverFlow.visible`：制約を無視してそのまま描画

## `EdgeInsetsGeometry`

- 余白（`padding`/`margin`）を表現するための抽象クラス
- 通常はサブクラスを利用する

#### サブクラス

- [`EdgeInsets`](#edgeinsets)
- [`EdgeInsetsDirectional`](#edgeinsetsdirectional)

## `EdgeInsetsDirectional`

言語の方向性（LTR/RTL）に応じて左右の意味が変わる
- `start`：LTRなら左、RTLなら右
- `end`：LTRなら右、RTLなら左

#### 値

- 方向依存：`EdgeInsetsDirectional.only({start, top, end, bottom})`
- STEB順に指定：`EdgeInsetsDirectional.fromSTEB(start, top, end, bottom)`

## `AlignmentGeometry`

配置を表すための抽象クラス

#### サブクラス

- [`Alignment`](#alignment)
- [`AlignmentDirectional`](#alignmentdirectional)

## `BoxConstraints`

#### プロパティ

- `double` `minWidth`
- `double` `maxWidth`
- `double` `minHeight`
- `double` `maxHeight`

#### コンストラクタ

- `BoxConstraints()`：全部指定できる
- `BoxConstraints.tight(Size size)`：幅と高さを固定
- `BoxConstraints.tightFor({double? width, double? height})`：幅または高さを固定
- `BoxConstraints.tightForfinite({double? width, double? height})`：無限指定時にだけ制約を与える
- `BoxConstraints.expand({double? width, double? height})`：親いっぱいに広げる
- `BoxConstraints.loose(Size size)`：最大値だけ指定
- `BoxConstraints.unconstrained()`：制約なし

## `showModalBottomSheet`

- 画面下からモーダル形式のシートを表示するための関数
- 背景が半透明で操作不可（モーダル）
- スワイプで閉じることも可能
- ユーザーが閉じると`Future<T?>`（`Navigator.pop()`で返す値）が返る

#### 基本構文

```dart
showModalBottomSheet(
  context: context,
  builder: (BuildContext context) {
    return Container(
      height: 200,
      padding: const EdgeInsets.all(16),
      child: Column(
        children: [
          const Text('モーダルシート', style: TextStyle(fontSize: 18)),
          ElevatedButton(
            onPressed: () => Navigator.pop(context, '閉じたよ'),
            child: const Text('閉じる'),
          ),
        ],
      ),
    );
  },
);
```

- `builder`でシートの内容を返す
- `Navigator.pop(context, result)`で閉じながら値を返せる