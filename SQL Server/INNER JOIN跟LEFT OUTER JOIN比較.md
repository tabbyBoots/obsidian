[[SQL]] [[JOIN]] [[INNER JOIN]] [[LEFT OUTER JOIN]]

#### 結論：
##### 一般情況用LEFT OUTER JOIN比較適合，因為**總筆數不會少**
```SQL
--列出儲存地點
SELECT PlaceNo , PlaceName FROM Place ORDER BY PlaceNo

--列出商品名稱
SELECT ProductNo , ProductName , ProductSpec , PlaceNo FROM Product 
ORDER BY ProductNo

--顯示商品名稱，並從儲存地點取得地點名稱
--用INNER JOIN可以取得
--但是商品儲存地點代號找不到的就不會列出來
SELECT ProductNo , ProductName , ProductSpec, Place.PlaceName
FROM Product
INNER JOIN Place ON Place.PlaceNo = Product.PlaceNo

--顯示商品名稱，並從儲存地點取得地點名稱
--用LEFT OUTER JOIN可以取得，
--其中商品儲存地點代號找不到的，
--一樣會顯示，所以總筆數不會少，只是代號找不到會顯示NULL
SELECT ProductNo , ProductName , ProductSpec, Place.PlaceName
FROM Product
LEFT OUTER JOIN Place ON Place.PlaceNo = Product.PlaceNo
```
