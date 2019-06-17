---
title: Создание сценариев | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- dependencies [SMO]
- scripts [SMO]
ms.assetid: 13a35511-3987-426b-a3b7-3b2e83900dc7
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f10289e099a0c3b6400b71d972c6f749ffb76ff8
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63158783"
---
# <a name="scripting"></a>Написание скриптов
  Создание скрипта в SMO управляется объектом <xref:Microsoft.SqlServer.Management.Smo.Scripter> и его дочерними объектами или методом `Script` на отдельных объектах. <xref:Microsoft.SqlServer.Management.Smo.Scripter> Объекта управляет сопоставлением связей зависимости для объектов в экземпляре [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 Расширенное создание сценария с помощью объекта <xref:Microsoft.SqlServer.Management.Smo.Scripter> и его дочерних объектов является процессом из трех фаз.  
  
1.  Обнаружение  
  
2.  Создание списка  
  
3.  Создание скрипта  
  
 Фаза обнаружения использует объект <xref:Microsoft.SqlServer.Management.Smo.DependencyWalker>. Учитывая URN-список объектов, метод <xref:Microsoft.SqlServer.Management.Smo.DependencyWalker.DiscoverDependencies%2A> объекта <xref:Microsoft.SqlServer.Management.Smo.DependencyWalker> возвращает объект <xref:Microsoft.SqlServer.Management.Smo.DependencyTree> объектам в URN-списке. Логическое значение *fParents* параметр используется для выбора объектов, которые необходимо обнаружить родительских или дочерних элементов указанного объекта. На данном этапе можно изменить дерево зависимостей.  
  
 На фазе создания списка передается дерево и возвращается результирующий список. Данный список объекта существует в порядке создания сценария, и им можно управлять.  
  
 Фазы создания списка используют метод <xref:Microsoft.SqlServer.Management.Smo.DependencyWalker.WalkDependencies%2A> для возвращения объекта <xref:Microsoft.SqlServer.Management.Smo.DependencyTree>. На данной фазе можно изменить объект <xref:Microsoft.SqlServer.Management.Smo.DependencyTree>.  
  
 В третьей и последней фазе сценарий формируется с указанным списком и параметрами создания скриптов. Этот результат возвращается в виде системного объекта <xref:System.Collections.Specialized.StringCollection>. На этой фазе имена зависимых объектов извлекаются из коллекции Items объекта <xref:Microsoft.SqlServer.Management.Smo.DependencyTree> и свойств, таких как <xref:Microsoft.SqlServer.Management.Smo.DependencyTree.NumberOfSiblings%2A> и <xref:Microsoft.SqlServer.Management.Smo.DependencyTree.FirstChild%2A>.  
  
## <a name="example"></a>Пример  
 Чтобы использовать какой-либо из представленных примеров кода, нужно выбрать среду, шаблон и язык программирования, с помощью которых будет создаваться приложение. Дополнительные сведения см. в разделе [Создание проекта SMO на Visual Basic в Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) или [Visual C создайте&#35; проекта SMO в Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
 Данный пример кода требует инструкцию `Imports` для пространства имен System.Collections.Specialized. Вставьте инструкцию с другими инструкциями Imports и перед любыми декларациями в приложении.  
  
```  
Imports Microsoft.SqlServer.Management.Smo  
Imports Microsoft.SqlServer.Management.Common  
Imports System.Collections.Specialized  
```  
  
## <a name="scripting-out-the-dependencies-for-a-database-in-visual-basic"></a>Создание сценария зависимостей для базы данных на языке Visual Basic  
 Данный пример кода показывает, как обнаруживать зависимости и просматривать список для отображения результатов.  
  
```  
' compile with:   
' /r:Microsoft.SqlServer.Smo.dll   
' /r:Microsoft.SqlServer.ConnectionInfo.dll   
' /r:Microsoft.SqlServer.Management.Sdk.Sfc.dll   
  
Imports Microsoft.SqlServer.Management.Smo  
Imports Microsoft.SqlServer.Management.Sdk.Sfc  
  
Public Class A  
   Public Shared Sub Main()  
      ' database name  
      Dim dbName As [String] = "AdventureWorksLT2012"   ' database name  
  
      ' Connect to the local, default instance of SQL Server.   
      Dim srv As New Server()  
  
      ' Reference the database.    
      Dim db As Database = srv.Databases(dbName)  
  
      ' Define a Scripter object and set the required scripting options.   
      Dim scrp As New Scripter(srv)  
      scrp.Options.ScriptDrops = False  
      scrp.Options.WithDependencies = True  
      scrp.Options.Indexes = True   ' To include indexes  
      scrp.Options.DriAllConstraints = True   ' to include referential constraints in the script  
  
      ' Iterate through the tables in database and script each one. Display the script.  
      For Each tb As Table In db.Tables  
         ' check if the table is not a system table  
         If tb.IsSystemObject = False Then  
            Console.WriteLine("-- Scripting for table " + tb.Name)  
  
            ' Generating script for table tb  
            Dim sc As System.Collections.Specialized.StringCollection = scrp.Script(New Urn() {tb.Urn})  
            For Each st As String In sc  
               Console.WriteLine(st)  
            Next  
            Console.WriteLine("--")  
         End If  
      Next  
   End Sub  
End Class  
```  
  
## <a name="scripting-out-the-dependencies-for-a-database-in-visual-c"></a>Создание сценария зависимостей для базы данных на языке Visual C#  
 Данный пример кода показывает, как обнаруживать зависимости и просматривать список для отображения результатов.  
  
```  
// compile with:   
// /r:Microsoft.SqlServer.Smo.dll   
// /r:Microsoft.SqlServer.ConnectionInfo.dll   
// /r:Microsoft.SqlServer.Management.Sdk.Sfc.dll   
  
using System;  
using Microsoft.SqlServer.Management.Smo;  
using Microsoft.SqlServer.Management.Sdk.Sfc;  
  
public class A {  
   public static void Main() {   
      String dbName = "AdventureWorksLT2012"; // database name  
  
      // Connect to the local, default instance of SQL Server.   
      Server srv = new Server();  
  
      // Reference the database.    
      Database db = srv.Databases[dbName];  
  
      // Define a Scripter object and set the required scripting options.   
      Scripter scrp = new Scripter(srv);  
      scrp.Options.ScriptDrops = false;  
      scrp.Options.WithDependencies = true;  
      scrp.Options.Indexes = true;   // To include indexes  
      scrp.Options.DriAllConstraints = true;   // to include referential constraints in the script  
  
      // Iterate through the tables in database and script each one. Display the script.     
      foreach (Table tb in db.Tables) {   
         // check if the table is not a system table  
         if (tb.IsSystemObject == false) {  
            Console.WriteLine("-- Scripting for table " + tb.Name);  
  
            // Generating script for table tb  
            System.Collections.Specialized.StringCollection sc = scrp.Script(new Urn[]{tb.Urn});  
            foreach (string st in sc) {  
               Console.WriteLine(st);  
            }  
            Console.WriteLine("--");  
         }  
      }   
   }  
}  
```  
  
## <a name="scripting-out-the-dependencies-for-a-database-in-powershell"></a>Создание сценария зависимостей для базы данных в PowerShell  
 Данный пример кода показывает, как обнаруживать зависимости и просматривать список для отображения результатов.  
  
```  
# Set the path context to the local, default instance of SQL Server.  
CD \sql\localhost\default  
  
# Create a Scripter object and set the required scripting options.  
$scrp = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Scripter -ArgumentList (Get-Item .)  
$scrp.Options.ScriptDrops = $false  
$scrp.Options.WithDependencies = $true  
$scrp.Options.IncludeIfNotExists = $true  
  
# Set the path context to the tables in AdventureWorks2012.  
  
CD Databases\AdventureWorks2012\Tables  
  
foreach ($Item in Get-ChildItem)  
 {    
 $scrp.Script($Item)  
 }  
```  
  
  
