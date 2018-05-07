---
title: Создание, изменение и удаление определяемых пользователем функций | Документы Microsoft
ms.custom: ''
ms.date: 08/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: smo
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- user-defined functions [SMO]
ms.assetid: 0ebebd3b-0775-41c2-989d-aa4cf81af12a
caps.latest.revision: 49
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 70176012dc61676a9c6b2193c8ca9034aa871284
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="creating-altering-and-removing-user-defined-functions"></a>Создание, изменение и удаление определяемых пользователем функций
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]
  <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunction> Объект предоставляет функциональные возможности, разрешающие пользователям программно управлять определяемых пользователем функций в [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Определяемые пользователем функции поддерживают входные и выходные параметры, а также прямые ссылки на столбцы таблицы.  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] требует, чтобы сборки были зарегистрированы внутри базы данных, прежде чем они могут использоваться внутри хранимой процедуры, определяемые пользователем функции, триггеры и определяемые пользователем типы данных. SMO поддерживает эту функцию при помощи объекта <xref:Microsoft.SqlServer.Management.Smo.SqlAssembly>.  
  
 <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunction> Объект ссылается на сборку .NET со <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunction.AssemblyName%2A>, <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunction.ClassName%2A>, и <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunction.MethodName%2A> свойства.  
  
 При <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunction> объект ссылается на сборку .NET, необходимо зарегистрировать сборку путем создания <xref:Microsoft.SqlServer.Management.Smo.SqlAssembly> объекта и его добавления в <xref:Microsoft.SqlServer.Management.Smo.SqlAssemblyCollection> объекта, который принадлежит <xref:Microsoft.SqlServer.Management.Smo.Database> объекта.  
  
## <a name="example"></a>Пример  
 Чтобы использовать какой-либо из представленных примеров кода, нужно выбрать среду, шаблон и язык программирования, с помощью которых будет создаваться приложение. Дополнительные сведения см. в разделе [создать Visual C&#35; проекта SMO в Visual Studio .NET](../../../relational-databases/server-management-objects-smo/how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
## <a name="creating-a-scalar-user-defined-function-in-visual-basic"></a>Создание определяемой пользователем скалярной функции на языке Visual Basic  
 Данный пример кода показано, как создавать и удалять скалярной определяемой пользователем функции, имеющую входной <xref:System.DateTime> параметр объекта и целое возвращаемый тип [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]. Определяемая пользователем функция создается на [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] базы данных. Пример создает определяемую пользователем функцию ISOweek, которая получает в качестве аргумента дату и вычисляет номер недели по ISO. Для правильной работы этой функции перед ее вызовом параметр базы данных DATEFIRST должен быть установлен в значение 1.  
  
```VBNET
'Connect to the local, default instance of SQL Server.
Dim srv As Server
srv = New Server
'Reference the AdventureWorks2012 2008R2 database.
Dim db As Database
db = srv.Databases("AdventureWorks2012")
'Define a UserDefinedFunction object variable by supplying the parent database and the name arguments in the constructor.
Dim udf As UserDefinedFunction
udf = New UserDefinedFunction(db, "IsOWeek")
'Set the TextMode property to false and then set the other properties.
udf.TextMode = False
udf.DataType = DataType.Int
udf.ExecutionContext = ExecutionContext.Caller
udf.FunctionType = UserDefinedFunctionType.Scalar
udf.ImplementationType = ImplementationType.TransactSql
'Add a parameter.
Dim par As UserDefinedFunctionParameter
par = New UserDefinedFunctionParameter(udf, "@DATE", DataType.DateTime)
udf.Parameters.Add(par)
'Set the TextBody property to define the user defined function.
udf.TextBody = "BEGIN  DECLARE @ISOweek int SET @ISOweek= DATEPART(wk,@DATE)+1 -DATEPART(wk,CAST(DATEPART(yy,@DATE) as CHAR(4))+'0104') IF (@ISOweek=0) SET @ISOweek=dbo.ISOweek(CAST(DATEPART(yy,@DATE)-1 AS CHAR(4))+'12'+ CAST(24+DATEPART(DAY,@DATE) AS CHAR(2)))+1 IF ((DATEPART(mm,@DATE)=12) AND ((DATEPART(dd,@DATE)-DATEPART(dw,@DATE))>= 28)) SET @ISOweek=1 RETURN(@ISOweek) END;"
'Create the user defined function on the instance of SQL Server.
udf.Create()
'Remove the user defined function.
udf.Drop()
``` 
  
## <a name="creating-a-scalar-user-defined-function-in-visual-c"></a>Создание определяемой пользователем скалярной функции на языке Visual C#  
 Данный пример кода показано, как создавать и удалять скалярной определяемой пользователем функции, имеющую входной <xref:System.DateTime> параметр объекта и целое возвращаемый тип [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]. Определяемая пользователем функция создается на [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] базы данных. В примере показано создание определяемой пользователем функции `ISOweek`. Эта функция получает в качестве аргумента дату и вычисляет номер недели по ISO. Для правильной работы этой функции перед ее вызовом параметр базы данных `DATEFIRST` должен быть установлен в значение `1` .  
  
```csharp  
{  
            //Connect to the local, default instance of SQL Server.   
           Server srv = new Server();  
            //Reference the AdventureWorks2012 database.   
           Database db = srv.Databases["AdventureWorks2012"];  
  
            //Define a UserDefinedFunction object variable by supplying the parent database and the name arguments in the constructor.   
            UserDefinedFunction udf = new UserDefinedFunction(db, "IsOWeek");  
  
            //Set the TextMode property to false and then set the other properties.   
            udf.TextMode = false;  
            udf.DataType = DataType.Int;  
            udf.ExecutionContext = ExecutionContext.Caller;  
            udf.FunctionType = UserDefinedFunctionType.Scalar;  
            udf.ImplementationType = ImplementationType.TransactSql;  
  
            //Add a parameter.   
  
     UserDefinedFunctionParameter par = new UserDefinedFunctionParameter(udf, "@DATE", DataType.DateTime);  
            udf.Parameters.Add(par);  
  
            //Set the TextBody property to define the user-defined function.   
            udf.TextBody = "BEGIN DECLARE @ISOweek int SET @ISOweek= DATEPART(wk,@DATE)+1 -DATEPART(wk,CAST(DATEPART(yy,@DATE) as CHAR(4))+'0104') IF (@ISOweek=0) SET @ISOweek=dbo.ISOweek(CAST(DATEPART(yy,@DATE)-1 AS CHAR(4))+'12'+ CAST(24+DATEPART(DAY,@DATE) AS CHAR(2)))+1 IF ((DATEPART(mm,@DATE)=12) AND ((DATEPART(dd,@DATE)-DATEPART(dw,@DATE))>= 28)) SET @ISOweek=1 RETURN(@ISOweek) END;";  
  
            //Create the user-defined function on the instance of SQL Server.   
            udf.Create();  
  
            //Remove the user-defined function.   
            udf.Drop();  
        }  
```  
  
## <a name="creating-a-scalar-user-defined-function-in-powershell"></a>Создание определяемой пользователем скалярной функции в PowerShell  
 Данный пример кода показано, как создавать и удалять скалярной определяемой пользователем функции, имеющую входной <xref:System.DateTime> параметр объекта и целое возвращаемый тип [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]. Определяемая пользователем функция создается на [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] базы данных. В примере показано создание определяемой пользователем функции `ISOweek`. Эта функция получает в качестве аргумента дату и вычисляет номер недели по ISO. Для правильной работы этой функции перед ее вызовом параметр базы данных `DATEFIRST` должен быть установлен в значение `1` .  
  
```powershell   
# Set the path context to the local, default instance of SQL Server and get a reference to AdventureWorks2012  
CD \sql\localhost\default\databases  
$db = get-item Adventureworks2012  
  
# Define a user defined function object variable by supplying the parent database and name arguments in the constructor.   
$udf  = New-Object -TypeName Microsoft.SqlServer.Management.SMO.UserDefinedFunction `  
-argumentlist $db, "IsOWeek"  
  
# Set the TextMode property to false and then set the other properties.   
$udf.TextMode = $false  
$udf.DataType = [Microsoft.SqlServer.Management.SMO.DataType]::Int   
$udf.ExecutionContext = [Microsoft.SqlServer.Management.SMO.ExecutionContext]::Caller  
$udf.FunctionType = [Microsoft.SqlServer.Management.SMO.UserDefinedFunctionType]::Scalar  
$udf.ImplementationType = [Microsoft.SqlServer.Management.SMO.ImplementationType]::TransactSql  
  
# Define a Parameter object variable by supplying the parent function, name and type arguments in the constructor.  
$type = [Microsoft.SqlServer.Management.SMO.DataType]::DateTime  
$par  = New-Object -TypeName Microsoft.SqlServer.Management.SMO.UserDefinedFunctionParameter `  
-argumentlist $udf, "@DATE",$type  
  
# Add the parameter to the function  
$udf.Parameters.Add($par)  
  
#Set the TextBody property to define the user-defined function.   
$udf.TextBody = "BEGIN DECLARE @ISOweek int SET @ISOweek= DATEPART(wk,@DATE)+1 -DATEPART(wk,CAST(DATEPART(yy,@DATE) as CHAR(4))+'0104') IF (@ISOweek=0) SET @ISOweek=dbo.ISOweek(CAST(DATEPART(yy,@DATE)-1 AS CHAR(4))+'12'+ CAST(24+DATEPART(DAY,@DATE) AS CHAR(2)))+1 IF ((DATEPART(mm,@DATE)=12) AND ((DATEPART(dd,@DATE)-DATEPART(dw,@DATE))>= 28)) SET @ISOweek=1 RETURN(@ISOweek) END;"  
  
# Create the user-defined function on the instance of SQL Server.   
$udf.Create()  
  
# Remove the user-defined function.   
$udf.Drop()  
```  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunction>  
  
  
