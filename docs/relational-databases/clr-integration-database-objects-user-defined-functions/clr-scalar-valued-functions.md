---
title: Функции CLR с скалярными значениями | Документация Майкрософт
description: Скалярная функция возвращает одно значение. В SQL Server интеграции со средой CLR можно написать скалярные определяемые пользователем функции в управляемом коде.
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
dev_langs:
- TSQL
- VB
- CSharp
helpviewer_keywords:
- SVF
- scalar-valued functions
ms.assetid: 20dcf802-c27d-4722-9cd3-206b1e77bee0
author: rothja
ms.author: jroth
ms.openlocfilehash: a44187fc41409d149501c4cda7e99817be034a12
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81488439"
---
# <a name="clr-scalar-valued-functions"></a>Скалярные функции среды CLR
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Скалярная функция возвращает единственное значение, например строку, целочисленное или битовое значение. В управляемом коде можно создавать скалярные определяемые пользователем функции, используя любой язык программирования .NET Framework. Эти функции доступны для [!INCLUDE[tsql](../../includes/tsql-md.md)] и другого управляемого кода. Сведения о преимуществах интеграции со средой CLR и выборе между управляемым [!INCLUDE[tsql](../../includes/tsql-md.md)]кодом и см. в разделе [Обзор интеграции со средой CLR](../../relational-databases/clr-integration/clr-integration-overview.md).  
  
## <a name="requirements-for-clr-scalar-valued-functions"></a>Требования к скалярным функциям среды CLR  
 Скалярные функции .NET Framework реализуются в виде методов класса в сборке .NET Framework. Типами входных параметров и типом, возвращаемым скалярной функцией, могут быть любые типы данных, которые поддерживаются в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], за исключением **varchar**, **char**, **rowversion**, **text**, **ntext**, **image**, **timestamp**, **table**и **cursor**. Скалярные функции должны обеспечивать соответствие типа данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и типа данных, возвращаемого методом реализации. Дополнительные сведения о преобразовании типов см. в разделе [сопоставление данных параметров CLR](../../relational-databases/clr-integration-database-objects-types-net-framework/mapping-clr-parameter-data.md).  
  
 При реализации скалярной функции .NET Framework на одном из языков .NET Framework можно включить дополнительные сведения о функции, задав пользовательский атрибут **SqlFunction** . Атрибут **SqlFunction** указывает, получает ли функция доступ к данным или вносит изменения в данные, является ли детерминированной и предусматривает ли выполнение операций с плавающей запятой.  
  
 Определяемые пользователем скалярные функции могут быть детерминированными или недетерминированными. Детерминированная функция всегда возвращает один и тот же результат при вызове с конкретным набором входных параметров. Недетерминированная функция может возвращать разные результаты при вызове с конкретным набором входных параметров.  
  
> [!NOTE]  
>  Не следует помечать функцию как детерминированную, если она не всегда выдает одинаковые выходные значения при передаче одинаковых входных значений и при одинаковом состоянии базы данных. Не следует определять функцию как детерминированную, если в действительности она таковой не является. Это может привести к искажению индексированных представлений и вычисляемых столбцов. Определить функцию как детерминированную можно, задав для свойства **IsDeterministic** значение true.  
  
### <a name="table-valued-parameters"></a>Параметры, возвращающие табличные значения  
 Возвращающие табличное значение параметры — это определяемые пользователем табличные типы, которые передаются в процедуру или функцию, предоставляя эффективный способ передачи на сервер нескольких строк данных. Возвращающие табличное значение параметры выполняют функции, аналогичные массивам параметров, но обладают большей гибкостью и лучше интегрируются с [!INCLUDE[tsql](../../includes/tsql-md.md)]. Они также обеспечивают возможность повышения производительности. Кроме того, возвращающие табличное значение параметры способствуют сокращению циклов приема-передачи данных с сервера и на сервер. Вместо того чтобы отправлять на сервер несколько запросов (как в случае списка скалярных параметров), данные можно отправить в виде возвращающего табличное значение параметра. Определяемый пользователем табличный тип нельзя передавать в виде возвращающего табличное значение параметра в управляемую хранимую процедуру или функцию, которая выполняется в процессе [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Кроме того, такие процедуры и функции не могут возвращать определяемые пользователем табличные типы. Дополнительные сведения о TVP см. в разделе [Использование возвращающих табличное значение параметров &#40;ядро СУБД&#41;](../../relational-databases/tables/use-table-valued-parameters-database-engine.md).  
  
## <a name="example-of-a-clr-scalar-valued-function"></a>Пример скалярной функции среды CLR  
 Ниже приводится простой пример скалярной функции, получающей доступ к данным и возвращающей целочисленное значение.  
  
```csharp  
using Microsoft.SqlServer.Server;  
using System.Data.SqlClient;  
  
public class T  
{  
    [SqlFunction(DataAccess = DataAccessKind.Read)]  
    public static int ReturnOrderCount()  
    {  
        using (SqlConnection conn   
            = new SqlConnection("context connection=true"))  
        {  
            conn.Open();  
            SqlCommand cmd = new SqlCommand(  
                "SELECT COUNT(*) AS 'Order Count' FROM SalesOrderHeader", conn);  
            return (int)cmd.ExecuteScalar();  
        }  
    }  
}  
```  
  
```vb  
Imports Microsoft.SqlServer.Server  
Imports System.Data.SqlClient  
  
Public Class T  
    <SqlFunction(DataAccess:=DataAccessKind.Read)> _  
    Public Shared Function ReturnOrderCount() As Integer  
        Using conn As New SqlConnection("context connection=true")  
            conn.Open()  
            Dim cmd As New SqlCommand("SELECT COUNT(*) AS 'Order Count' FROM SalesOrderHeader", conn)  
            Return CType(cmd.ExecuteScalar(), Integer)  
        End Using  
    End Function  
End Class  
```  
  
 В первой строке кода содержится ссылка на объект **Microsoft.SqlServer.Server** для доступа к атрибутам и на объект **System.Data.SqlClient** для доступа к пространству имен ADO.NET. (Это пространство имен содержит **SqlClient**, поставщик данных .NET Framework для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].)  
  
 Далее функция получает пользовательский атрибут **SqlFunction** , относящийся к пространству имен **Microsoft.SqlServer.Server** . Пользовательский атрибут указывает, используется ли определяемая пользователем функция (UDF) внутрипроцессным поставщиком для чтения данных с сервера. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не позволяет определяемым пользователем функциям обновлять, вставлять и удалять данные. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может оптимизировать выполнение определяемой пользователем функции, не использующей внутрипроцессный поставщик. На это указывает параметр **DataAccessKind** , имеющий значение **DataAccessKind.None**. На следующей строке целевой метод определяется как public static (или на языке Visual Basic .NET — shared).  
  
 Атрибут **SqlContext** , находящийся в пространстве имен **Microsoft.SqlServer.Server** , может получить доступ к объекту **SqlCommand** с уже созданным соединением с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Кроме того, становится доступным в рамках API **System.Transactions** контекст текущей транзакции, хотя в данном случае не используется.  
  
 Большая часть строк кода в тексте функции должна быть знакома для разработчика, имеющего опыт написания клиентских приложений с использованием типов из пространства имен **System.Data.SqlClient** .  
  
 [C#]  
  
```  
using(SqlConnection conn = new SqlConnection("context connection=true"))   
{  
   conn.Open();  
   SqlCommand cmd = new SqlCommand(  
        "SELECT COUNT(*) AS 'Order Count' FROM SalesOrderHeader", conn);  
   return (int) cmd.ExecuteScalar();  
}    
```  
  
 [Visual Basic]  
  
```  
Using conn As New SqlConnection("context connection=true")  
   conn.Open()  
   Dim cmd As New SqlCommand( _  
        "SELECT COUNT(*) AS 'Order Count' FROM SalesOrderHeader", conn)  
   Return CType(cmd.ExecuteScalar(), Integer)  
End Using  
```  
  
 Необходимый текст команды можно задать путем инициализации объекта **SqlCommand** . В предыдущем примере подсчитывалось число строк в таблице **SalesOrderHeader**. Далее вызывается метод **ExecuteScalar** объекта **cmd** . Он возвращает значение типа **int** на основе запроса. Наконец происходит возврат сведений о количестве заказов в вызывающий код.  
  
 После сохранения в файле с именем FirstUdf.cs этот код можно скомпилировать в сборку следующим образом:  
  
 [C#]  
  
```  
csc.exe /t:library /out:FirstUdf.dll FirstUdf.cs   
```  
  
 [Visual Basic]  
  
```  
vbc.exe /t:library /out:FirstUdf.dll FirstUdf.vb  
```  
  
> [!NOTE]  
>  `/t:library` указывает, что результатом компиляции должна быть библиотека, а не исполняемый объект. Исполняемые объекты нельзя регистрировать в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  Выполнение объектов базы данных, написанных на языке Visual C++ и скомпилированных с параметром **/clr:pure** , в СУБД [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. В частности, такими объектами базы данных являются скалярные функции.  
  
 Ниже приведены запрос [!INCLUDE[tsql](../../includes/tsql-md.md)] и образец вызова для регистрации сборки и определяемой пользователем функции.  
  
```  
CREATE ASSEMBLY FirstUdf FROM 'FirstUdf.dll';  
GO  
  
CREATE FUNCTION CountSalesOrderHeader() RETURNS INT   
AS EXTERNAL NAME FirstUdf.T.ReturnOrderCount;   
GO  
  
SELECT dbo.CountSalesOrderHeader();  
GO  
  
```  
  
 Обратите внимание, что имя функции в [!INCLUDE[tsql](../../includes/tsql-md.md)] не обязательно должно соответствовать имени общего статического целевого метода.  
  
## <a name="see-also"></a>См. также:  
 [Сопоставление данных параметров среды CLR](../../relational-databases/clr-integration-database-objects-types-net-framework/mapping-clr-parameter-data.md)   
 [Общие сведения о настраиваемых атрибутах интеграции со средой CLR](https://msdn.microsoft.com/library/ecf5c097-0972-48e2-a9c0-b695b7dd2820)   
 [Определяемые пользователем функции](../../relational-databases/user-defined-functions/user-defined-functions.md)   
 [Доступ к данным из объектов среды CLR для работы с базами данных](../../relational-databases/clr-integration/data-access/data-access-from-clr-database-objects.md)  
  
  
