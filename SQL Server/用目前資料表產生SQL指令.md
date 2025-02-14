### [[SQL]] [[SSMS]] [[database]]

``資料庫`` ``> 工作`` ``> 產生指令碼``

![[2025-02-07 14_16_08-.png]]

## 產生結果
```SQL
USE [demoSQLdb]
GO
IF  EXISTS (SELECT * FROM sys.fn_listextendedproperty(N'MS_Description' , N'SCHEMA',N'dbo', N'TABLE',N'ZipRoad', N'COLUMN',N'Remark'))
EXEC sys.sp_dropextendedproperty @name=N'MS_Description' , @level0type=N'SCHEMA',@level0name=N'dbo', @level1type=N'TABLE',@level1name=N'ZipRoad', @level2type=N'COLUMN',@level2name=N'Remark'
GO
IF  EXISTS (SELECT * FROM sys.fn_listextendedproperty(N'MS_Description' , N'SCHEMA',N'dbo', N'TABLE',N'ZipRoad', N'COLUMN',N'RoadName'))
EXEC sys.sp_dropextendedproperty @name=N'MS_Description' , @level0type=N'SCHEMA',@level0name=N'dbo', @level1type=N'TABLE',@level1name=N'ZipRoad', @level2type=N'COLUMN',@level2name=N'RoadName'
GO
IF  EXISTS (SELECT * FROM sys.fn_listextendedproperty(N'MS_Description' , N'SCHEMA',N'dbo', N'TABLE',N'ZipRoad', N'COLUMN',N'AreaNo'))
EXEC sys.sp_dropextendedproperty @name=N'MS_Description' , @level0type=N'SCHEMA',@level0name=N'dbo', @level1type=N'TABLE',@level1name=N'ZipRoad', @level2type=N'COLUMN',@level2name=N'AreaNo'
GO
IF  EXISTS (SELECT * FROM sys.fn_listextendedproperty(N'MS_Description' , N'SCHEMA',N'dbo', N'TABLE',N'ZipRoad', N'COLUMN',N'CityNo'))
EXEC sys.sp_dropextendedproperty @name=N'MS_Description' , @level0type=N'SCHEMA',@level0name=N'dbo', @level1type=N'TABLE',@level1name=N'ZipRoad', @level2type=N'COLUMN',@level2name=N'CityNo'
GO
IF  EXISTS (SELECT * FROM sys.fn_listextendedproperty(N'MS_Description' , N'SCHEMA',N'dbo', N'TABLE',N'ZipRoad', N'COLUMN',N'Id'))
EXEC sys.sp_dropextendedproperty @name=N'MS_Description' , @level0type=N'SCHEMA',@level0name=N'dbo', @level1type=N'TABLE',@level1name=N'ZipRoad', @level2type=N'COLUMN',@level2name=N'Id'
GO
IF  EXISTS (SELECT * FROM sys.fn_listextendedproperty(N'MS_Description' , N'SCHEMA',N'dbo', N'TABLE',N'ZipCity', N'COLUMN',N'Remark'))
EXEC sys.sp_dropextendedproperty @name=N'MS_Description' , @level0type=N'SCHEMA',@level0name=N'dbo', @level1type=N'TABLE',@level1name=N'ZipCity', @level2type=N'COLUMN',@level2name=N'Remark'
GO
IF  EXISTS (SELECT * FROM sys.fn_listextendedproperty(N'MS_Description' , N'SCHEMA',N'dbo', N'TABLE',N'ZipCity', N'COLUMN',N'CityName'))
EXEC sys.sp_dropextendedproperty @name=N'MS_Description' , @level0type=N'SCHEMA',@level0name=N'dbo', @level1type=N'TABLE',@level1name=N'ZipCity', @level2type=N'COLUMN',@level2name=N'CityName'
GO
IF  EXISTS (SELECT * FROM sys.fn_listextendedproperty(N'MS_Description' , N'SCHEMA',N'dbo', N'TABLE',N'ZipCity', N'COLUMN',N'CityNo'))
EXEC sys.sp_dropextendedproperty @name=N'MS_Description' , @level0type=N'SCHEMA',@level0name=N'dbo', @level1type=N'TABLE',@level1name=N'ZipCity', @level2type=N'COLUMN',@level2name=N'CityNo'
GO
IF  EXISTS (SELECT * FROM sys.fn_listextendedproperty(N'MS_Description' , N'SCHEMA',N'dbo', N'TABLE',N'ZipCity', N'COLUMN',N'Id'))
EXEC sys.sp_dropextendedproperty @name=N'MS_Description' , @level0type=N'SCHEMA',@level0name=N'dbo', @level1type=N'TABLE',@level1name=N'ZipCity', @level2type=N'COLUMN',@level2name=N'Id'
GO
IF  EXISTS (SELECT * FROM sys.fn_listextendedproperty(N'MS_Description' , N'SCHEMA',N'dbo', N'TABLE',N'ZipArea', N'COLUMN',N'Remark'))
EXEC sys.sp_dropextendedproperty @name=N'MS_Description' , @level0type=N'SCHEMA',@level0name=N'dbo', @level1type=N'TABLE',@level1name=N'ZipArea', @level2type=N'COLUMN',@level2name=N'Remark'
GO
IF  EXISTS (SELECT * FROM sys.fn_listextendedproperty(N'MS_Description' , N'SCHEMA',N'dbo', N'TABLE',N'ZipArea', N'COLUMN',N'AreaName'))
EXEC sys.sp_dropextendedproperty @name=N'MS_Description' , @level0type=N'SCHEMA',@level0name=N'dbo', @level1type=N'TABLE',@level1name=N'ZipArea', @level2type=N'COLUMN',@level2name=N'AreaName'
GO
IF  EXISTS (SELECT * FROM sys.fn_listextendedproperty(N'MS_Description' , N'SCHEMA',N'dbo', N'TABLE',N'ZipArea', N'COLUMN',N'AreaNo'))
EXEC sys.sp_dropextendedproperty @name=N'MS_Description' , @level0type=N'SCHEMA',@level0name=N'dbo', @level1type=N'TABLE',@level1name=N'ZipArea', @level2type=N'COLUMN',@level2name=N'AreaNo'
GO
IF  EXISTS (SELECT * FROM sys.fn_listextendedproperty(N'MS_Description' , N'SCHEMA',N'dbo', N'TABLE',N'ZipArea', N'COLUMN',N'CityNo'))
EXEC sys.sp_dropextendedproperty @name=N'MS_Description' , @level0type=N'SCHEMA',@level0name=N'dbo', @level1type=N'TABLE',@level1name=N'ZipArea', @level2type=N'COLUMN',@level2name=N'CityNo'
GO
IF  EXISTS (SELECT * FROM sys.fn_listextendedproperty(N'MS_Description' , N'SCHEMA',N'dbo', N'TABLE',N'ZipArea', N'COLUMN',N'Id'))
EXEC sys.sp_dropextendedproperty @name=N'MS_Description' , @level0type=N'SCHEMA',@level0name=N'dbo', @level1type=N'TABLE',@level1name=N'ZipArea', @level2type=N'COLUMN',@level2name=N'Id'
GO
/****** Object:  Table [dbo].[ZipRoad]    Script Date: 2025/2/7 下午 02:13:22 ******/
DROP TABLE IF EXISTS [dbo].[ZipRoad]
GO
/****** Object:  Table [dbo].[ZipCity]    Script Date: 2025/2/7 下午 02:13:22 ******/
DROP TABLE IF EXISTS [dbo].[ZipCity]
GO
/****** Object:  Table [dbo].[ZipArea]    Script Date: 2025/2/7 下午 02:13:22 ******/
DROP TABLE IF EXISTS [dbo].[ZipArea]
GO

CREATE TABLE [dbo].[ZipArea](
	[Id] [int] IDENTITY(1,1) NOT NULL,
	[CityNo] [nvarchar](50) NULL,
	[AreaNo] [nvarchar](50) NULL,
	[AreaName] [nvarchar](50) NULL,
	[Remark] [nvarchar](250) NULL,
 CONSTRAINT [PK_ZipArea] PRIMARY KEY CLUSTERED 
(
	[Id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[ZipCity]    Script Date: 2025/2/7 下午 02:13:22 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[ZipCity](
	[Id] [int] IDENTITY(1,1) NOT NULL,
	[CityNo] [nvarchar](50) NULL,
	[CityName] [nvarchar](50) NULL,
	[Remark] [nvarchar](250) NULL,
 CONSTRAINT [PK_ZipCity] PRIMARY KEY CLUSTERED 
(
	[Id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
GO

CREATE TABLE [dbo].[ZipRoad](
	[Id] [int] IDENTITY(1,1) NOT NULL,
	[CityNo] [nvarchar](50) NULL,
	[AreaNo] [nvarchar](50) NULL,
	[RoadName] [nvarchar](50) NULL,
	[Remark] [nvarchar](250) NULL,
 CONSTRAINT [PK_ZipRoad] PRIMARY KEY CLUSTERED 
(
	[Id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
GO
EXEC sys.sp_addextendedproperty @name=N'MS_Description', @value=N'區域主檔' , @level0type=N'SCHEMA',@level0name=N'dbo', @level1type=N'TABLE',@level1name=N'ZipArea', @level2type=N'COLUMN',@level2name=N'Id'
GO
EXEC sys.sp_addextendedproperty @name=N'MS_Description', @value=N'縣市代號' , @level0type=N'SCHEMA',@level0name=N'dbo', @level1type=N'TABLE',@level1name=N'ZipArea', @level2type=N'COLUMN',@level2name=N'CityNo'
GO
EXEC sys.sp_addextendedproperty @name=N'MS_Description', @value=N'區域代號' , @level0type=N'SCHEMA',@level0name=N'dbo', @level1type=N'TABLE',@level1name=N'ZipArea', @level2type=N'COLUMN',@level2name=N'AreaNo'
GO
EXEC sys.sp_addextendedproperty @name=N'MS_Description', @value=N'區域名稱' , @level0type=N'SCHEMA',@level0name=N'dbo', @level1type=N'TABLE',@level1name=N'ZipArea', @level2type=N'COLUMN',@level2name=N'AreaName'
GO
EXEC sys.sp_addextendedproperty @name=N'MS_Description', @value=N'備註' , @level0type=N'SCHEMA',@level0name=N'dbo', @level1type=N'TABLE',@level1name=N'ZipArea', @level2type=N'COLUMN',@level2name=N'Remark'
GO
EXEC sys.sp_addextendedproperty @name=N'MS_Description', @value=N'城市主檔' , @level0type=N'SCHEMA',@level0name=N'dbo', @level1type=N'TABLE',@level1name=N'ZipCity', @level2type=N'COLUMN',@level2name=N'Id'
GO
EXEC sys.sp_addextendedproperty @name=N'MS_Description', @value=N'縣市代號' , @level0type=N'SCHEMA',@level0name=N'dbo', @level1type=N'TABLE',@level1name=N'ZipCity', @level2type=N'COLUMN',@level2name=N'CityNo'
GO
EXEC sys.sp_addextendedproperty @name=N'MS_Description', @value=N'城市名稱' , @level0type=N'SCHEMA',@level0name=N'dbo', @level1type=N'TABLE',@level1name=N'ZipCity', @level2type=N'COLUMN',@level2name=N'CityName'
GO
EXEC sys.sp_addextendedproperty @name=N'MS_Description', @value=N'備註' , @level0type=N'SCHEMA',@level0name=N'dbo', @level1type=N'TABLE',@level1name=N'ZipCity', @level2type=N'COLUMN',@level2name=N'Remark'
GO
EXEC sys.sp_addextendedproperty @name=N'MS_Description', @value=N'道路主檔' , @level0type=N'SCHEMA',@level0name=N'dbo', @level1type=N'TABLE',@level1name=N'ZipRoad', @level2type=N'COLUMN',@level2name=N'Id'
GO
EXEC sys.sp_addextendedproperty @name=N'MS_Description', @value=N'縣市代號' , @level0type=N'SCHEMA',@level0name=N'dbo', @level1type=N'TABLE',@level1name=N'ZipRoad', @level2type=N'COLUMN',@level2name=N'CityNo'
GO
EXEC sys.sp_addextendedproperty @name=N'MS_Description', @value=N'區域代號' , @level0type=N'SCHEMA',@level0name=N'dbo', @level1type=N'TABLE',@level1name=N'ZipRoad', @level2type=N'COLUMN',@level2name=N'AreaNo'
GO
EXEC sys.sp_addextendedproperty @name=N'MS_Description', @value=N'道路名稱' , @level0type=N'SCHEMA',@level0name=N'dbo', @level1type=N'TABLE',@level1name=N'ZipRoad', @level2type=N'COLUMN',@level2name=N'RoadName'
GO
EXEC sys.sp_addextendedproperty @name=N'MS_Description', @value=N'備註' , @level0type=N'SCHEMA',@level0name=N'dbo', @level1type=N'TABLE',@level1name=N'ZipRoad', @level2type=N'COLUMN',@level2name=N'Remark'
GO
```



