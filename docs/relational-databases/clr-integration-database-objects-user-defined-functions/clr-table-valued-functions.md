---
title: Возвращающие табличные значения функции CLR | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: clr
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
dev_langs:
- TSQL
- VB
- CSharp
helpviewer_keywords:
- Transact-SQL table-valued functions
- table-valued functions [CLR integration]
- TVFs [CLR integration]
ms.assetid: 9a6133ea-36e9-45bf-b572-1c0df3d6c194
caps.latest.revision: 88
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 7b84682f6b2c22ab58f8ba0b591cdfe3c3eda2e0
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="clr-table-valued-functions"></a>Функции среды CLR с табличным значением
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Функция с табличным значением представляет собой определяемую пользователем функцию, которая возвращает таблицу.  
  
 Начиная с [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] расширяет возможности возвращающих табличное значение функций, позволяя определить функцию с табличным значением на любом управляемом языке. Данные возвращаются из функции, возвращающие табличные значения, через **IEnumerable** или **IEnumerator** объекта.  
  
> [!NOTE]  
>  Для функций, возвращающих табличные значения, не может включать столбцы возвращаемого табличного типа, столбцы отметок времени и столбцы строкового типа данных не в Юникоде (такие как **char**, **varchar**, и **текста**). Ограничение NOT NULL не поддерживается.  
  
 Дополнительные сведения о функции CLR табличные извлечь MSSQLTips [введение в SQL Server со средой CLR таблицы функции с табличным значением.](https://www.mssqltips.com/sqlservertip/2582/introduction-to-sql-server-clr-table-valued-functions/)  
  
## <a name="differences-between-transact-sql-and-clr-table-valued-functions"></a>Различия между функциями Transact-SQL и среды CLR с табличным значением  
 Возвращающие табличное значение функции [!INCLUDE[tsql](../../includes/tsql-md.md)] материализуют результаты вызова в промежуточной таблице. По этой причине они поддерживают в результатах ограничения и уникальные индексы. Это исключительно полезно при возвращении результатов большого объема.  
  
 Функции CLR с табличным значением, напротив, представляют альтернативу в виде потока. Материализация всего результирующего набора в одной таблице не требуется. **IEnumerable** объект, возвращаемый управляемой функции вызывается непосредственно в плане выполнения запроса, который вызывает функции, возвращающие табличные значения, и будут использованы результаты, следите за тем. Такая потоковая модель обеспечивает немедленную обработку результатов сразу после получения первой строки, вместо того чтобы ожидать заполнения всей таблицы. Она также полезна, если возвращается очень большое число строк, поскольку таблица не материализуется в памяти как единое целое. Например, функция с табличным значением может использоваться для синтаксического анализа текстового файла и возвращения каждой строки текста в виде строки таблицы.  
  
## <a name="implementing-table-valued-functions"></a>Реализация функций с табличным значением  
 Функции с табличным значением реализуются в виде методов класса в сборке [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework. Необходимо реализовать в коде функция с табличным **IEnumerable** интерфейса. **IEnumerable** интерфейс определен в .NET Framework. Типы, представляющие массивы и коллекции в .NET Framework уже реализуйте **IEnumerable** интерфейса. Это облегчает написание функций с табличным значением, преобразующих коллекцию или массив в результирующий набор.  
  
## <a name="table-valued-parameters"></a>Параметры, возвращающие табличные значения  
 Возвращающие табличное значение параметры — это определяемые пользователем табличные типы, которые передаются в процедуру или функцию, предоставляя эффективный способ передачи на сервер нескольких строк данных. Возвращающие табличное значение параметры выполняют функции, аналогичные массивам параметров, но обладают большей гибкостью и лучше интегрируются с [!INCLUDE[tsql](../../includes/tsql-md.md)]. Они также обеспечивают возможность повышения производительности. Кроме того, возвращающие табличное значение параметры способствуют сокращению циклов приема-передачи данных с сервера и на сервер. Вместо того чтобы отправлять на сервер несколько запросов (как в случае списка скалярных параметров), данные можно отправить в виде возвращающего табличное значение параметра. Определяемый пользователем табличный тип нельзя передавать в виде возвращающего табличное значение параметра в управляемую хранимую процедуру или функцию, которая выполняется в процессе [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Кроме того, такие процедуры и функции не могут возвращать определяемые пользователем табличные типы. Дополнительные сведения о возвращающих табличные значения параметров см. в разделе [использование возвращающих табличные значения параметры & #40; компонент Database Engine & #41;](../../relational-databases/tables/use-table-valued-parameters-database-engine.md).  
  
## <a name="output-parameters-and-table-valued-functions"></a>Выходные параметры и функции с табличным значением  
 Возврат данных из функции с табличным значением может производиться через выходные параметры. Соответствующий аргумент в коде реализации функции с табличным значением должен передаваться по ссылке. Следует отметить, что язык Visual Basic не поддерживает выходные параметры так, как они поддерживаются в языке Visual C#. Необходимо задать параметр по ссылке и применить \<Out() > атрибут для представления выходного параметра, как описано ниже:  
  
```vb  
Imports System.Runtime.InteropServices  
…  
Public Shared Sub FillRow ( <Out()> ByRef value As SqlInt32)  
```  
  
### <a name="defining-a-table-valued-function-in-transact-sql"></a>Определение функции с табличным значением на языке Transact-SQL  
 Синтаксис для определения табличной функции CLR аналогичен [!INCLUDE[tsql](../../includes/tsql-md.md)] функции, возвращающие табличные значения, с добавлением **ВНЕШНЕЕ имя** предложения. Например:  
  
```  
CREATE FUNCTION GetEmpFirstLastNames()  
RETURNS TABLE (FirstName NVARCHAR(4000), LastName NVARCHAR(4000))  
EXTERNAL NAME MyDotNETAssembly.[MyNamespace.MyClassname]. GetEmpFirstLastNames;  
```  
  
 Функции с табличным значением используются для представления данных в реляционном формате для дальнейшей обработки в запросах, например:  
  
```  
select * from function();  
select * from tbl join function() f on tbl.col = f.col;  
select * from table t cross apply function(t.column);  
```  
  
 Функции с табличным значением могут вернуть таблицу в следующих случаях.  
  
-   Если они созданы из скалярных входных аргументов. Например, функция с табличным значением, принимающая строку чисел, разделенных запятыми, и преобразующая ее в таблицу.  
  
-   Если они созданы из внешних данных. Например, функция с табличным значением, считывающая журнал событий и представляющая его в виде таблицы.  
  
 **Примечание** табличную функцию можно выполнить только доступ к данным в [!INCLUDE[tsql](../../includes/tsql-md.md)] запроса в **InitMethod** метода, а не в **FillRow** метод. **InitMethod** должны быть отмечены **SqlFunction.DataAccess.Read** свойству атрибута, если [!INCLUDE[tsql](../../includes/tsql-md.md)] выполняется запрос.  
  
## <a name="a-sample-table-valued-function"></a>Образец функции с табличным значением  
 Следующая функция с табличным значением возвращает сведения из журнала системных событий. Функция принимает один строковый аргумент, содержащий имя журнала событий.  
  
###### <a name="sample-code"></a>Образец кода  
  
```csharp  
using System;  
using System.Data.Sql;  
using Microsoft.SqlServer.Server;  
using System.Collections;  
using System.Data.SqlTypes;  
using System.Diagnostics;  
  
public class TabularEventLog  
{  
    [SqlFunction(FillRowMethodName = "FillRow")]  
    public static IEnumerable InitMethod(String logname)  
    {  
        return new EventLog(logname).Entries;    }  
  
    public static void FillRow(Object obj, out SqlDateTime timeWritten, out SqlChars message, out SqlChars category, out long instanceId)  
    {  
        EventLogEntry eventLogEntry = (EventLogEntry)obj;  
        timeWritten = new SqlDateTime(eventLogEntry.TimeWritten);  
        message = new SqlChars(eventLogEntry.Message);  
        category = new SqlChars(eventLogEntry.Category);  
        instanceId = eventLogEntry.InstanceId;  
    }  
}  
```  
  
```vb  
Imports System  
Imports System.Data.Sql  
Imports Microsoft.SqlServer.Server  
Imports System.Collections  
Imports System.Data.SqlTypes  
Imports System.Diagnostics  
Imports System.Runtime.InteropServices  
  
Public Class TabularEventLog  
    <SqlFunction(FillRowMethodName:="FillRow")> _  
    Public Shared Function InitMethod(ByVal logname As String) As IEnumerable  
        Return New EventLog(logname).Entries  
    End Function  
  
    Public Shared Sub FillRow(ByVal obj As Object, <Out()> ByRef timeWritten As SqlDateTime, <Out()> ByRef message As SqlChars, <Out()> ByRef category As SqlChars, <Out()> ByRef instanceId As Long)  
        Dim eventLogEnTry As EventLogEntry = CType(obj, EventLogEntry)  
        timeWritten = New SqlDateTime(eventLogEnTry.TimeWritten)  
        message = New SqlChars(eventLogEnTry.Message)  
        category = New SqlChars(eventLogEnTry.Category)  
        instanceId = eventLogEnTry.InstanceId  
    End Sub  
End Class  
```  
  
###### <a name="declaring-and-using-the-sample-table-valued-function"></a>Объявление и использование образца функции с табличным значением  
 После компиляции образца возвращающей табличное значение функции его можно объявить в [!INCLUDE[tsql](../../includes/tsql-md.md)] следующим образом.  
  
```  
use master;  
-- Replace SQL_Server_logon with your SQL Server user credentials.  
GRANT EXTERNAL ACCESS ASSEMBLY TO [SQL_Server_logon];   
-- Modify the following line to specify a different database.  
ALTER DATABASE master SET TRUSTWORTHY ON;  
  
-- Modify the next line to use the appropriate database.  
CREATE ASSEMBLY tvfEventLog   
FROM 'D:\assemblies\tvfEventLog\tvfeventlog.dll'   
WITH PERMISSION_SET = EXTERNAL_ACCESS;  
GO  
CREATE FUNCTION ReadEventLog(@logname nvarchar(100))  
RETURNS TABLE   
(logTime datetime,Message nvarchar(4000),Category nvarchar(4000),InstanceId bigint)  
AS   
EXTERNAL NAME tvfEventLog.TabularEventLog.InitMethod;  
GO  
```  
  
 Выполнение объектов базы данных, написанных на языке Visual C++ и скомпилированных с параметром /clr:pure, не поддерживается в [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]. Например, в число таких объектов базы данных входят функции с табличным значением.  
  
 Чтобы проверить образец, выполните следующий код [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
```  
-- Select the top 100 events,  
SELECT TOP 100 *  
FROM dbo.ReadEventLog(N'Security') as T;  
go  
  
-- Select the last 10 login events.  
SELECT TOP 10 T.logTime, T.Message, T.InstanceId   
FROM dbo.ReadEventLog(N'Security') as T  
WHERE T.Category = N'Logon/Logoff';  
go  
```  
  
## <a name="sample-returning-the-results-of-a-sql-server-query"></a>Образец. Возвращение результатов запроса SQL Server  
 В следующем образце показана возвращающая табличное значение функция, которая запрашивает базу данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. В этом образце используется база данных AdventureWorks Light из [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]. В разделе [ http://www.codeplex.com/sqlserversamples ](http://go.microsoft.com/fwlink/?LinkId=87843) Дополнительные сведения о загрузке AdventureWorks.  
  
 Задайте для файла исходного кода имя FindInvalidEmails.cs или FindInvalidEmails.vb.  
  
```csharp  
using System;  
using System.Collections;  
using System.Data;  
using System.Data.SqlClient;  
using System.Data.SqlTypes;  
  
using Microsoft.SqlServer.Server;  
  
public partial class UserDefinedFunctions {  
   private class EmailResult {  
      public SqlInt32 CustomerId;  
      public SqlString EmailAdress;  
  
      public EmailResult(SqlInt32 customerId, SqlString emailAdress) {  
         CustomerId = customerId;  
         EmailAdress = emailAdress;  
      }  
   }  
  
   public static bool ValidateEmail(SqlString emailAddress) {  
      if (emailAddress.IsNull)  
         return false;  
  
      if (!emailAddress.Value.EndsWith("@adventure-works.com"))  
         return false;  
  
      // Validate the address. Put any more rules here.  
      return true;  
   }  
  
   [SqlFunction(  
       DataAccess = DataAccessKind.Read,  
       FillRowMethodName = "FindInvalidEmails_FillRow",  
       TableDefinition="CustomerId int, EmailAddress nvarchar(4000)")]  
   public static IEnumerable FindInvalidEmails(SqlDateTime modifiedSince) {  
      ArrayList resultCollection = new ArrayList();  
  
      using (SqlConnection connection = new SqlConnection("context connection=true")) {  
         connection.Open();  
  
         using (SqlCommand selectEmails = new SqlCommand(  
             "SELECT " +  
             "[CustomerID], [EmailAddress] " +  
             "FROM [AdventureWorksLT2008].[SalesLT].[Customer] " +  
             "WHERE [ModifiedDate] >= @modifiedSince",  
             connection)) {  
            SqlParameter modifiedSinceParam = selectEmails.Parameters.Add(  
                "@modifiedSince",  
                SqlDbType.DateTime);  
            modifiedSinceParam.Value = modifiedSince;  
  
            using (SqlDataReader emailsReader = selectEmails.ExecuteReader()) {  
               while (emailsReader.Read()) {  
                  SqlString emailAddress = emailsReader.GetSqlString(1);  
                  if (ValidateEmail(emailAddress)) {  
                     resultCollection.Add(new EmailResult(  
                         emailsReader.GetSqlInt32(0),  
                         emailAddress));  
                  }  
               }  
            }  
         }  
      }  
  
      return resultCollection;  
   }  
  
   public static void FindInvalidEmails_FillRow(  
       object emailResultObj,  
       out SqlInt32 customerId,  
       out SqlString emailAdress) {  
      EmailResult emailResult = (EmailResult)emailResultObj;  
  
      customerId = emailResult.CustomerId;  
      emailAdress = emailResult.EmailAdress;  
   }  
};  
```  
  
```vb  
Imports System.Collections  
Imports System.Data  
Imports System.Data.SqlClient  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
  
Public Partial Class UserDefinedFunctions  
   Private Class EmailResult  
      Public CustomerId As SqlInt32  
      Public EmailAdress As SqlString  
  
      Public Sub New(customerId__1 As SqlInt32, emailAdress__2 As SqlString)  
         CustomerId = customerId__1  
         EmailAdress = emailAdress__2  
      End Sub  
   End Class  
  
   Public Shared Function ValidateEmail(emailAddress As SqlString) As Boolean  
      If emailAddress.IsNull Then  
         Return False  
      End If  
  
      If Not emailAddress.Value.EndsWith("@adventure-works.com") Then  
         Return False  
      End If  
  
      ' Validate the address. Put any more rules here.  
      Return True  
   End Function  
  
   <SqlFunction(DataAccess := DataAccessKind.Read, FillRowMethodName := "FindInvalidEmails_FillRow", TableDefinition := "CustomerId int, EmailAddress nvarchar(4000)")> _  
   Public Shared Function FindInvalidEmails(modifiedSince As SqlDateTime) As IEnumerable  
      Dim resultCollection As New ArrayList()  
  
      Using connection As New SqlConnection("context connection=true")  
         connection.Open()  
  
         Using selectEmails As New SqlCommand("SELECT " & "[CustomerID], [EmailAddress] " & "FROM [AdventureWorksLT2008].[SalesLT].[Customer] " & "WHERE [ModifiedDate] >= @modifiedSince", connection)  
            Dim modifiedSinceParam As SqlParameter = selectEmails.Parameters.Add("@modifiedSince", SqlDbType.DateTime)  
            modifiedSinceParam.Value = modifiedSince  
  
            Using emailsReader As SqlDataReader = selectEmails.ExecuteReader()  
               While emailsReader.Read()  
                  Dim emailAddress As SqlString = emailsReader.GetSqlString(1)  
                  If ValidateEmail(emailAddress) Then  
                     resultCollection.Add(New EmailResult(emailsReader.GetSqlInt32(0), emailAddress))  
                  End If  
               End While  
            End Using  
         End Using  
      End Using  
  
      Return resultCollection  
   End Function  
  
   Public Shared Sub FindInvalidEmails_FillRow(emailResultObj As Object, ByRef customerId As SqlInt32, ByRef emailAdress As SqlString)  
      Dim emailResult As EmailResult = DirectCast(emailResultObj, EmailResult)  
  
      customerId = emailResult.CustomerId  
      emailAdress = emailResult.EmailAdress  
   End Sub  
End ClassImports System.Collections  
Imports System.Data  
Imports System.Data.SqlClient  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
  
Public Partial Class UserDefinedFunctions  
   Private Class EmailResult  
      Public CustomerId As SqlInt32  
      Public EmailAdress As SqlString  
  
      Public Sub New(customerId__1 As SqlInt32, emailAdress__2 As SqlString)  
         CustomerId = customerId__1  
         EmailAdress = emailAdress__2  
      End Sub  
   End Class  
  
   Public Shared Function ValidateEmail(emailAddress As SqlString) As Boolean  
      If emailAddress.IsNull Then  
         Return False  
      End If  
  
      If Not emailAddress.Value.EndsWith("@adventure-works.com") Then  
         Return False  
      End If  
  
      ' Validate the address. Put any more rules here.  
      Return True  
   End Function  
  
   <SqlFunction(DataAccess := DataAccessKind.Read, FillRowMethodName := "FindInvalidEmails_FillRow", TableDefinition := "CustomerId int, EmailAddress nvarchar(4000)")> _  
   Public Shared Function FindInvalidEmails(modifiedSince As SqlDateTime) As IEnumerable  
      Dim resultCollection As New ArrayList()  
  
      Using connection As New SqlConnection("context connection=true")  
         connection.Open()  
  
         Using selectEmails As New SqlCommand("SELECT " & "[CustomerID], [EmailAddress] " & "FROM [AdventureWorksLT2008].[SalesLT].[Customer] " & "WHERE [ModifiedDate] >= @modifiedSince", connection)  
            Dim modifiedSinceParam As SqlParameter = selectEmails.Parameters.Add("@modifiedSince", SqlDbType.DateTime)  
            modifiedSinceParam.Value = modifiedSince  
  
            Using emailsReader As SqlDataReader = selectEmails.ExecuteReader()  
               While emailsReader.Read()  
                  Dim emailAddress As SqlString = emailsReader.GetSqlString(1)  
                  If ValidateEmail(emailAddress) Then  
                     resultCollection.Add(New EmailResult(emailsReader.GetSqlInt32(0), emailAddress))  
                  End If  
               End While  
            End Using  
         End Using  
      End Using  
  
      Return resultCollection  
   End Function  
  
   Public Shared Sub FindInvalidEmails_FillRow(emailResultObj As Object, customerId As SqlInt32, emailAdress As SqlString)  
      Dim emailResult As EmailResult = DirectCast(emailResultObj, EmailResult)  
  
      customerId = emailResult.CustomerId  
      emailAdress = emailResult.EmailAdress  
   End Sub  
End Class  
```  
  
 Скомпилируйте исходный код в библиотеку DLL и скопируйте ее в корневой каталог диска C.  Затем выполните следующий запрос [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
```  
use AdventureWorksLT2008;  
go  
  
IF EXISTS (SELECT name FROM sysobjects WHERE name = 'FindInvalidEmails')  
   DROP FUNCTION FindInvalidEmails;  
go  
  
IF EXISTS (SELECT name FROM sys.assemblies WHERE name = 'MyClrCode')  
   DROP ASSEMBLY MyClrCode;  
go  
  
CREATE ASSEMBLY MyClrCode FROM 'C:\FindInvalidEmails.dll'  
WITH PERMISSION_SET = SAFE -- EXTERNAL_ACCESS;  
GO  
  
CREATE FUNCTION FindInvalidEmails(@ModifiedSince datetime)   
RETURNS TABLE (  
   CustomerId int,  
   EmailAddress nvarchar(4000)  
)  
AS EXTERNAL NAME MyClrCode.UserDefinedFunctions.[FindInvalidEmails];  
go  
  
SELECT * FROM FindInvalidEmails('2000-01-01');  
go  
```  
  
  
