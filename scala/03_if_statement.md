# if式

### 目次

- [if式](#if式-1)

<br>

## if式

- 基本文法
  
  ```scala
  val result = if (age >= 20) "adult" else "minor"
  ```

- Scalaではifは式（expression）であり、値を返す
  ```scala
  val status = if (age >= 65) "senior"
               else if (age >= 20) "adult"
               else "minor"
  ```

<br>

参照：[サンプルコード](00_sample_codes.md#3-if式)

<br>

→[4. コレクション（List）](04_list.md)