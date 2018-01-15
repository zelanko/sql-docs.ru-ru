---
title: "Создание, изменение и удаление значения по умолчанию | Документы Microsoft"
ms.custom: 
ms.date: 08/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: smo
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: defaults [SMO]
ms.assetid: c30ac3b9-8150-4264-ba4c-c549f44261ab
caps.latest.revision: "46"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: edd16a7f12eef15d28508c01744537a4aa67e346
ms.sourcegitcommit: cb2f9d4db45bef37c04064a9493ac2c1d60f2c22
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/12/2018
---
# <a name="creating-altering-and-removing-defaults"></a>Создание, изменение и удаление используемых по умолчанию значений
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

  В управляющих объектах [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (SMO) значение по умолчанию представлено объектом <xref:Microsoft.SqlServer.Management.Smo.Default>.  
  
 Свойство <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.TextBody%2A> объекта <xref:Microsoft.SqlServer.Management.Smo.Default> используется, чтобы установить вставляемое значение. Это может быть константа или инструкция [!INCLUDE[tsql](../../../includes/tsql-md.md)], возвращающая значение константы, такая как GETDATE(). Свойство <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.TextBody%2A> не может быть изменено методом <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A>. Вместо этого объект <xref:Microsoft.SqlServer.Management.Smo.Default> необходимо удалить и создать заново.  
  
## <a name="example"></a>Пример  
 Чтобы использовать какой-либо из представленных примеров кода, нужно выбрать среду, шаблон и язык программирования, с помощью которых будет создаваться приложение. Дополнительные сведения см. в разделе [Create Visual C# 35; Проект SMO в Visual Studio .NET](../../../relational-databases/server-management-objects-smo/how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
## <a name="creating-altering-and-removing-a-default-in-visual-basic"></a>Создание, изменение и удаление значения по умолчанию на языке Visual Basic  
 Этот пример кода показывает, как создать одно значение по умолчанию, являющееся простым текстом, и другое значение по умолчанию, представляющее собой инструкцию [!INCLUDE[tsql](../../../includes/tsql-md.md)]. Значение по умолчанию необходимо присоединять к столбцу с помощью метода <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.BindToColumn%2A> и отсоединять с помощью метода <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.UnbindFromColumn%2A>.  
  
```VBNET
'Connect to the local, default instance of SQL Server.
Dim srv As Server
srv = New Server
'Reference the AdventureWorks2012 database.
Dim db As Database
db = srv.Databases("AdventureWorks2012")
'Define a Default object variable by supplying the parent database and the default name 
'in the constructor.
Dim def As [Default]
def = New [Default](db, "Test_Default2")
'Set the TextHeader and TextBody properties that define the default.
def.TextHeader = "CREATE DEFAULT [Test_Default2] AS"
def.TextBody = "GetDate()"
'Create the default on the instance of SQL Server.
def.Create()
'Declare a Column object variable and reference a column in the AdventureWorks2012 database.
Dim col As Column
col = db.Tables("SpecialOffer", "Sales").Columns("StartDate")
'Bind the default to the column.
def.BindToColumn("SpecialOffer", "StartDate", "Sales")
'Unbind the default from the column and remove it from the database.
def.UnbindFromColumn("SpecialOffer", "StartDate", "Sales")
def.Drop()
```
  
## <a name="creating-altering-and-removing-a-default-in-visual-c"></a>Создание, изменение и удаление значения по умолчанию на языке Visual C#  
 Этот пример кода показывает, как создать одно значение по умолчанию, являющееся простым текстом, и другое значение по умолчанию, представляющее собой инструкцию [!INCLUDE[tsql](../../../includes/tsql-md.md)]. Значение по умолчанию необходимо присоединять к столбцу с помощью метода <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.BindToColumn%2A> и отсоединять с помощью метода <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.UnbindFromColumn%2A>.  
  
```csharp  
{  
  
          Server srv = new Server();  
  
            //Reference the AdventureWorks2012 database.   
            Database  db = srv.Databases["AdventureWorks2012"];  
  
            //Define a Default object variable by supplying the parent database and the default name   
            //in the constructor.   
            Default def = new Default(db, "Test_Default2");  
  
            //Set the TextHeader and TextBody properties that define the default.   
            def.TextHeader = "CREATE DEFAULT [Test_Default2] AS";  
            def.TextBody = "GetDate()";  
  
            //Create the default on the instance of SQL Server.   
            def.Create();  
  
            //Bind the default to a column in a table in AdventureWorks2012  
            def.BindToColumn("SpecialOffer", "StartDate", "Sales");  
  
            //Unbind the default from the column and remove it from the database.   
            def.UnbindFromColumn("SpecialOffer", "StartDate", "Sales");  
            def.Drop();  
        }  
```  
  
## <a name="creating-altering-and-removing-a-default-in-powershell"></a>Создание, изменение и удаление значения по умолчанию в PowerShell  
 Этот пример кода показывает, как создать одно значение по умолчанию, являющееся простым текстом, и другое значение по умолчанию, представляющее собой инструкцию [!INCLUDE[tsql](../../../includes/tsql-md.md)]. Значение по умолчанию необходимо присоединять к столбцу с помощью метода <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.BindToColumn%2A> и отсоединять с помощью метода <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.UnbindFromColumn%2A>.  
  
```powershell   
# Set the path context to the local, default instance of SQL Server and get a reference to AdventureWorks2012  
CD \sql\localhost\default\databases  
$db = get-item Adventureworks2012  
  
#Define a Default object variable by supplying the parent database and the default name in the constructor.  
$def = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Default `  
-argumentlist $db, "Test_Default2"  
  
#Set the TextHeader and TextBody properties that define the default.   
$def.TextHeader = "CREATE DEFAULT [Test_Default2] AS"  
$def.TextBody = "GetDate()"  
  
#Create the default on the instance of SQL Server.   
$def.Create()  
  
#Bind the default to the column.   
$def.BindToColumn("SpecialOffer", "StartDate", "Sales")  
  
#Unbind the default from the column and remove it from the database.   
$def.UnbindFromColumn("SpecialOffer", "StartDate", "Sales")  
$def.Drop()  
```  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.SqlServer.Management.Smo.Default>  
  
  
