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

