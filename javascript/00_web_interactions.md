# Webアプリ向けJavaScript

### 目次

<br>

## 設置方法

1. インラインJavaScript
   
   ```html
   <body>
     <script>
       document.write("Hello");
     </script>
   </body>
   ```

   - HTMLファイル内でscript要素を用いる方法
   - ルール上どこにでも配置可能
    
2. 外部JavaScript

   ```html
   <script src="script.js"></script>
   ```

   ```js
   # script.js
   var output1 = document.getElementById("output1);
   var a = "Hello"
   output1.innerHTML = y;
   ```

## 要素の取得

```html
  <body>
  <p id=”output1”>Hello</p>
  <script>
    var output1 = document.getElementById(”output1”);
    output1.innerHTML = “Bye”;
  </script>
</body>
```

- 操作したい要素に`id`属性（識別子）をつける
- `document.getElementById()`で要素の取得を行い、変数に代入する
- 変数の要素の中のHTML部分（`innerHTML`）に別の値を代入

## データの入力

### input要素

```html
<p><input type=”text” id=”input1”></p>
<p><button onclick=”btn1();”>PUSH</button></p>
<p id=”output1”>出力</p>
<script>
  var input1=document.getElementById(”input1”);
  var output1=document.getElementById(”output1”);
  function btn(){
  output1.innerHTML=input1.value;
  }
</script>
```

- 要素の取得のため、`input`要素に`id`属性をつける
- `onclick`属性：クリックしたら起動するプログラム・関数を定義
- `function function_name(){}`：独自関数の定義
- `input1.value`：入力の値

<br>

#### type属性

- `text`：単一行のテキスト入力
- `range`：スライダ
- `color`：色を指定するカラーピッカー
- `date`：日付けのカレンダ
- `time`：時刻入力
- `number`：数値入力
- `tel`：電話番号テンキー（スマホのみ）

#### その他の属性

- `value`：初期値入力
- `max`：最大値
- `min`：最小値
- `step`：増分
- `placeholder`：入力のヒント

### select要素

```html
<p>Size
  <select id=”input1”>
    <option>S</option>
    <option>M</option>
    <option>L</option>
  </select>
  <button onclick=”btn1()”>PUSH</button>
</p>
<p id=”output1”>Choice</p>
```

### textarea要素

```html
<p>Message
  <textarea id=”input1”></textarea>
</p>
<button onclock=”btn1()”>PUSH</button>
<pre id=”output1”>Result</pre>
```

## 標準ライブラリ

### Mathオブジェクト

- `Math.PI`：円周率（約3.14）
- `Math.E`：ネイピア数（自然対数の底e=約2.718）

<br>

- `Math.floor()`：切り捨て
- `Math.round()`：四捨五入
- `Math.ceil()`：切り上げ
- `Math.pow()`：累乗
- `Math.random()`：乱数

### Dateオブジェクト

`var now = new Date();`

- `now.getFullYear()`：年
- `now.getMonth()`：月+1
- `now.getDate()`：日
- `now.getDay()`：曜日
- `now.getHours()`：時
- `now.getMinutes()`：分
- `now.getSeconds()`：秒
- `now.getTime()`：UNIXエボック（1970.01.01 00\:00:00からのミリ秒）
