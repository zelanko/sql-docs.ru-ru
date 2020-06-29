---
title: Программное перечисление доступных пакетов | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- programmatically enumerate packages [SSIS]
- existence testing [Integration Services]
- enumerating packages [Integration Services]
ms.assetid: 254ec7ee-d3ff-4361-8995-46e9b9c4dc95
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0b432398f7151f5cd08546a5145d43b41f085bd1
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/26/2020
ms.locfileid: "85422881"
---
# <a name="enumerating-available-packages-programmatically"></a>Программное перечисление доступных пакетов
  Во время обработки пакетов служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] программным путем может потребоваться определить, существует ли отдельный пакет или папка, или перечислить сохраненные пакеты, которые доступны для загрузки и выполнения. Класс <xref:Microsoft.SqlServer.Dts.Runtime.Application> из пространства имен <xref:Microsoft.SqlServer.Dts.Runtime> предоставляет разнообразные методы, выполняющие эти требования.  
  
##  <a name="determining-whether-a-package-or-folder-exists"></a><a name="exists"></a> Определение существования пакета или папки  
 Чтобы определить программно, существует ли сохраненный пакет, вызовите один из следующих методов перед тем, как пытаться загрузить и выполнить пакет.  
  
|Место хранения|Вызываемый метод|  
|----------------------|--------------------|  
|Хранилище пакетов служб SSIS|<xref:Microsoft.SqlServer.Dts.Runtime.Application.ExistsOnDtsServer%2A>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.ExistsOnSqlServer%2A>|  
  
 Чтобы определить программно, существует ли папка, прежде чем пытаться перечислить сохраненные в ней пакеты, вызовите один из следующих методов.  
  
|Место хранения|Вызываемый метод|  
|----------------------|--------------------|  
|Хранилище пакетов служб SSIS|<xref:Microsoft.SqlServer.Dts.Runtime.Application.FolderExistsOnDtsServer%2A>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.FolderExistsOnSqlServer%2A>|  
  
 [Вверх](#top)  
  
##  <a name="enumerating-available-packages"></a><a name="listing"></a> Перечисление доступных пакетов  
 Чтобы получить программным путем список сохраненных пакетов, вызовите один из следующих методов.  
  
|Место хранения|Вызываемый метод|  
|----------------------|--------------------|  
|Хранилище пакетов служб SSIS|<xref:Microsoft.SqlServer.Dts.Runtime.Application.GetDtsServerPackageInfos%2A>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.GetPackageInfos%2A>|  
  
 Приложения командной строки в следующих образцах иллюстрируют использование этих методов.  
  
###  <a name="example-ssis-package-store"></a><a name="listing_store"></a> Пример (хранилище пакетов служб SSIS)  
 Используйте метод <xref:Microsoft.SqlServer.Dts.Runtime.Application.GetDtsServerPackageInfos%2A> для перечисления пакетов, сохраненных в хранилище пакетов служб SSIS. Местом хранения по умолчанию, которое управляется хранилищем пакетов служб SSIS, является файловая система и MSDB. В этих местах можно создать дополнительные логические папки.  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
  
Module Module1  
  
  Sub Main()  
  
    Dim sqlFolder As String  
    Dim sqlServer As String  
  
    Dim ssisApplication As Application  
    Dim sqlPackages As PackageInfos  
    Dim sqlPackage As PackageInfo  
  
    sqlServer = "."  
  
    ssisApplication = New Application()  
  
    ' Get packages stored in MSDB.  
    sqlFolder = "MSDB"  
    sqlPackages = ssisApplication.GetDtsServerPackageInfos(sqlFolder, sqlServer)  
    If sqlPackages.Count > 0 Then  
      Console.WriteLine("Packages stored in MSDB:")  
      For Each sqlPackage In sqlPackages  
        Console.WriteLine(sqlPackage.Name)  
      Next  
      Console.WriteLine()  
    End If  
  
    ' Get packages stored in the File System.  
    sqlFolder = "File System"  
    sqlPackages = ssisApplication.GetDtsServerPackageInfos(sqlFolder, sqlServer)  
    If sqlPackages.Count > 0 Then  
      Console.WriteLine("Packages stored in the File System:")  
      For Each sqlPackage In sqlPackages  
        Console.WriteLine(sqlPackage.Name)  
      Next  
    End If  
  
    Console.Read()  
  
  End Sub  
  
End Module  
```  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
  
namespace EnumeratePackagesSSIS_CS  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
  
      string sqlFolder;  
      string sqlServer;  
  
      Application ssisApplication;  
      PackageInfos sqlPackages;  
  
      sqlServer = ".";  
  
      ssisApplication = new Application();  
  
      // Get packages stored in MSDB.  
      sqlFolder = "MSDB";  
      sqlPackages = ssisApplication.GetDtsServerPackageInfos(sqlFolder, sqlServer);  
      if (sqlPackages.Count > 0)  
      {  
        Console.WriteLine("Packages stored in MSDB:");  
        foreach (PackageInfo sqlPackage in sqlPackages)  
        {  
          Console.WriteLine(sqlPackage.Name);  
        }  
        Console.WriteLine();  
      }  
  
      // Get packages stored in the File System.  
      sqlFolder = "File System";  
      sqlPackages = ssisApplication.GetDtsServerPackageInfos(sqlFolder, sqlServer);  
      if (sqlPackages.Count > 0)  
      {  
        Console.WriteLine("Packages stored in the File System:");  
        foreach (PackageInfo sqlPackage in sqlPackages)  
        {  
          Console.WriteLine(sqlPackage.Name);  
        }  
      }  
  
      Console.Read();  
  
    }  
  
  }  
  
}  
```  
  
 [Вверх](#top)  
  
###  <a name="example-sql-server"></a><a name="listing_sql"></a> Пример (SQL Server)  
 Используйте метод <xref:Microsoft.SqlServer.Dts.Runtime.Application.GetPackageInfos%2A> для перечисления пакетов служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], хранящихся в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
  
Module Module1  
  
  Sub Main()  
  
    Dim sqlFolder As String  
    Dim sqlServer As String  
    Dim sqlUser As String  
    Dim sqlPassword As String  
  
    Dim ssisApplication As Application  
    Dim sqlPackages As PackageInfos  
    Dim sqlPackage As PackageInfo  
  
    sqlFolder = String.Empty  
    sqlServer = "(local)"  
    sqlUser = String.Empty  
    sqlPassword = String.Empty  
  
    ssisApplication = New Application()  
  
    sqlPackages = ssisApplication.GetPackageInfos(sqlFolder, sqlServer, sqlUser, sqlPassword)  
  
    For Each sqlPackage In sqlPackages  
      Console.WriteLine(sqlPackage.Name)  
    Next  
  
    Console.Read()  
  
  End Sub  
  
End Module  
```  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
  
namespace EnumeratePackagesSql_CS  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
  
      string sqlFolder;  
      string sqlServer;  
      string sqlUser;  
      string sqlPassword;  
  
      Application ssisApplication;  
      PackageInfos sqlPackages;  
  
      sqlFolder = String.Empty;  
      sqlServer = "(local)";  
      sqlUser = String.Empty;  
      sqlPassword = String.Empty;  
  
      ssisApplication = new Application();  
  
      sqlPackages = ssisApplication.GetPackageInfos(sqlFolder, sqlServer, sqlUser, sqlPassword);  
  
      foreach (PackageInfo sqlPackage in sqlPackages)  
      {  
        Console.WriteLine(sqlPackage.Name);  
      }  
  
      Console.Read();  
  
    }  
  }  
}  
```  
  
 [Вверх](#top)  
  
![Значок Integration Services (маленький)](../media/dts-16.gif "Значок служб Integration Services (маленький)")  **следит за обновлениями Integration Services**<br /> Чтобы загрузить новейшую документацию, статьи, образцы и видеоматериалы корпорации Майкрософт, а также лучшие решения участников сообщества, посетите страницу служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] на сайте MSDN:<br /><br /> [Посетить страницу «Службы Integration Services» на сайте MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Чтобы получать автоматические уведомления об этих обновлениях, подпишитесь на RSS-каналы, предлагаемые на этой странице.  
  
## <a name="see-also"></a>См. также  
 [Управление пакетами (службы SSIS)](../service/package-management-ssis-service.md)  
  
  
