[[SQL]] [[CTE]] [[單遞迴]]

以下以員工主檔中的單位主管來讀出各單位主管下屬員工明細為例，其中單位主管是有上下級結構的

![image](https://hackmd.io/_uploads/rkM5Dw4b1g.png)

```SQL
WITH HierarchyCTE AS
(
	SELECT A.BossNo, A.EmpNo, A.EmpName
	FROM Employee AS A
	WHERE A.BossNo = 'E003'
	UNION ALL
	SELECT B.BossNo, B.EmpNo, B.EmpName
	FROM Employee AS B
	INNER JOIN HierarchyCTE AS H ON B.BossNo = H.EmpNo
	--INNER JOIN Employee AS H ON B.BossNo = H.EmpNo
)
SELECT H.BossNo, E.EmpName, H.EmpNo, H.EmpName
FROM HierarchyCTE AS H
LEFT OUTER JOIN Employee AS E ON H.BossNo = E.EmpNo
```

![image](https://hackmd.io/_uploads/r1iWv_NZ1x.png)