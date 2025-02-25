### [[SQL]] [[AI]] [[Excel]] [[TSQL]]
 >how to export query result from MS SQL 2022 to a excel spreadsheet
 >
 >Exporting the results of an MS SQL Server 2022 query to an Excel spreadsheet is a common task and can be accomplished in several ways. Below are some methods you can use:

### Method 1: Using SSMS (SQL Server Management Studio)
1. **Open SQL Server Management Studio (SSMS)** and connect to your SQL Server instance.
2. Run the query you want to export.
3. Right-click on the result grid and select "Export Data to Excel..." or "Export To" if it's available in newer versions of SSMS.
4. Follow the prompts in the Export Settings dialog to configure how you want your data exported (e.g., format, sheet name, etc.).
5. Click "OK" to start the export process and save the file.

### Method 2: Using T-SQL Command
You can use a T-SQL command to directly export the results to an Excel file. This requires having SQL Server Agent enabled on your server.

```sql
-- Create a job that runs the query 
-- and exports it to Excel

DECLARE @sqlcommand NVARCHAR(MAX)
SET @sqlcommand = N'SELECT Product.ProductNo, Product.ProductName, Product.ProductSpec, Product.VendorNo, Vendor.ShortName
FROM Product 
LEFT OUTER JOIN Vendor 
ON Product.VendorNo = Vendor.VendorNo;' 
-- Replace with your actual query

EXEC sp_start_job
@job_name='ExportToExcel',
@step_name='Export Step',
@step_id=1,
@database_name='demodb', --YourDatabase
@subsystem='TSQL',
@command=@sqlcommand,
@output_file_name='D:\QryResult.xlsx'; 
-- Specify the path where you want to save the file
```


### Method 3: Using PowerShell with SQL Server Module for Powershell
You can use a PowerShell script that leverages the SQL Server module for PowerShell to execute your query and export it to Excel.

1. Install the SQL Server module for PowerShell if you haven't already:
   ```powershell
   Install-Module -Name SqlServer -Scope CurrentUser
   ```

2. Run the following PowerShell script:
```powershell
   Import-Module SqlServer

   $query = 'SELECT Product.ProductNo, Product.ProductName, Product.ProductSpec, Product.VendorNo, Vendor.ShortName FROM Product LEFT OUTER JOIN Vendor ON Product.VendorNo = Vendor.VendorNo;' 
# Replace with your actual query
   $serverName = "localhost"
   $databaseName = 'demodb'
   $filePath = 'D:\QryResult.xlsx'
# Specify the path where you want to save the file

   Invoke-Sqlcmd -Query $query -ServerInstance $serverName -Database $databaseName | Export-Excel -Path $filePath
```


