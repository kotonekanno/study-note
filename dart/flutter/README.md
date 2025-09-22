<!-- omit in toc -->
# Flutter

### 目次

- [リンク](#リンク)
- [階層構造](#階層構造)
  - [基本のWidget階層](#基本のwidget階層)
  - [値クラス・装飾クラス](#値クラス装飾クラス)
  - [テキスト関連](#テキスト関連)
  - [入力・コントローラー系](#入力コントローラー系)
  - [レイアウト制御用enum](#レイアウト制御用enum)
  - [Material/Theme系](#materialtheme系)
  - [Navigator/ジェスチャー関連](#navigatorジェスチャー関連)
  - [Sliver/Delegate系](#sliverdelegate系)
- [Widget索引](#widget索引)

## リンク

1. [Flutterアプリの基礎](01_basic.md)
2. [Widget／クラス](02_02_widgets.md)

## 階層構造

### 基本のWidget階層

```
Widget (抽象クラス)
├── StatelessWidget
│   ├── Text
│   ├── Icon
│   ├── Card
│   ├── Material
│   ├── Divider
│   ├── CircleAvatar
│   ├── Tooltip
│   ├── FloatingActionButton
│   ├── ElevatedButton
│   ├── TextButton
│   ├── IconButton
│   ├── ListTile
│   └── InkWell
│
├── StatefulWidget
│   ├── Scaffold
│   ├── AppBar
│   ├── SliverAppBar
│   ├── BottomNavigationBar
│   ├── Form
│   ├── TextField
│   ├── TextFormField
│   ├── Checkbox
│   ├── Switch
│   ├── Radio
│   ├── ListView
│   ├── GridView
│   ├── SingleChildScrollView
│   ├── StreamBuilder<T>
│   └── ValueListenableBuilder<T>
│
├── RenderObjectWidget
│   ├── SingleChildRenderObjectWidget
│   │   ├── Container
│   │   ├── Padding
│   │   ├── Center
│   │   ├── Align
│   │   ├── SizedBox
│   │   ├── Expanded
│   │   ├── Flexible
│   │   ├── Positioned
│   │   ├── Visibility
│   │   └── FractionallySizedBox
│   └── MultiChildRenderObjectWidget
│       ├── Row
│       ├── Column
│       ├── Stack
│       └── Spacer
│
├── ProxyWidget
│   ├── InheritedWidget
│   └── ParentDataWidget
│
└── PreferredSizeWidget (interface)
    └── AppBar (implements)
```

### 値クラス・装飾クラス

```
Color / Colors
Size / Offset / Duration
EdgeInsets
Alignment
BoxFit (enum)
BoxDecoration
Border
│  ├── BorderSide
│  └── BorderStyle (enum)
BorderRadius / Radius
DecorationImage
BoxShadow
Gradient (abstract)
ShapeBorder (abstract)
│  ├── RoundedRectangleBorder
│  ├── CircleBorder
│  └── StadiumBorder
```

### テキスト関連

```
TextStyle
│  ├── FontWeight
│  ├── FontStyle
│  ├── TextDecoration
│  └── backgroundColor, height, etc.
TextAlign (enum)
TextTheme
```

### 入力・コントローラー系

```TextEditingController
TextSelection
ScrollPhysics (enum)
TextInputType (enum)
ValueListenable<T>
ValueNotifier<T>
AsyncSnapshot<T>
```

### レイアウト制御用enum

```
MainAxisAlignment
CrossAxisAlignment
MainAxisSize
FlexFit
StackFit
Axis
Clip
TextDirection
```

### Material/Theme系

```
Theme
ThemeData
AppBarTheme
CardTheme
VisualDensity
ButtonStyle
ButtonStyleFrom (factory)
MaterialApp
NavigationDestination
MediaQuery
```

### Navigator/ジェスチャー関連

```
Navigator
GestureDetector
DragUpDetails
```

### Sliver/Delegate系

```
SliverGridDelegate (abstract)
├── SliverGridDelegateWithFixedCrossAxisCount
└── SliverGridDelegateWithMaxCrossAxisExtent
```

## Widget索引

- [Align](02_widgets.md#align)
- [Alignment](02_widgets.md#alignment)
- [AppBar](02_widgets.md#appbar)
- [AppBar(implements)](02_widgets.md#appbarinplements)
- [Axis](02_widgets.md#axis)
- [BlendMode](02_widgets.md#blendmode)
- [Border](02_widgets.md#border)
- [BorderRadius](02_widgets.md#borderradius)
- [BorderSide](02_widgets.md#borderside)
- [BottomNavigationBar](02_widgets.md#bottomnavigationbar)
- [BoxDecoration](02_widgets.md#boxdecoration)
- [BoxFit](02_widgets.md#boxfit)
- [BoxShadow](02_widgets.md#boxshadow)
- [Card](02_widgets.md#card)
- [Center](02_widgets.md#center)
- [CheckBox](02_widgets.md#checkbox)
- [CircleAvatar](02_widgets.md#circleavatar)
- [Clip](02_widgets.md#clip)
- [Color](02_widgets.md#color)
- [Column](02_widgets.md#column)
- [Container](02_widgets.md#container)
- [CrossAxissAlignment](02_widgets.md#crossaxisalignment)
- [Divider](02_widgets.md#divider)
- [Duration](02_widgets.md#duration)
- [EdgeInsets](02_widgets.md#edgeinsets)
- [ElevatedButton](02_widgets.md#elevatedbutton)
- [Expanded](02_widgets.md#expanded)
- [FlexFit](02_widgets.md#flexfit)
- [Flexible](02_widgets.md#flexible)
- [FloatingActionButton](02_widgets.md#floatingactionbutton)
- [Form](02_widgets.md#form)
- [GestureDetector](02_widgets.md#gesturedetector)
- [Gradient](02_widgets.md#gradient)
- [GridView](02_widgets.md#gridview)
- [Icon](02_widgets.md#icon)
- [IconButton](02_widgets.md#iconbutton)
- [ImageProvider](02_widgets.md#imageprovider)
- [ImageRepeat](02_widgets.md#imagerepeat)
- [InheritedWidget](02_widgets.md#inheritedwidget)
- [ListTile](02_widgets.md#listtile)
- [ListView](02_widgets.md#listview)
- [MainAxisAlignment](02_widgets.md#mainaxisalignment)
- [Material](02_widgets.md#material)
- [Navigator](02_widgets.md#navigator)
- [Padding](02_widgets.md#padding)
- [ParentDataWidget](02_widgets.md#parentdatawidget)
- [Positioned](02_widgets.md#positioned)
- [PreferredSizeWidget](02_widgets.md#preferredsizewidget)
- [ProxyWidget](02_widgets.md#proxywidget)
- [Radio](02_widgets.md#radio)
- [Row](02_widgets.md#row)
- [Scaffold](02_widgets.md#scaffold)
- [ScrollPhysics](02_widgets.md#scrollphysics)
- [ShapeBorder](02_widgets.md#shapeborder)
- [SingleChildrenScrollView](02_widgets.md#singlechildrenscrollview)
- [SizedBox](02_widgets.md#sizedbox)
- [Spacer](02_widgets.md#spacer)
- [Stack](02_widgets.md#stack)
- [StackFit](02_widgets.md#stackfit)
- [StreamBuilder](02_widgets.md#streambuilder)
- [Switch](02_widgets.md#switch)
- [Text](02_widgets.md#text)
- [TextButton](02_widgets.md#textbutton)
- [TextDirection](02_widgets.md#textdirection)
- [TextEditingController](02_widgets.md#texteditingcontroller)
- [TextField](02_widgets.md#textfield)
- [TextFormField](02_widgets.md#textformfield)
- [TextInputType](02_widgets.md#textinputtype)
- [TextSelection](02_widgets.md#textselection)
- [TextStyle](02_widgets.md#textstyle)
- [Tooltip](02_widgets.md#tooltip)
- [ValueListenableBuilder](02_widgets.md#valuelistenablebuilder)
- [Visibility](02_widgets.md#visibility)