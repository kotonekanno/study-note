# 基本構造とリクエスト処理の流れ

### 目次

- [Playアプリのプロジェクト構成](#playアプリのプロジェクト構成)
- [リクエスト処理の流れ](#リクエスト処理の流れ)
- [routesファイルの基本構文](#routesファイルの基本構文)

## Playアプリのプロジェクト構成

典型的なPlayアプリ構造：  
```cpp
project-root/
├── app/              ← メインのアプリコード
│   ├── controllers/  ← コントローラ定義（C）
│   ├── models/       ← ドメインロジックやDB関連（M）
│   └── views/        ← HTMLテンプレート（V）
├── conf/
│   └── routes        ← ルーティング定義ファイル
├── public/           ← JS, CSS, 画像などの静的ファイル
├── build.sbt         ← ビルド設定ファイル
```

## リクエスト処理の流れ

ユーザーがブラウザでページにアクセスすると、  
1. ` routes`ファイルでURLに対応するControllerのメソッドが決まる  
2. Controllerが呼ばれ、必要に応じてModelやViewを呼ぶ  
3. 結果（HTMLまたはJSONなど）を生成し、レスポンスとして返す  
   
```css
[ブラウザ] → URLアクセス
      ↓
[conf/routes] → どのController/Actionに渡すか決定
      ↓
[Controller] → ModelやViewを使用
      ↓
[View or 結果] → ブラウザへHTMLなどを返す
```

## routesファイルの基本構文

- ファイル場所：` conf/routes`  

```pgsql
メソッド   パス            コントローラとアクション
-------------------------------------------------------
GET       /home          controllers.HomeController.index
POST      /user/create   controllers.UserController.createUser
```

- ルール：  
  - 1列目：HTTPメソッド（GET, POST, etc.）  
  - 2列目：URLパス  
  - 3列目：呼び出すControllerのクラスとメソッド  
- 動的パスパラメータの例：
  ```bash
  GET   /users/:id      controllers.UserController.show(id: Long)
  ```
