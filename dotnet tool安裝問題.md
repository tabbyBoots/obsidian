[[dotnet]] [[nuget]] [[Visual Studio]]

以下系統工具為適合 [ASP.NET](http://ASP.NET) MVC 開發的相關系統工具，開啟終端機，輸入以下指令進行安裝。

開啟 **DOS 命令提示字元** ，將以下指令貼上執行

```bash
dotnet tool uninstall --global dotnet-aspnet-codegenerator 
dotnet tool uninstall --global dotnet-ef
dotnet tool uninstall -g Microsoft.Web.LibraryManager.Cli
dotnet tool install --global dotnet-aspnet-codegenerator
dotnet tool install --global dotnet-ef
dotnet tool install -g Microsoft.Web.LibraryManager.Cli
```

若``dotnet tool install --global dotnet-aspnet-codegenerator``有問題
可以下這個指令，新增 **Nuget** 套件來源

``dotnet nuget add source https://api.nuget.org/v3/index.json -n nuget.org``

或是可以在**Visual Studio**中的**Nuget套件管理**新增

![[2025-02-20 10_20_43-Microsoft Visual Studio.png]]

![[2025-02-20 10_21_37-Microsoft Visual Studio.png]]