---
title: Создание, изменение и удаление хранимых процедур | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- stored procedures [SMO]
ms.assetid: 2a072f9c-8f11-4364-ab71-3990735a8d66
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: fe7fb603ae3b0f3550d63d4c9b886934b31a28ba
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48074504"
---
# <a name="creating-altering-and-removing-stored-procedures"></a>Создание, изменение и удаление хранимых процедур
  В [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] управляющих объектов (SMO), хранимые процедуры представляются <xref:Microsoft.SqlServer.Management.Smo.StoredProcedure> объекта.  
  
 Создание <xref:Microsoft.SqlServer.Management.Smo.StoredProcedure> объекта в SMO требует параметр <xref:Microsoft.SqlServer.Management.Smo.StoredProcedure.TextBody%2A> свойства [!INCLUDE[tsql](../../../includes/tsql-md.md)] сценарий, который определяет хранимую процедуру. Параметры требуют \@ префикса и должны создаваться отдельно с помощью <xref:Microsoft.SqlServer.Management.Smo.StoredProcedureParameter> объектов и добавления <xref:Microsoft.SqlServer.Management.Smo.StoredProcedureParameter> коллекцию <xref:Microsoft.SqlServer.Management.Smo.StoredProcedure> объекта.  
  
## <a name="example"></a>Пример  
 Чтобы использовать какой-либо из представленных примеров кода, нужно выбрать среду, шаблон и язык программирования, с помощью которых будет создаваться приложение. Дополнительные сведения см. в разделе [Создание проекта SMO на Visual Basic в Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) или [Visual C создайте&#35; проекта SMO в Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
## <a name="creating-altering-and-removing-a-stored-procedure-in-visual-basic"></a>Создание, изменение и удаление хранимой процедуры на языке Visual Basic  
 Данный пример кода показано, как создать хранимую процедуру для [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] базы данных. По идентификатору сотрудника пример возвращает фамилию этого сотрудника. Хранимая процедура требует один входной параметр для указания идентификатора сотрудника и один выходной параметр для возвращения последнего имени сотрудника.  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBStoredProcs1](SMO How to#SMO_VBStoredProcs1)]  -->  
  
## <a name="creating-altering-and-removing-a-stored-procedure-in-visual-c"></a>Создание, изменение и удаление хранимой процедуры на языке Visual C#  
 Данный пример кода показано, как создать хранимую процедуру для [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] базы данных. В этом примере возвращается фамилия сотрудника по его идентификатору (`BusinessEntityID`). Хранимая процедура требует один входной параметр для указания идентификатора сотрудника и один выходной параметр для возвращения последнего имени сотрудника.  
  
```  
{  
            //Connect to the local, default instance of SQL Server.   
            Server srv;  
            srv = new Server();  
            //Reference the AdventureWorks2012 database.   
            Database db;  
            db = srv.Databases["AdventureWorks2012"];  
            //Define a StoredProcedure object variable by supplying the parent database and name arguments in the constructor.   
            StoredProcedure sp;  
            sp = new StoredProcedure(db, "GetLastNameByBusinessEntityID");  
            //Set the TextMode property to false and then set the other object properties.   
            sp.TextMode = false;  
            sp.AnsiNullsStatus = false;  
            sp.QuotedIdentifierStatus = false;  
            //Add two parameters.   
            StoredProcedureParameter param;  
            param = new StoredProcedureParameter(sp, "@empval", DataType.Int);  
            sp.Parameters.Add(param);  
            StoredProcedureParameter param2;  
            param2 = new StoredProcedureParameter(sp, "@retval", DataType.NVarChar(50));  
            param2.IsOutputParameter = true;  
            sp.Parameters.Add(param2);  
            //Set the TextBody property to define the stored procedure.   
            string stmt;  
            stmt = " SELECT @retval = (SELECT LastName FROM Person.Person,HumanResources.Employee WHERE Person.Person.BusinessEntityID = HumanResources.Employee.BusinessentityID AND HumanResources.Employee.BusinessEntityID = @empval )";  
            sp.TextBody = stmt;  
            //Create the stored procedure on the instance of SQL Server.   
            sp.Create();  
            //Modify a property and run the Alter method to make the change on the instance of SQL Server.   
            sp.QuotedIdentifierStatus = true;  
            sp.Alter();  
            //Remove the stored procedure.   
            sp.Drop();  
        }  
```  
  
## <a name="creating-altering-and-removing-a-stored-procedure-in-powershell"></a>Создание, изменение и удаление хранимой процедуры в PowerShell  
 Данный пример кода показано, как создать хранимую процедуру для [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] базы данных. В этом примере возвращается фамилия сотрудника по его идентификатору (`BusinessEntityID`). Хранимая процедура требует один входной параметр для указания идентификатора сотрудника и один выходной параметр для возвращения последнего имени сотрудника.  
  
```  
# Set the path context to the local, default instance of SQL Server and get a reference to AdventureWorks2012  
CD \sql\localhost\default\databases  
$db = get-item Adventureworks2012  
  
# Define a StoredProcedure object variable by supplying the parent database and name arguments in the constructor.   
$sp  = New-Object -TypeName Microsoft.SqlServer.Management.SMO.StoredProcedure `  
-argumentlist $db, "GetLastNameByBusinessEntityID"  
  
#Set the TextMode property to false and then set the other object properties.   
$sp.TextMode = $false  
$sp.AnsiNullsStatus = $false  
$sp.QuotedIdentifierStatus = $false  
  
# Add two parameters  
$type = [Microsoft.SqlServer.Management.SMO.Datatype]::Int  
$param  = New-Object -TypeName Microsoft.SqlServer.Management.SMO.StoredProcedureParameter `  
-argumentlist $sp,"@empval",$type  
$sp.Parameters.Add($param)  
  
$type = [Microsoft.SqlServer.Management.SMO.DataType]::NVarChar(50)  
$param2  = New-Object -TypeName Microsoft.SqlServer.Management.SMO.StoredProcedureParameter `  
-argumentlist $sp,"@retval",$type  
$param2.IsOutputParameter = $true  
$sp.Parameters.Add($param2)  
  
#Set the TextBody property to define the stored procedure.   
$sp.TextBody =  " SELECT @retval = (SELECT LastName FROM Person.Person,HumanResources.Employee WHERE Person.Person.BusinessEntityID = HumanResources.Employee.BusinessentityID AND HumanResources.Employee.BusinessEntityID = @empval )"  
  
# Create the stored procedure on the instance of SQL Server.   
$sp.Create()  
  
# Modify a property and run the Alter method to make the change on the instance of SQL Server.   
$sp.QuotedIdentifierStatus = $true  
$sp.Alter()  
  
#Remove the stored procedure.   
$sp.Drop()  
```  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.SqlServer.Management.Smo.StoredProcedure>  
  
  
