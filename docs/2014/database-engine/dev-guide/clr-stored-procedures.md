---
title: Хранимые процедуры CLR | Документация Майкрософт
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
dev_langs:
- TSQL
- VB
- CSharp
helpviewer_keywords:
- database objects [CLR integration], stored procedures
- stored procedures [CLR integration]
- common language runtime [SQL Server], stored procedures
- building database objects [CLR integration], stored procedures
- output parameters [CLR integration]
- tabular results
ms.assetid: bbdd51b2-a9b4-4916-ba6f-7957ac6c3f33
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 9f509b2a2544c67c9113bc700b7d98bfd4a24024
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62753825"
---
# <a name="clr-stored-procedures"></a>Хранимые процедуры CLR
  Хранимыми процедурами являются процедуры, которые нельзя использовать в скалярных выражениях. В отличие от скалярных функций, они могут возвращать клиенту табличные результаты и сообщения, вызывать инструкции языка описания данных DDL и языка обработки данных DML, а также возвращать выходные параметры. Дополнительные сведения о преимуществах интеграции со средой CLR и выборе между управляемым кодом и [!INCLUDE[tsql](../../includes/tsql-md.md)], см. в разделе [Общие сведения об интеграции со средой CLR](../../relational-databases/clr-integration/clr-integration-overview.md).  
  
## <a name="requirements-for-clr-stored-procedures"></a>Требования для хранимых процедур CLR  
 В CLR (CLR), хранимые процедуры реализуются как общие статические методы класса в [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] сборки. Статический метод может быть объявлен как void или может возвратить целое значение. Если он возвращает целое значение, возвращенное целое число рассматривается как код возврата из процедуры. Пример:  
  
 `EXECUTE @return_status = procedure_name`  
  
 @return_status Переменная будет содержать значение, возвращаемое этим методом. Если метод объявляется как void, код возврата равен 0.  
  
 Если метод принимает параметры, число параметров в реализации [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] должно быть равно числу параметров, используемых в декларации [!INCLUDE[tsql](../../includes/tsql-md.md)] хранимой процедуры.  
  
 Параметры, передаваемые в хранимую процедуру CLR, могут быть любого собственного типа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], имеющего эквивалент в управляемом коде. Для синтаксиса [!INCLUDE[tsql](../../includes/tsql-md.md)], используемого при создании процедуры, такие типы должны задаваться при помощи наиболее подходящего эквивалента собственного типа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения о преобразованиях типов см. в разделе [сопоставление данных параметров CLR](../../relational-databases/clr-integration-database-objects-types-net-framework/mapping-clr-parameter-data.md).  
  
### <a name="table-valued-parameters"></a>Параметры, возвращающие табличные значения  
 Возвращающие табличное значение параметры — это определяемые пользователем табличные типы, которые передаются в процедуру или функцию, предоставляя эффективный способ передачи на сервер нескольких строк данных. Возвращающие табличное значение параметры выполняют функции, аналогичные массивам параметров, но обладают большей гибкостью и лучше интегрируются с [!INCLUDE[tsql](../../includes/tsql-md.md)]. Они также обеспечивают возможность повышения производительности. Кроме того, возвращающие табличное значение параметры способствуют сокращению циклов приема-передачи данных с сервера и на сервер. Вместо того чтобы отправлять на сервер несколько запросов (как в случае списка скалярных параметров), данные можно отправить в виде возвращающего табличное значение параметра. Определяемый пользователем табличный тип нельзя передавать в виде возвращающего табличное значение параметра в управляемую хранимую процедуру или функцию, которая выполняется в процессе [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Кроме того, такие процедуры и функции не могут возвращать определяемые пользователем табличные типы. Дополнительные сведения о возвращающие табличное значение параметры, см. в разделе [параметров, возвращающих &#40;СУБД&#41;](../../relational-databases/tables/use-table-valued-parameters-database-engine.md).  
  
## <a name="returning-results-from-clr-stored-procedures"></a>Возврат результатов хранимых процедур CLR  
 Возврат данных из хранимых процедур [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] может осуществляться несколькими способами. Это относится к выходным параметрам, табличным результатам и сообщениям.  
  
### <a name="output-parameters-and-clr-stored-procedures"></a>Параметры OUTPUT и хранимые процедуры CLR  
 Так же как и для хранимых процедур [!INCLUDE[tsql](../../includes/tsql-md.md)], данные могут возвращаться из хранимых процедур [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] при помощи параметров, описанных с ключевым словом OUTPUT. Синтаксис [!INCLUDE[tsql](../../includes/tsql-md.md)] DML, используемый для создания хранимых процедур [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], тот же, что и синтаксис, используемый для создания хранимых процедур, написанных на [!INCLUDE[tsql](../../includes/tsql-md.md)]. Соответствующий параметр в коде реализации в классе [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] должен использовать в качестве аргумента параметр, передаваемый по ссылке. Следует отметить, что язык Visual Basic не поддерживает выходные параметры так, как они поддерживаются в языке Visual C#. Необходимо указать параметр по ссылке и применить \<Out() > атрибут для представления ВЫХОДНОГО параметра, как описано ниже:  
  
```  
Imports System.Runtime.InteropServices  
...  
Public Shared Sub PriceSum ( <Out()> ByRef value As SqlInt32)  
```  
  
 Следующий пример представляет хранимую процедуру с входным и выходным параметрами:  
  
 C#  
  
```  
using System;  
using System.Data.SqlTypes;  
using System.Data.SqlClient;  
using Microsoft.SqlServer.Server;   
  
public class StoredProcedures   
{  
   [Microsoft.SqlServer.Server.SqlProcedure]  
   public static void PriceSum(out SqlInt32 value)  
   {  
      using(SqlConnection connection = new SqlConnection("context connection=true"))   
      {  
         value = 0;  
         connection.Open();  
         SqlCommand command = new SqlCommand("SELECT Price FROM Products", connection);  
         SqlDataReader reader = command.ExecuteReader();  
  
         using (reader)  
         {  
            while( reader.Read() )  
            {  
               value += reader.GetSqlInt32(0);  
            }  
         }           
      }  
   }  
}  
```  
  
 Visual Basic  
  
```  
Imports System  
Imports System.Data  
Imports System.Data.Sql  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
Imports System.Data.SqlClient  
Imports System.Runtime.InteropServices  
  
'The Partial modifier is only required on one class definition per project.  
Partial Public Class StoredProcedures   
    ''' <summary>  
    ''' Executes a query and iterates over the results to perform a summation.  
    ''' </summary>  
    <Microsoft.SqlServer.Server.SqlProcedure> _  
    Public Shared Sub PriceSum( <Out()> ByRef value As SqlInt32)  
  
        Using connection As New SqlConnection("context connection=true")  
           value = 0  
           Connection.Open()  
           Dim command As New SqlCommand("SELECT Price FROM Products", connection)  
           Dim reader As SqlDataReader  
           reader = command.ExecuteReader()  
  
           Using reader  
              While reader.Read()  
                 value += reader.GetSqlInt32(0)  
              End While  
           End Using  
        End Using          
    End Sub  
End Class  
```  
  
 После сохранения сборки, содержащей выше CLR процедуры построена и создана на сервере, следующие [!INCLUDE[tsql](../../includes/tsql-md.md)] используется для создания процедуры в базе данных и задает *sum* как ВЫХОДНОЙ параметр.  
  
```  
CREATE PROCEDURE PriceSum (@sum int OUTPUT)  
AS EXTERNAL NAME TestStoredProc.StoredProcedures.PriceSum  
-- if StoredProcedures class was inside a namespace, called MyNS,  
-- you would use:  
-- AS EXTERNAL NAME TestStoredProc.[MyNS.StoredProcedures].PriceSum  
```  
  
 Обратите внимание, что *sum* объявляется как `int` тип данных SQL Server и что *значение* указания параметра, определенного в хранимой процедуре CLR `SqlInt32` тип данных CLR. Если вызывающая программа выполняет хранимую процедуру CLR, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] автоматически преобразует `SqlInt32` тип данных CLR `int` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] тип данных.  Дополнительные сведения о какой среде CLR типы данных, можно и нельзя преобразовать, см. в разделе [сопоставление данных параметров CLR](../../relational-databases/clr-integration-database-objects-types-net-framework/mapping-clr-parameter-data.md).  
  
### <a name="returning-tabular-results-and-messages"></a>Возврат табличных результатов и сообщений  
 Возврат клиенту табличных результатов и сообщений выполняется через объект `SqlPipe`, получаемый при использовании свойства `Pipe` класса `SqlContext`. Объект `SqlPipe` имеет метод `Send`. Вызвав метод `Send`, можно передать данные по каналу вызывающему приложению.  
  
 Далее приводятся несколько перегрузок метода `SqlPipe.Send`, включая перегрузку, которая посылает объект `SqlDataReader`, а также другую перегрузку, которая просто посылает текстовую строку.  
  
###### <a name="returning-messages"></a>Возврат сообщений  
 Метод `SqlPipe.Send(string)` используется для передачи сообщений в клиентское приложение. Текст сообщения ограничен 8000 символов. Если размер сообщения превышает 8000 символов, сообщение усекается.  
  
###### <a name="returning-tabular-results"></a>Возврат табличных результатов  
 Чтобы послать результаты запроса непосредственно клиенту, используется один из перегруженных методов `Execute` на объекте `SqlPipe`. Это наиболее эффективный способ возврата результатов клиенту, поскольку данные передаются в сетевые буферы без копирования в управляемую память. Пример:  
  
 [C#]  
  
```  
using System;  
using System.Data;  
using System.Data.SqlTypes;  
using System.Data.SqlClient;  
using Microsoft.SqlServer.Server;   
  
public class StoredProcedures   
{  
   /// <summary>  
   /// Execute a command and send the results to the client directly.  
   /// </summary>  
   [Microsoft.SqlServer.Server.SqlProcedure]  
   public static void ExecuteToClient()  
   {  
   using(SqlConnection connection = new SqlConnection("context connection=true"))   
   {  
      connection.Open();  
      SqlCommand command = new SqlCommand("select @@version", connection);  
      SqlContext.Pipe.ExecuteAndSend(command);  
      }  
   }  
}  
```  
  
 [Visual Basic]  
  
```  
Imports System  
Imports System.Data  
Imports System.Data.Sql  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
Imports System.Data.SqlClient  
  
'The Partial modifier is only required on one class definition per project.  
Partial Public Class StoredProcedures   
    ''' <summary>  
    ''' Execute a command and send the results to the client directly.  
    ''' </summary>  
    <Microsoft.SqlServer.Server.SqlProcedure> _  
    Public Shared Sub ExecuteToClient()  
        Using connection As New SqlConnection("context connection=true")  
            connection.Open()  
            Dim command As New SqlCommand("SELECT @@VERSION", connection)  
            SqlContext.Pipe.ExecuteAndSend(command)  
        End Using  
    End Sub  
End Class  
```  
  
 Чтобы послать результаты ранее выполненного запроса через внутрипроцессного поставщика или чтобы предварительно обработать данные с использованием пользовательской реализации `SqlDataReader`, используется перегрузка метода `Send`, которая принимает `SqlDataReader`. Этот метод немного медленнее, чем описанный выше непосредственный метод, но он обеспечивает большую гибкость при обработке данных перед их отправкой клиенту.  
  
```csharp  
using System;  
using System.Data;  
using System.Data.SqlTypes;  
using System.Data.SqlClient;  
using Microsoft.SqlServer.Server;   
  
public class StoredProcedures   
{  
   /// <summary>  
   /// Execute a command and send the resulting reader to the client  
   /// </summary>  
   [Microsoft.SqlServer.Server.SqlProcedure]  
   public static void SendReaderToClient()  
   {  
      using(SqlConnection connection = new SqlConnection("context connection=true"))   
      {  
         connection.Open();  
         SqlCommand command = new SqlCommand("select @@version", connection);  
         SqlDataReader r = command.ExecuteReader();  
         SqlContext.Pipe.Send(r);  
      }  
   }  
}  
```  
  
 [Visual Basic]  
  
```  
Imports System  
Imports System.Data  
Imports System.Data.Sql  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
Imports System.Data.SqlClient  
  
'The Partial modifier is only required on one class definition per project.  
Partial Public Class StoredProcedures   
    ''' <summary>  
    ''' Execute a command and send the results to the client directly.  
    ''' </summary>  
    <Microsoft.SqlServer.Server.SqlProcedure> _  
    Public Shared Sub SendReaderToClient()  
        Using connection As New SqlConnection("context connection=true")  
            connection.Open()  
            Dim command As New SqlCommand("SELECT @@VERSION", connection)  
            Dim reader As SqlDataReader  
            reader = command.ExecuteReader()  
            SqlContext.Pipe.Send(reader)  
        End Using  
    End Sub  
End Class  
```  
  
 Чтобы создать динамический результирующий набор, заполнить его и послать клиенту, можно создать записи на текущем соединении и послать их при помощи `SqlPipe.Send`.  
  
```csharp  
using System.Data;  
using System.Data.SqlClient;  
using Microsoft.SqlServer.Server;   
using System.Data.SqlTypes;  
  
public class StoredProcedures   
{  
   /// <summary>  
   /// Create a result set on the fly and send it to the client.  
   /// </summary>  
   [Microsoft.SqlServer.Server.SqlProcedure]  
   public static void SendTransientResultSet()  
   {  
      // Create a record object that represents an individual row, including it's metadata.  
      SqlDataRecord record = new SqlDataRecord(new SqlMetaData("stringcol", SqlDbType.NVarChar, 128));  
  
      // Populate the record.  
      record.SetSqlString(0, "Hello World!");  
  
      // Send the record to the client.  
      SqlContext.Pipe.Send(record);  
   }  
}  
```  
  
 [Visual Basic]  
  
```  
Imports System  
Imports System.Data  
Imports System.Data.Sql  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
Imports System.Data.SqlClient  
  
'The Partial modifier is only required on one class definition per project.  
Partial Public Class StoredProcedures   
    ''' <summary>  
    ''' Create a result set on the fly and send it to the client.  
    ''' </summary>  
    <Microsoft.SqlServer.Server.SqlProcedure> _  
    Public Shared Sub SendTransientResultSet()  
        ' Create a record object that represents an individual row, including it's metadata.  
        Dim record As New SqlDataRecord(New SqlMetaData("stringcol", SqlDbType.NVarChar, 128) )  
  
        ' Populate the record.  
        record.SetSqlString(0, "Hello World!")  
  
        ' Send the record to the client.  
        SqlContext.Pipe.Send(record)          
    End Sub  
End Class   
```  
  
 Здесь представлен пример отправки табличных результатов и сообщения через `SqlPipe`.  
  
```csharp  
using System.Data.SqlClient;  
using Microsoft.SqlServer.Server;   
  
public class StoredProcedures   
{  
   [Microsoft.SqlServer.Server.SqlProcedure]  
   public static void HelloWorld()  
   {  
      SqlContext.Pipe.Send("Hello world! It's now " + System.DateTime.Now.ToString()+"\n");  
      using(SqlConnection connection = new SqlConnection("context connection=true"))   
      {  
         connection.Open();  
         SqlCommand command = new SqlCommand("SELECT ProductNumber FROM ProductMaster", connection);  
         SqlDataReader reader = command.ExecuteReader();  
         SqlContext.Pipe.Send(reader);  
      }  
   }  
}  
```  
  
 [Visual Basic]  
  
```  
Imports System  
Imports System.Data  
Imports System.Data.Sql  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
Imports System.Data.SqlClient  
  
'The Partial modifier is only required on one class definition per project.  
Partial Public Class StoredProcedures   
    ''' <summary>  
    ''' Execute a command and send the results to the client directly.  
    ''' </summary>  
    <Microsoft.SqlServer.Server.SqlProcedure> _  
    Public Shared Sub HelloWorld()  
        SqlContext.Pipe.Send("Hello world! It's now " & System.DateTime.Now.ToString() & "\n")  
        Using connection As New SqlConnection("context connection=true")  
            connection.Open()  
            Dim command As New SqlCommand("SELECT ProductNumber FROM ProductMaster", connection)  
            Dim reader As SqlDataReader  
            reader = command.ExecuteReader()  
            SqlContext.Pipe.Send(reader)  
        End Using  
    End Sub  
End Class   
```  
  
 Первый метод `Send` отправляет клиенту сообщение, а второй — табличные результаты с помощью объекта `SqlDataReader`.  
  
 Следует отметить, что эти примеры служат только для иллюстрации. Для приложений, ориентированных в основном на большой объем вычислений, больше подходят функции CLR, чем простые инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)]. Эта хранимая процедура [!INCLUDE[tsql](../../includes/tsql-md.md)] почти эквивалентна процедуре из предыдущего примера:  
  
```  
CREATE PROCEDURE HelloWorld() AS  
BEGIN  
PRINT('Hello world!')  
SELECT ProductNumber FROM ProductMaster  
END;  
```  
  
> [!NOTE]  
>  Сообщения и результирующие наборы в клиентском приложении получаются по-разному. К примеру [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] результирующих наборов отображаются в **результатов** представления, а сообщения **сообщений** области.  
  
 Если сохранить приведенный выше код на языке Visual C# в файле с именем MyFirstUdp.cs и скомпилировать его следующей командой:  
  
```  
csc /t:library /out:MyFirstUdp.dll MyFirstUdp.cs   
```  
  
 Или если сохранить приведенный выше код на языке Visual Basic в файле с именем MyFirstUdp.vb и скомпилировать его следующей командой:  
  
```  
vbc /t:library /out:MyFirstUdp.dll MyFirstUdp.vb   
```  
  
> [!NOTE]  
>  Начиная с версии [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], выполнение объектов баз данных языка Visual C++ (например, хранимых процедур), скомпилированных с параметром `/clr:pure`, не поддерживается.  
  
 Следующая инструкция DDL регистрирует результирующую сборку и вызывает точку входа:  
  
```  
CREATE ASSEMBLY MyFirstUdp FROM 'C:\Programming\MyFirstUdp.dll';  
CREATE PROCEDURE HelloWorld  
AS EXTERNAL NAME MyFirstUdp.StoredProcedures.HelloWorld;  
EXEC HelloWorld;  
```  
  
## <a name="see-also"></a>См. также  
 [Определяемые пользователем функции среды CLR](../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-functions.md)   
 [Определяемые пользователем типы CLR](../../relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types.md)   
 [Триггеры CLR](../../../2014/database-engine/dev-guide/clr-triggers.md)  
  
  
