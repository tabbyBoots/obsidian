[[SQL]] [[Cursor]] [[迴圈]]
[參考出處](https://hackmd.io/@johnsonnote/sqlds_sql_cursor)

```SQL
--宣告Cursor要用的參數
DECLARE @SaleAmount int = 0 --銷售總額，變數型態要跟資料表一樣
DECLARE @TotalAmout int = 0 --合計銷售總額
DECLARE @StartDate date = CAST('2022-01-03' AS Date) --開始日期
DECLARE @EndDate date = CAST('2022-01-10' AS Date) --開始日期

--宣告並建立CURSOR物件，取得指定日期範圍的銷售記錄檔中的銷售金額
DECLARE SaleCursor CURSOR LOCAL FAST_FORWARD FOR
	SELECT SaleAmount 
	FROM SaleRecord 
	WHERE SaleDate BETWEEN @StartDate AND @EndDate 
	ORDER BY SaleAmount ASC

--開啟Cursor
OPEN SaleCursor

--讀取第一筆記錄到變數
FETCH NEXT FROM SaleCursor INTO @SaleAmount;

--跑迴圈讀取每一筆記錄
--status為0表示讀取成功
--status為-1表示讀取失敗
--status為-2表示記錄不存在
WHILE @@FETCH_STATUS = 0 
BEGIN
	--(要迴圈執行的程式碼)
	--因為取得的資料可能為NULL，所以要檢查
	IF (@SaleAmount IS NULL) SET @SaleAmount = 0
	SET @TotalAmout += @SaleAmount
	--讀取下一筆記錄
	FETCH NEXT FROM SaleCursor INTO @SaleAmount;
END;

--關閉Cursor
CLOSE SaleCursor;
DEALLOCATE SaleCursor;

SELECT @SaleAmount AS 銷售總額
SELECT @TotalAmout AS 合計銷售總額 --用SELECT會顯示在結果
```

