<!-- omit in toc -->
# SQL

### 目次

- [基本構文](#基本構文)
- [絞り込みと並べ替え](#絞り込みと並べ替え)
- [集約関数](#集約関数)

## 基本構文

- `SELECT`：データの取得
  ```sql
  SELECT * FROM table;
  ```
  ```sql
  SELECT column1, column2,,, FROM table;
  ```

- `INSERT`：データの追加
  ```sql
  INSERT INTO table ( column1, column2,,, ) VALUES ( val1, val2,,, );
  ```

- `UPDATE`：データの更新
  ```sql
  UPDATE table SET column = val WHERE id = 1;
  ```

- `DELETE`：データの削除
  ```sql
  DELETE FROM table WHERE id = 1;
  ```

## 絞り込みと並べ替え

- `WHERE`：条件で絞り込み
  ```sql
  WHERE id = 1
  ```

- `ORDER BY`：並べ替え
  - 昇順
    ```sql
    SELECT * FROM table ORDER BY id ASC;
    ```
  - 降順
    ```sql
    SELECT * FROM table ORDER BY id DESC;
    ```

- `LIMIT`：取得件数制限
  ```sql
  LIMIT 5
  ```

## 集約関数

- `COUNT()`：レコードの数を数える
  ```sql
  SELECT COUNT(*) FROM table;
  ```

- `SUM()`：合計を計算する
  ```sql
  SELECT SUM(column) FROM table;
  ```

- `AVG()`：平均値を計算する
  ```sql
  SELECT AVG(column) FROM table;
  ```

- `MAX()`：最大値を取得する
  ```sql
  SELECT MAX(column) FROM table;
  ```

- `MIN()`：最小値を取得する
  ```sql
  SELECT MIN(column) FROM table;
  ```

<br>

- `GROUP BY`：グループごとに集計
  ```sql
  SELECT column, COUNT(*) FROM table GROUP BY  column;
  ```