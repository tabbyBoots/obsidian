[[SQL]] [[CTE]]

簡單的CTE查詢

```SQL
WITH DepartmentCTE (部門代號, 員工姓名) AS
(
	SELECT DeptNo, EmpName
	FROM Employee
	WHERE DeptNo = 'D01'
)
SELECT *
FROM DepartmentCTE
```

![image](https://hackmd.io/_uploads/BktO0I4WJl.png)