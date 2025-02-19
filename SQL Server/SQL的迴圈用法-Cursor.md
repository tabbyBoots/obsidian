[[SQL]] [[Cursor]] [[迴圈]]
[參考出處](https://hackmd.io/@johnsonnote/sqlds_sql_cursor)

程式撰寫迴圈，在SQL裡面就是使用 **Cusor** ， Cursor 會先從資料庫裡面讀出資料，暫存於 **tempDB** 資料庫內，再從 tempDB 逐筆讀出處理。

#### DECLARE Cursor 語法
標準語法
**ISO 語法**
```SQL
DECLARE cursor_name [ INSENSITIVE ] [ SCROLL ] CURSOR
    FOR select_statement
    [ FOR { READ_ONLY | UPDATE [ OF column_name [ , ...n ] ] } ]
[ ; ]
```

**Transact-SQL 擴充語法**
```SQL
DECLARE cursor_name CURSOR
    [ LOCAL | GLOBAL ]
    [ FORWARD_ONLY | SCROLL ]
    [ STATIC | KEYSET | DYNAMIC | FAST_FORWARD ]
    [ READ_ONLY | SCROLL_LOCKS | OPTIMISTIC ]
    [ TYPE_WARNING ]
FOR
    select_statement
[ FOR UPDATE [ OF column_name [ ,...n ] ] ]
```

#### OPEN Cursor 語法

```SQL
OPEN { { [ GLOBAL ] cursor_name } | cursor_variable_name } 
```

#### CLOSE Cursor 語法
```SQL
CLOSE { { [ GLOBAL ] cursor_name } | cursor_variable_name } 
```

#### DEALLOCATE Cursor 語法
```SQL
DEALLOCATE { { [ GLOBAL ] cursor_name } | @cursor_variable_name }   
```

#### FETCH Cursor 語法
```SQL
FETCH   
  [ [ NEXT | PRIOR | FIRST | LAST   
            | ABSOLUTE { n | @nvar }   
            | RELATIVE { n | @nvar }   
       ]   
       FROM   
  ]   
{ { [ GLOBAL ] cursor_name } | @cursor_variable_name }   
[ INTO @variable_name [ ,...n ] ] 
```