---
title: Создание, изменение и удаление определяемых пользователем функций | Документация Майкрософт
ms.custom: ''
ms.date: 08/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- user-defined functions [SMO]
ms.assetid: 0ebebd3b-0775-41c2-989d-aa4cf81af12a
author: markingmyname
ms.author: maghan
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: dd6a7b8817e86207e9e8c8df2270344d5106ead3
ms.sourcegitcommit: f3f83ef95399d1570851cd1360dc2f072736bef6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/13/2019
ms.locfileid: "70148484"
---
# <a name="creating-altering-and-removing-user-defined-functions"></a>Создание, изменение и удаление определяемых пользователем функций
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]
  Объект предоставляет функциональные возможности, позволяющие пользователям программно управлять определяемыми пользователем функциями в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. [!INCLUDE[msCoName](../../../includes/msconame-md.md)] <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunction> Определяемые пользователем функции поддерживают входные и выходные параметры, а также прямые ссылки на столбцы таблицы.  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] требует, чтобы сборки были зарегистрированы внутри базы данных до того, как их можно будет использовать внутри хранимых процедур, определяемых пользователем функций и типов данных. SMO поддерживает эту функцию при помощи объекта <xref:Microsoft.SqlServer.Management.Smo.SqlAssembly>.  
  
 Объект <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunction> указывает на сборку .NET со свойствами <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunction.AssemblyName%2A>, <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunction.ClassName%2A> и <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunction.MethodName%2A>.  
  
 Когда объект <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunction> указывает на сборку .NET, необходимо ее зарегистрировать путем создания объекта <xref:Microsoft.SqlServer.Management.Smo.SqlAssembly> и его добавления в объект <xref:Microsoft.SqlServer.Management.Smo.SqlAssemblyCollection>, принадлежащий объекту <xref:Microsoft.SqlServer.Management.Smo.Database>.  
  
## <a name="example"></a>Пример  
 Чтобы использовать какой-либо из представленных примеров кода, нужно выбрать среду, шаблон и язык программирования, с помощью которых будет создаваться приложение. Дополнительные сведения см. [в разделе Создание проекта Visual&#35; C SMO в Visual Studio .NET](../../../relational-databases/server-management-objects-smo/how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
## <a name="creating-a-scalar-user-defined-function-in-visual-basic"></a>Создание определяемой пользователем скалярной функции на языке Visual Basic  
 Данный пример кода показывает, как на языке [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] создать и удалить определяемую пользователем скалярную функцию, имеющую входной параметр объекта <xref:System.DateTime> и возвращаемый тип integer. Функция, определяемая пользователем, создается в базе данных [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] . Пример создает определяемую пользователем функцию ISOweek, которая получает в качестве аргумента дату и вычисляет номер недели по ISO. Для правильной работы этой функции перед ее вызовом параметр базы данных DATEFIRST должен быть установлен в значение 1.  
  
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
 Данный пример кода показывает, как на языке [!INCLUDE[csprcs](../../../includes/csprcs-md.md)] создать и удалить определяемую пользователем скалярную функцию, имеющую входной параметр объекта <xref:System.DateTime> и возвращаемый тип integer. Функция, определяемая пользователем, создается в базе данных [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] . В примере показано создание определяемой пользователем функции `ISOweek`. которая получает в качестве аргумента дату и вычисляет номер недели по ISO. Для правильной работы этой функции перед ее вызовом параметр базы данных `DATEFIRST` должен быть установлен в значение `1` .  
  
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
 Данный пример кода показывает, как на языке [!INCLUDE[csprcs](../../../includes/csprcs-md.md)] создать и удалить определяемую пользователем скалярную функцию, имеющую входной параметр объекта <xref:System.DateTime> и возвращаемый тип integer. Функция, определяемая пользователем, создается в базе данных [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] . В примере показано создание определяемой пользователем функции `ISOweek`. которая получает в качестве аргумента дату и вычисляет номер недели по ISO. Для правильной работы этой функции перед ее вызовом параметр базы данных `DATEFIRST` должен быть установлен в значение `1` .  
  
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
  
  
