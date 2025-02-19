[[SQL]] [[CTE]] [[簡化查詢]]
CTE 可以用來分解複雜的查詢，使其更易於理解和維護。例如：
以下以銷售記錄檔為例，列出所有商品的總銷售額，並且不顯示低於 10000 的總銷售額商品記錄。

Left outer join Product跟SaleRecord兩個資料表

```SQL
WITH SaleCTE AS
(
SELECT ProductNo, SUM(SaleAmount) AS totalSales
FROM SaleRecord
GROUP BY ProductNo
)
SELECT S.ProductNo, P.ProductName, S.totalSales
FROM SaleCTE AS S
LEFT OUTER JOIN Product as P ON P.ProductNo = S.ProductNo
WHERE S.totalSales > 100000
ORDER BY S.totalSales DESC;
```

