---
title: Создание, изменение и удаление значений по умолчанию | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- defaults [SMO]
ms.assetid: c30ac3b9-8150-4264-ba4c-c549f44261ab
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: dcc29aa897674ae61d6bc5e8a53abe109661ebbc
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "72797159"
---
# <a name="creating-altering-and-removing-defaults"></a>Создание, изменение и удаление используемых по умолчанию значений
  В управляющих объектах [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (SMO) значение по умолчанию представлено объектом <xref:Microsoft.SqlServer.Management.Smo.Default>.  
  
 Свойство <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.TextBody%2A> объекта <xref:Microsoft.SqlServer.Management.Smo.Default> используется, чтобы установить вставляемое значение. Это может быть константа или инструкция [!INCLUDE[tsql](../../../includes/tsql-md.md)] , возвращающая значение константы, такая как GETDATE(). Свойство <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.TextBody%2A> не может быть изменено методом <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A>. Вместо этого объект <xref:Microsoft.SqlServer.Management.Smo.Default> необходимо удалить и создать заново.  
  
## <a name="example"></a>Пример  
 Чтобы использовать какой-либо из представленных примеров кода, нужно выбрать среду, шаблон и язык программирования, с помощью которых будет создаваться приложение. Дополнительные сведения см. в статьях [Создание проекта Visual Basic SMO в Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) или [Создание проекта Visual C&#35; SMO в Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
## <a name="creating-altering-and-removing-a-default-in-visual-basic"></a>Создание, изменение и удаление значения по умолчанию на языке Visual Basic  
 Этот пример кода показывает, как создать одно значение по умолчанию, являющееся простым текстом, и другое значение по умолчанию, представляющее собой инструкцию [!INCLUDE[tsql](../../../includes/tsql-md.md)] . Значение по умолчанию необходимо присоединять к столбцу с помощью метода <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.BindToColumn%2A> и отсоединять с помощью метода <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.UnbindFromColumn%2A>.  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBDefaults1](SMO How to#SMO_VBDefaults1)]  -->  
  
## <a name="creating-altering-and-removing-a-default-in-visual-c"></a>Создание, изменение и удаление значения по умолчанию на языке Visual C#  
 Этот пример кода показывает, как создать одно значение по умолчанию, являющееся простым текстом, и другое значение по умолчанию, представляющее собой инструкцию [!INCLUDE[tsql](../../../includes/tsql-md.md)] . Значение по умолчанию необходимо присоединять к столбцу с помощью метода <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.BindToColumn%2A> и отсоединять с помощью метода <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.UnbindFromColumn%2A>.  
  
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
 Этот пример кода показывает, как создать одно значение по умолчанию, являющееся простым текстом, и другое значение по умолчанию, представляющее собой инструкцию [!INCLUDE[tsql](../../../includes/tsql-md.md)] . Значение по умолчанию необходимо присоединять к столбцу с помощью метода <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.BindToColumn%2A> и отсоединять с помощью метода <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.UnbindFromColumn%2A>.  
  
```powershell
# Set the path context to the local, default instance of SQL Server and get a reference to AdventureWorks2012  
CD \sql\localhost\default\databases  
$db = Get-Item Adventureworks2012  
  
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
  
## <a name="see-also"></a>См. также:  
 <xref:Microsoft.SqlServer.Management.Smo.Default>  
