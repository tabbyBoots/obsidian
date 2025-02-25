[[SQL]] [[Triger]]

[參考出處](https://hackmd.io/@johnsonnote/sqlds_sql_trigger)

觸發程序 **是一種特殊的預存程序，其會在資料庫伺服器發生事件時自動執行** 。 當使用者試圖透過資料操作語言 (DML) 事件來修改資料時，便會執行DML 觸發程序。 DML 事件包括資料表或檢視的INSERT、UPDATE 或 DELETE 陳述式。 無論資料表的資料列有無受到影響，這些觸發程序皆會在引發任何有效事件時引發。

語法
```SQL
CREATE [ OR ALTER ] TRIGGER [ schema_name . ]trigger_name   
ON { table | view }   
[ WITH <dml_trigger_option> [ ,...n ] ]  
{ FOR | AFTER | INSTEAD OF }   
{ [ INSERT ] [ , ] [ UPDATE ] [ , ] [ DELETE ] }   
[ WITH APPEND ]  
[ NOT FOR REPLICATION ]   
AS { sql_statement  [ ; ] [ ,...n ] | EXTERNAL NAME <method specifier [ ; ] > }  
  
<dml_trigger_option> ::=  
    [ ENCRYPTION ]  
    [ EXECUTE AS Clause ]  
  
<method_specifier> ::=  
    assembly_name.class_name.method_name  
```

觸發程序緩衝區

觸發程序緩衝區有兩個

| 緩衝區      | 說明              |
| -------- | --------------- |
| Inserted | 使用者新增後的資料會存放在這裏 |
| Deleted  | 使用者刪除後的資料會存放在這裏 |
![](https://hackmd.io/_uploads/B1n4XaQLs.png)

### 每個資料表都有Trigger程序，可以按右鍵新增

![[新增Trigger.png]]

![[2025-02-18 16_04_40-Window.png]]
