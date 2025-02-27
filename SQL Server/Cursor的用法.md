[[SQL]] [[TSQL]] [[Cursor]]

#### 宣告Cursor
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

**游標有效範圍**：**LOCAL** 或 **GLOBAL**
**游標讀取方式**：**FORWARD_ONLY** 或 **SCROLL**
**Concurrency Options**：是否鎖定
**游標型態：STATIC | KEYSET | DYNAMIC | FAST_FORWARD**
##### 範例：
```SQL
--宣告並建立 Cursor 物件, 取得需要 Table 中所有指定欄位的資料 

DECLARE @ColName NVARCHAR(50)
DECLARE TableCursor CURSOR LOCAL FAST_FORWARD FOR SELECT ColName FROM TableName ORDER BY ColName
```

--開啟 Cursor 
``OPEN TableCursor``
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

##### 範例：
```SQL
--讀取第一筆記錄值到變數中
FETCH NEXT FROM TableCursor INTO @ColumnName;
```

#### 每筆資料提取完成後，檢查提取狀態，若還有資料，用while迴圈繼續拿資料

```SQL
--跑迴圈讀取每一筆記錄 
WHILE @@FETCH_STATUS = 0 
BEGIN 

--(其它處理的程式) 

--讀取下一筆記錄 
FETCH NEXT FROM TableCursor INTO @ColumnName; 
END;
```

**提取狀態 - @@FETCH_STATUS**
	**0** : 提取成功 
	**-1** : 提取失敗  
	**-2** : 要獲取之記錄已不存在

#### 關閉並釋放Cursor
```SQL
CLOSE TableCursor; 
DEALLOCATE TableCursor;
```

