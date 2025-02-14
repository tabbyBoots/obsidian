### [[SQL]] [[SSMS]] [[backup]] [[database]]


```SQL
use [master]

-- 開啟 xp_cmdshell

EXEC sp_configure 'show advanced options', 1;

GO

RECONFIGURE;

GO

EXEC sp_configure 'xp_cmdshell', 1;

GO

RECONFIGURE;

GO

  

--宣告變數

DECLARE @BackupFolderName nvarchar(250) = ''

DECLARE @DataBaseName nvarchar(250) = ''

DECLARE @JobName nvarchar(250) = ''

DECLARE @KeepDays int = 0

DECLARE @FolderName nvarchar(250) = ''

DECLARE @FileName nvarchar(250) = ''

DECLARE @FileDate nvarchar(250) = ''

DECLARE @Command nvarchar(250) = ''

  

---設定變數預設值

SET @BackupFolderName = 'D:\DB_backup'   --備份資料夾名稱

SET @DataBaseName = 'demoSQLdb'   --備份資料庫名稱

SET @JobName = @DataBaseName + ' 資料庫備份工作' --備份工作名稱

SET @KeepDays = 30  --保留備份檔天數

  

--取得日期變數 , 例 2013-01-01 12:30:40.001

SET @FileDate = CONVERT(NVARCHAR(250), GETDATE(), 121)

  

--除去日期變數中的 - : . 符號 , 例 20130101_123040_001

SET @FileDate = REPLACE( @FileDate , '-' , '' )

SET @FileDate = REPLACE( @FileDate , ':' , '' )

SET @FileDate = REPLACE( @FileDate , '.' , '_' )

SET @FileDate = REPLACE( @FileDate , ' ' , '_' )

  

--設定備份目錄,並自動以年、月建立目錄

SET @FolderName = @BackupFolderName

SET @Command = 'mkdir ' + @FolderName

EXEC xp_cmdshell @Command, no_output

  

SET @FolderName = @FolderName + '\' + @DataBaseName

SET @Command = 'mkdir ' + @FolderName

EXEC xp_cmdshell @Command, no_output

  

SET @FolderName = @FolderName + '\' + SUBSTRING(@FileDate , 1 , 4)

SET @Command = 'mkdir ' + @FolderName

EXEC xp_cmdshell @Command, no_output

  

SET @FolderName = @FolderName + '\' + SUBSTRING(@FileDate , 5 , 2)

SET @Command = 'mkdir ' + @FolderName

EXEC xp_cmdshell @Command, no_output

  

--設定檔案名稱 , 例 D:\dbbackup\demodb\2013\01\demodb_20130101_123040.bak

SET @FileName = @FolderName + '\' + @DataBaseName + '_' +SUBSTRING(@FileDate , 1 , 15) + '.bak'

  

--執行備份作業

BACKUP DATABASE @DataBaseName TO DISK = @FileName WITH NOINIT , NOUNLOAD , NAME = @JobName , NOSKIP , STATS = 10, NOFORMAT

  

--刪除過期備份檔案

SET @KeepDays *= -1

SET @FileDate = CONVERT(NVARCHAR(250), DATEADD(day , @KeepDays , GETDATE()) , 121)

SET @FileDate = REPLACE( @FileDate , '-' , '' )

SET @FileDate = REPLACE( @FileDate , ':' , '' )

SET @FileDate = REPLACE( @FileDate , '.' , '_' )

SET @FileDate = REPLACE( @FileDate , ' ' , '_' )

  

SET @FolderName = @BackupFolderName

SET @FolderName += '\' + @DataBaseName

SET @FolderName += '\' + SUBSTRING(@FileDate , 1 , 4)

SET @FolderName += '\' + SUBSTRING(@FileDate , 5 , 2)

SET @FileName = SUBSTRING(@FileDate , 1 , 8) + '*.bak'

SET @Command = 'del ' + @FolderName + '\' + @DataBaseName + '_' + @FileName + ' /f /q'

EXEC xp_cmdshell @Command, no_output

  

IF SUBSTRING(@FileDate , 7 , 2) = '01'

BEGIN

    SET @Command = 'rmdir ' + @FolderName + ' /s /q'

    EXEC xp_cmdshell @Command, no_output

END

  

-- 關閉 xp_cmdshell

use [master]

EXEC sp_configure 'show advanced options', 0;

GO

EXEC sp_configure 'xp_cmdshell', 0;

GO

RECONFIGURE;

GO
```

