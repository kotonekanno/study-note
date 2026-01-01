<!-- omit in toc -->
# 基本操作

<!-- omit in toc -->
### 目次

- [データベースの操作](#データベースの操作)
  - [データベースの一覧表示](#データベースの一覧表示)
  - [データベースの作成](#データベースの作成)
  - [データベースの削除](#データベースの削除)
  - [利用するデータベースの指定](#利用するデータベースの指定)
  - [現在使用しているデータベースの表示](#現在使用しているデータベースの表示)
- [テーブル操作](#テーブル操作)
  - [テーブルの作成](#テーブルの作成)
  - [テーブルの表示](#テーブルの表示)
  - [テーブルのカラム構造を表示](#テーブルのカラム構造を表示)
- [カラムの操作](#カラムの操作)
  - [カラムの追加](#カラムの追加)
  - [カラムの削除](#カラムの削除)
  - [カラムのデータ型を変更](#カラムのデータ型を変更)
  - [カラム名とデータ型を変更](#カラム名とデータ型を変更)
- [データの操作](#データの操作)
  - [データの挿入](#データの挿入)
  - [データの更新](#データの更新)
  - [テーブルのデータをすべて削除](#テーブルのデータをすべて削除)
  - [指定する条件に合致するデータを削除](#指定する条件に合致するデータを削除)
- [ファイルからのインポート](#ファイルからのインポート)


## データベースの操作

### データベースの一覧表示

```sql
SHOW DATABASES;
```

- `information_schema`が表示される
- `information_schema`：初期状態で用意されている、メタデータなどが格納されたデータベース

### データベースの作成

```sql
CREATE DATABASE <database_name>;
```

### データベースの削除

```sqL
DROP DATABASE <database_name>;
```

### 利用するデータベースの指定

```sql
USE <database_name>;
```

### 現在使用しているデータベースの表示

```sql
SELECT DATABASE();
```


## テーブル操作

### テーブルの作成

```sql
CREATE TABLE <table_name>(<column_name1> <value_type1>, <column_name2> <value_type2>, ...);
```

### テーブルの表示

```sql
SHOW TABLES;
```

### テーブルのカラム構造を表示

```sql
DESC <table_name>;
```


## カラムの操作

### カラムの追加

1. 最後に追加
  ```sql
  ALTER TABLE <table_name> ADD COLUMN <data_type>;
  ```

2. 先頭に追加
  ```sql
  ALTER TABLE <table_name> ADD COLUMN <data_type> FIRST;
  ```

3. 自由な位置に追加
  ```sql
  ALTER TABLE <table_name> ADD COLUMN <data_type> AFTER <column_name>;
  ```

### カラムの削除

```sql
ALTER TANLE <table_name> DROP <column_name>;
```

### カラムのデータ型を変更

```sql
ALTER TABLE <table_name> MODIFY <column_name> <data_type>;
```

### カラム名とデータ型を変更

```sql
ALTER TABLE <table_name> CHANGE <old_column_name> <new_column_name> <data_type>;
```


## データの操作

### データの挿入

```sql
INSERT INTO <table_name> (<column_name1>, <column_name2>) VALUES(value1, value2);
```

- カラム名を省略した場合、データが`CREATE`文で定義したカラムに対応する順で全て並んでいると見なされる

### データの更新

```sql
UPDATE <table_name> SET <column_name1>=<value1>, <column_name2>=<value2> WHERE <conditional_statement>;
```

### テーブルのデータをすべて削除

```sql
DELETE FROM <table_name>;
```

### 指定する条件に合致するデータを削除

```sql
DELETE FROM <table_name> WHERE <conditinal_statement>;
```

## ファイルからのインポート

```sql
SOURCE <file_name>;
```

- USE命令によって、事前に使用するデータベースを選択しておく必要がある
- `CREATE`, `INSERT`, `UPDATE`などを一気に実行可能