<!-- omit in toc -->
# ビュー

<!-- omit in toc -->
### 目次

- [ビューの定義](#ビューの定義)
- [テーブルの結合](#テーブルの結合)
  - [内部結合](#内部結合)
  - [外部結合](#外部結合)
    - [左外部結合](#左外部結合)
    - [右外部結合](#右外部結合)
- [ビューの上書き・変更](#ビューの上書き変更)
  - [ビューの上書き定義](#ビューの上書き定義)
  - [ビューのカラム構造変更](#ビューのカラム構造変更)
  - [ビューの削除](#ビューの削除)

## ビューの定義

```sql
CREATE VIEW <view_name> AS <select_statement>;
```

## テーブルの結合

### 内部結合

```sql
SELECT <column_name>
FROM <table_name1>
JOIN <table_name2>
ON <column_table1>=<column_table2>;
```

### 外部結合

指定したカラムの値が一致するデータに加えて、どちらか一方のテーブルにしか存在しないデータについても取得する

#### 左外部結合

結合する左テーブルの全行を出力

```sql
SELECT <column_name>
FROM <left_table>
LEFT JOIN <right_table>
ON <column_left_table>=<column_right_table>;
```

#### 右外部結合

結合する右テーブルの全行を出力

```sql
SELECT <column_name>
FROM <right_table>
RIGHT JOIN <left_table>
ON <column_left_table>=<column_right_table>;
```


## ビューの上書き・変更

### ビューの上書き定義

```sql
CREATE OR REPLACE VIEW <view_name>
AS select_statement;
```

### ビューのカラム構造変更

```sql
ALTER VIEW <view_name>
AS select_statement;
```

### ビューの削除

```sql
DROP VIEW <view_name>;
```