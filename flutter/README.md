<!-- omit in toc -->
# Flutter

### 目次

- [リンク](#リンク)
- [Widget階層構造](#widget階層構造)
- [Widget索引](#widget索引)

## リンク

- [Widget](widgets.md)
- [ライブラリ](packages.md)
  - [Provider](provider.md)

## Widget階層構造

```
【最上位】
Widget
├── DiagnosticableTree
├── Key

【Widget の主要サブクラス】
Widget
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
│   └── ListTile
│
├── StatefulWidget
│   ├── Scaffold
│   ├── AppBar
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
│   │   └── Visibility
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
└── PreferredSizeWidget
    └── AppBar (implements)

【その他の重要クラス】
Navigator (システムクラス)
GestureDetector (StatelessWidget)
StreamBuilder (StatefulWidget)

【非Widget クラス（値・設定・コントローラー系）】
ImageProvider (abstract)
EdgeInsets (値クラス)
Color (値クラス)
Colors (定数クラス)
Alignment (値クラス)
BoxFit (enum)
BoxDecoration (値クラス)
TextStyle (値クラス)
TextEditingController (コントローラー)
TextSelection (値クラス)
Duration (値クラス)
BorderRadius (値クラス)
Border (値クラス)
BoxShadow (値クラス)
Gradient (abstract)
ShapeBorder (abstract)
├── RoundedRectangleBorder
├── CircleBorder
└── StadiumBorder

【enum系】
MainAxisAlignment
CrossAxisAlignment
TextDirection
FlexFit
StackFit
Clip
Axis
ScrollPhysics
TextInputType
BlendMode
ImageRepeat

【Generic系】
MaterialStateProperty<T>
ValueListenable<T>
ValueNotifier<T>
AsyncSnapshot<T>

【Delegate系（GridView用）】
SliverGridDelegate (abstract)
├── SliverGridDelegateWithFixedCrossAxisCount
└── SliverGridDelegateWithMaxCrossAxisExtent
```

## Widget索引

- [Align](widgets.md#align)
- [Alignment](widgets.md#alignment)
- [AppBar](widgets.md#appbar)
- [AppBar(implements)](widgets.md#appbarinplements)
- [Axis](widgets.md#axis)
- [BlendMode](widgets.md#blendmode)
- [Border](widgets.md#border)
- [BorderRadius](widgets.md#borderradius)
- [BorderSide](widgets.md#borderside)
- [BottomNavigationBar](widgets.md#bottomnavigationbar)
- [BoxDecoration](widgets.md#boxdecoration)
- [BoxFit](widgets.md#boxfit)
- [BoxShadow](widgets.md#boxshadow)
- [Card](widgets.md#card)
- [Center](widgets.md#center)
- [CheckBox](widgets.md#checkbox)
- [CircleAvatar](widgets.md#circleavatar)
- [Clip](widgets.md#clip)
- [Color](widgets.md#color)
- [Column](widgets.md#column)
- [Container](widgets.md#container)
- [CrossAxissAlignment](widgets.md#crossaxisalignment)
- [Divider](widgets.md#divider)
- [Duration](widgets.md#duration)
- [EdgeInsets](widgets.md#edgeinsets)
- [ElevatedButton](widgets.md#elevatedbutton)
- [Expanded](widgets.md#expanded)
- [FlexFit](widgets.md#flexfit)
- [Flexible](widgets.md#flexible)
- [FloatingActionButton](widgets.md#floatingactionbutton)
- [Form](widgets.md#form)
- [GestureDetector](widgets.md#gesturedetector)
- [Gradient](widgets.md#gradient)
- [GridView](widgets.md#gridview)
- [Icon](widgets.md#icon)
- [IconButton](widgets.md#iconbutton)
- [ImageProvider](widgets.md#imageprovider)
- [ImageRepeat](widgets.md#imagerepeat)
- [InheritedWidget](widgets.md#inheritedwidget)
- [ListTile](widgets.md#listtile)
- [ListView](widgets.md#listview)
- [MainAxisAlignment](widgets.md#mainaxisalignment)
- [Material](widgets.md#material)
- [Navigator](widgets.md#navigator)
- [Padding](widgets.md#padding)
- [ParentDataWidget](widgets.md#parentdatawidget)
- [Positioned](widgets.md#positioned)
- [PreferredSizeWidget](widgets.md#preferredsizewidget)
- [ProxyWidget](widgets.md#proxywidget)
- [Radio](widgets.md#radio)
- [Row](widgets.md#row)
- [Scaffold](widgets.md#scaffold)
- [ScrollPhysics](widgets.md#scrollphysics)
- [ShapeBorder](widgets.md#shapeborder)
- [SingleChildrenScrollView](widgets.md#singlechildrenscrollview)
- [SizedBox](widgets.md#sizedbox)
- [Spacer](widgets.md#spacer)
- [Stack](widgets.md#stack)
- [StackFit](widgets.md#stackfit)
- [StreamBuilder](widgets.md#streambuilder)
- [Switch](widgets.md#switch)
- [Text](widgets.md#text)
- [TextButton](widgets.md#textbutton)
- [TextDirection](widgets.md#textdirection)
- [TextEditingController](widgets.md#texteditingcontroller)
- [TextField](widgets.md#textfield)
- [TextFormField](widgets.md#textformfield)
- [TextInputType](widgets.md#textinputtype)
- [TextSelection](widgets.md#textselection)
- [TextStyle](widgets.md#textstyle)
- [Tooltip](widgets.md#tooltip)
- [ValueListenableBuilder](widgets.md#valuelistenablebuilder)
- [Visibility](widgets.md#visibility)