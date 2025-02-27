[[SQL]] [[Cursor]] [[迴圈]]
[參考出處](https://hackmd.io/@johnsonnote/sqlds_sql_cursor)

```SQL
--宣告Cursor要用的參數
DECLARE @SaleAmount NVARCHAR(50)

--宣告並建立CURSOR物件，取得指定欄位資料
DECLARE TableCursor CURSOR LOCAL FAST_FORWARD FOR
	SELECT SaleAmount 
	FROM SaleRecord  
	ORDER BY SaleAmount

--開啟Cursor
OPEN TableCursor

--讀取第一筆記錄到變數
FETCH NEXT FROM TableCursor INTO @SaleAmount;

--跑迴圈讀取每一筆記錄
WHILE @@FETCH_STATUS = 0
BEGIN
	--(要迴圈執行的程式碼)

	--讀取下一筆記錄
	FETCH NEXT FROM TableCursor INTO @SaleAmount;
END;

--關閉Cursor
CLOSE TableCursor;
DEALLOCATE TableCursor;

PRINT　@SaleAmount; --用PRINT會顯示在訊息
SELECT @SaleAmount AS 銷售總額 --用SELECT會顯示在結果
```