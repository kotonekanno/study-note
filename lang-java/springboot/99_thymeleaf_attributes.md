<!-- omit in toc -->
# Thymeleaf構文一覧

<!-- omit in toc -->
### 目次

- [属性](#属性)
  - [`th:text`](#thtext)
  - [`th:each`](#theach)
  - [`th:if`](#thif)
  - [`th:unless`](#thunless)
  - [`th:object` / `th:field`](#thobject--thfield)
  - [`th:errors`](#therrors)
  - [`th:value`](#thvalue)
  - [`th:href`](#thhref)
  - [`th:action`](#thaction)
- [インライン式](#インライン式)
  - [標準式構文](#標準式構文)
  - [インライン表記](#インライン表記)
  - [式オブジェクト](#式オブジェクト)

## 属性

HTMLタグの属性として記述する

### `th:text`

テキストノードを置き換える

```html
<p th:text="${name}"></p>
```
```java
model.addAttribute("name", "John")
```

### `th:each`

コレクションをループ処理する

```html
<ul>
  <li th:each="item : ${items}" th:text="${item}"></li>
</ul>
```
```java
model.addAttribute("items", list)
```

### `th:if`

条件が`true`のとき描画

```html
<p th:if="${isAdmin}">Authorized</p>
```

### `th:unless`

条件が`false`のとき描画

```html
<p th:unless="{isAdmin}">Unauthorized</p>
```

### `th:object` / `th:field`

```html
<form th:object="${user}">
  <input th:field="*{name}">
</form>
```

- `th:object`：
  - フォームなどで基準となるオブジェクトを指定
  - `*{}`式とセットで使う
- `th:field`：
  - フォーム入力とオブジェクトのプロパティをバインド
  - `name`, `id`, `value`を自動生成

### `th:errors`

バリデーションエラー表示

```html
<p th:errors="*{プロパティ名}">
```

### `th:value`

`value`属性を動的に設定

```html
<input th:values="式">
```

### `th:href`

`href`属性を動的に設定

```html
<a th:href="URL式">
```

### `th:action`

フォーム送信先URLを指定

```html
<form th:action="@{/login}" method="post">
```


## インライン式

属性値やテキストの中で評価される式

### 標準式構文

- `${...}`：変数式
- `*{...}`：選択変数式
- `@{...}`：URL式
- `#{...}`：メッセージ式
- `~{...}`：フラグメント式

### インライン表記

- テキストインライン
  ```html
  <p>Hello, [[${name}]]!</p>
  ```

- JavaScriptインライン
  ```html
  <script th:inline="javascript">
    const name = [[${name}]];
  </script>
  ```

### 式オブジェクト

3.1 ${...}：変数式
役割

Model に入っている値を参照

例
<p th:text="${user.name}"></p>

3.2 *{...}：選択変数式
役割

th:object で指定されたオブジェクト配下を参照

例
<form th:object="${user}">
  <input th:field="*{name}">
</form>


➡ 実体は ${user.name}

3.3 #fields：バリデーション関連
役割

入力エラーの有無チェックなど

よく使うメソッド
#fields.hasErrors('fieldName')
#fields.errors('fieldName')

例
<div th:if="${#fields.hasErrors('email')}">
  <span th:errors="*{email}"></span>
</div>

全体イメージ（対応関係）
Model
 └─ ${user}
     ├─ name
     ├─ email
     └─ age

<form th:object="${user}">
  <input th:field="*{name}">
  <span th:errors="*{name}"></span>
</form>