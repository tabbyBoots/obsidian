### [[SQL]]

between**有包含上下限**，要注意
```SQL
SELECT * FROM StandardPrice WHERE StandardPrice BETWEEN 20 AND 80

SELECT * FROM StandardPrice WHERE StandardPrice > 20 AND StandardPrice < 80
```

![[2025-02-13 09_21_20-Window.png]]