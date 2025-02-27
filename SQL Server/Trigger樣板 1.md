[[SQL]] [[Trigger]] [[template]]

```SQL
USE [demodb]
GO
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
-- =============================================
-- Author:		TabbyBoots
-- Create date: 2025-2-18
-- Description:	Calcuate total amount when Insert 
---             and Update records detected.
-- =============================================
CREATE TRIGGER [dbo].[tr_SaleDetail] 
   ON   [dbo].[SaleDetail]
   AFTER INSERT,DELETE,UPDATE
AS 
BEGIN
	SET NOCOUNT ON;
    
    -- Insert statements for trigger here

	--宣告變數	
	DECLARE @Id int = 0	

	--判斷 Trigger 指令類型
	IF(EXISTS(SELECT * FROM inserted) AND NOT EXISTS(SELECT * FROM deleted)) SET @Command = 'Insert'
	IF(NOT EXISTS(SELECT * FROM inserted) AND EXISTS(SELECT * FROM deleted)) SET @Command = 'Delete'
	IF(EXISTS(SELECT * FROM inserted) AND EXISTS(SELECT * FROM deleted)) SET @Command = 'Update'

	--Trigger 指令類型為新增或修改時時才要執行小計自動計算
	IF(@Command = 'Insert' OR @Command = 'Update')
	BEGIN
		SET @Id = (SELECT Id from inserted)
		
	--資料庫撈出來的資料要檢查是否為NULL
		IF (@Qty IS NULL) SET @Qty = 0
		IF (@Price IS NULL) SET @Price = 0
		SET @Amount = @Qty * @Price
		UPDATE [dbo].[SaleDetail] SET [Amount] = @Amount WHERE [Id] = @Id
	END
END
```

