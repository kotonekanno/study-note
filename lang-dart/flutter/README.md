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
  - [BottomNavigation系](#bottomnavigation系)
- [Widget索引](#widget索引)

## リンク

1. [Flutterアプリの基礎](01_basic.md)
2. [Widget／クラス](02_widgets.md)

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
│   ├── InkWell
│   ├── Image
│   └── LayoutBuilder
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
│   ├── AppBar (implements)
│   └── PreferredSize
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
ImageProvider<T>
BlendMode (enum)
ImageRepeat (enum)
VerticalDecoration
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
InputDecoration
```

### 入力・コントローラー系

```TextEditingController
TextSelection
ScrollPhysics (enum)
TextInputType (enum)
ValueListenable<T>
ValueNotifier<T>
AsyncSnapshot<T>
State<T>
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
Curves
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
styleFrom (factory)
MaterialStateProperty<T>
MaterialState (enum)
MaterialApp
NavigationDestination
MediaQuery
ColorScheme
```

### Navigator/ジェスチャー関連

```
Navigator
GestureDetector
DragUpdateDetails
```

### Sliver/Delegate系

```
SliverGridDelegate (abstract)
├── SliverGridDelegateWithFixedCrossAxisCount
└── SliverGridDelegateWithMaxCrossAxisExtent
```

### BottomNavigation系

```
BottomNavigationBar
BottomNavigationBarType (enum)
BottomNavigationBarItem
```

## Widget索引

- [Align](02_widgets.md#align)
- [Alignment](02_widgets.md#alignment)
- [AppBar](02_widgets.md#appbar)
- [AppBar(implements)](02_widgets.md#appbarinplements)
- [AppBarTheme](02_widgets.md#appbartheme)
- [AsyncSnapshot<T>](02_widgets.md#asyncsnapshott)
- [Axis](02_widgets.md#axis)
- [BlendMode](02_widgets.md#blendmode)
- [Border](02_widgets.md#border)
- [BorderRadius](02_widgets.md#borderradius)
- [BorderSide](02_widgets.md#borderside)
- [BorderStyle](02_widgets.md#borderstyle)
- [BottomNavigationBar](02_widgets.md#bottomnavigationbar)
- [BottomNavigationBarItem](02_widgets.md#bottomnavigationbaritem)
- [BottomNavigationBarType](02_widgets.md#bottomnavigationbartype)
- [BoxDecoration](02_widgets.md#boxdecoration)
- [BoxFit](02_widgets.md#boxfit)
- [BoxShadow](02_widgets.md#boxshadow)
- [ButtonStyle](02_widgets.md#buttonstyle)
- [ButtonStyleFrom](02_widgets.md#buttonstylefrom)
- [Card](02_widgets.md#card)
- [CardTheme](02_widgets.md#cardtheme)
- [Center](02_widgets.md#center)
- [CheckBox](02_widgets.md#checkbox)
- [CircleAvatar](02_widgets.md#circleavatar)
- [Clip](02_widgets.md#clip)
- [Color](02_widgets.md#color)
- [Colors](02_widgets.md#colors)
- [ColorScheme](02_widgets.md#colorscheme)
- [Column](02_widgets.md#column)
- [Container](02_widgets.md#container)
- [CrossAxissAlignment](02_widgets.md#crossaxisalignment)
- [Curves](02_widgets.md#curves)
- [DecorationImage](02_widgets.md#decorationimage)
- [Divider](02_widgets.md#divider)
- [DrauUpdateDetails](02_widgets.md#dragupdatedetails)
- [Duration](02_widgets.md#duration)
- [EdgeInsets](02_widgets.md#edgeinsets)
- [ElevatedButton](02_widgets.md#elevatedbutton)
- [Expanded](02_widgets.md#expanded)
- [FlexFit](02_widgets.md#flexfit)
- [Flexible](02_widgets.md#flexible)
- [FloatingActionButton](02_widgets.md#floatingactionbutton)
- [FontStyle](02_widgets.md#fontstyle)
- [FontWeight](02_widgets.md#fontweight)
- [Form](02_widgets.md#form)
- [GestureDetector](02_widgets.md#gesturedetector)
- [Gradient](02_widgets.md#gradient)
- [GridView](02_widgets.md#gridview)
- [Icon](02_widgets.md#icon)
- [IconButton](02_widgets.md#iconbutton)
- [Image](02_widgets.md#image)
- [ImageProvider<T>](02_widgets.md#imageprovidert)
- [ImageRepeat](02_widgets.md#imagerepeat)
- [InheritedWidget](02_widgets.md#inheritedwidget)
- [InkWell](02_widgets.md#inkwell)
- [InputDecoration](02_widgets.md#inputdecoration)
- [LayoutBuilder](02_widgets.md#layoutbuilder)
- [ListTile](02_widgets.md#listtile)
- [ListView](02_widgets.md#listview)
- [MainAxisAlignment](02_widgets.md#mainaxisalignment)
- [MainAxisSize](02_widgets.md#mainaxissize)
- [Material](02_widgets.md#material)
- [MaterialApp](02_widgets.md#materialapp)
- [MaterialState](02_widgets.md#materialstate)
- [MaterialStateProperty<T>](02_widgets.md#materialstatepropertyt)
- [MediaQuery](02_widgets.md#mediaquery)
- [NavigationDestination](02_widgets.md#navigationdestination)
- [Navigator](02_widgets.md#navigator)
- [Offset](02_widgets.md#offset)
- [Padding](02_widgets.md#padding)
- [ParentDataWidget](02_widgets.md#parentdatawidget)
- [Positioned](02_widgets.md#positioned)
- [PreferredSize](02_widgets.md#preferredsize)
- [PreferredSizeWidget](02_widgets.md#preferredsizewidget)
- [ProxyWidget](02_widgets.md#proxywidget)
- [Radio<T>](02_widgets.md#radiot)
- [Radius](02_widgets.md#radius)
- [Row](02_widgets.md#row)
- [Scaffold](02_widgets.md#scaffold)
- [ScrollPhysics](02_widgets.md#scrollphysics)
- [ShapeBorder](02_widgets.md#shapeborder)
- [SingleChildScrollView](02_widgets.md#singlechildscrollview)
- [Size](02_widgets.md#size)
- [SizedBox](02_widgets.md#sizedbox)
- [SliverAppBar](02_widgets.md#sliverappbar)
- [SliverGridDelegate](02_widgets.md#slivergriddelegate)
- [SliverGridDelegateWithFixedCrossAxisCount](02_widgets.md#slivergriddelegatewithfixedcrossaxiscount)
- [SliverGridDelegateWithMaxCrossAxisExtent](02_widgets.md#slivergriddelegatewithmaxcrossaxisextent)
- [Spacer](02_widgets.md#spacer)
- [Stack](02_widgets.md#stack)
- [StackFit](02_widgets.md#stackfit)
- [State<T>](02_widgets.md#statet)
- [StreamBuilder<T>](02_widgets.md#streambuildert)
- [styleFrom](02_widgets.md#stylefrom)
- [Switch](02_widgets.md#switch)
- [Text](02_widgets.md#text)
- [TextAlign](02_widgets.md#textalign)
- [TextButton](02_widgets.md#textbutton)
- [TextDecoration](02_widgets.md#textdecoration)
- [TextDirection](02_widgets.md#textdirection)
- [TextEditingController](02_widgets.md#texteditingcontroller)
- [TextField](02_widgets.md#textfield)
- [TextFormField](02_widgets.md#textformfield)
- [TextInputType](02_widgets.md#textinputtype)
- [TextSelection](02_widgets.md#textselection)
- [TextStyle](02_widgets.md#textstyle)
- [TextTheme](02_widgets.md#texttheme)
- [Theme](02_widgets.md#theme)
- [ThemeData](02_widgets.md#themedata)
- [Tooltip](02_widgets.md#tooltip)
- [ValueListenable<T>](02_widgets.md#valuelistenablet)
- [ValueListenableBuilder<T>](02_widgets.md#valuelistenablebuildert)
- [ValueNotifer<T>](02_widgets.md#valuenotifiert)
- [VerticalDecoration](02_widgets.md#verticaldecoration)
- [VisualDencity](02_widgets.md#visualdencity)
- [Visibility](02_widgets.md#visibility)