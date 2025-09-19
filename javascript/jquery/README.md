<!-- omit in toc -->
# jQuery

### 目次

- [jQuery](#jquery-1)
- [セレクタ](#セレクタ)
- [メソッド](#メソッド)
- [イベントオブジェクト](#イベントオブジェクト)
- [イベント名](#イベント名)

## jQuery

- `$`：jQueryの別名（エイリアス）
- `$ ->`：CoffeeScriptにおいて、DOMが完全に読み込まれた時に実行する処理を定義

## セレクタ

書式：`$(selector)`

- `$("#id")`：既存のHTML要素をIDで取得
  - HTML内で一意
- `$(".class")`：既存のHTML要素をクラス属性で取得
  - 複数の要素に同じクラス名をつけられる
  - 共通の属性やスタイルを複数要素にまとめて適用できる
- `$("<tag>content<tag>"`：新しいHTML要素を生成
  - `$("id").append`：idの中に追加
- `$(document)`：HTMLドキュメント全体（DOMツリーのルート）を表す

## メソッド

- `.trigger('event_name')`：指定した要素に擬似的にイベントを発生させる
- `.on('event_name', handlerFunction)`：イベントが起きた時に実行され得る関数を登録
  - イベント名は複数設定できる
  - **イベント委譲**
    - 第二引数にセレクタを入れると、動的に追加された要素にも反応できる
    - `$(document)`を指定する
- `.val`：input等の値を取得・設定
- `.text`/`.html`：テキスト／HTMLを取得・設定
- `.append`/`.prepend`：要素の追加
- `.remove`：要素の削除
- `.css`：スタイルの設定
- `.addClass`/`.removeClass`：クラス操作
- `.next`/`.prev`：DOM(HTMLツリー)構造の中をたどり、直前／直後の兄弟要素を取得
- `.parent`/`.children`：親要素／子要素を取得
- `.find(target)`：その要素の中（子孫）から指定した要素を探す
- `.data`：HTML要素に任意のデータを紐付けて保存・取得
  - 保存（セット）：`.data('key', 'value')`
  - 取得（ゲット）：`.data('key')`（`value`が返される）
 
## イベントオブジェクト

- `evt.tyoe`：発生したイベントの種類（例：`"click"`）
- `evt.target`：イベントが発生したHTML要素（DOMノード）
- `evt.which`：押されたキーのコード（キーボードイベントで使う）
- `evt.oreventDefault()`：ブラウザのデフォルト動作をキャンセルする（リンク遷移など）
- `evt.stopPropagation()`：イベントのバブリング（親要素への伝播）を止める

※`evt`を`e`としても良い

## イベント名

- `'click'`：クリックされた時
- `'dblclick'`：ダブルクリックされた時
- `'keypress'`：キーボード入力（非推奨）
- `'keydown'`：キーが押された時
- `'keyup'`：キーが離された時
- `'submit'`：フォームが送信された時
- `'change'`：`<input>`や`<select>`の値が変更された時
- `'mouseover'`：マウスが乗った時
- `'mouseout'`：マウスが離れた時
- `'focus'`：フォーカスが当たった時
- `'blur'`：フォーカスが外れた時
