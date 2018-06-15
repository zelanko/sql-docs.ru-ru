---
title: Объект SqlPipe | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: clr
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- custom result sets [CLR integration]
- SqlPipe object
- tabular results
ms.assetid: 3e090faf-085f-4c01-a565-79e3f1c36e3b
caps.latest.revision: 54
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 15786a3af4b6598f73c822a8196039ec3e335d2a
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32921569"
---
# <a name="sqlpipe-object"></a>Объект SqlPipe
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  В предыдущих версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]обычным было написание хранимой процедуры (или расширенной хранимой процедуры), которая отправляет результаты или выдает выходные параметры вызывающему клиенту.  
  
 В хранимой процедуре [!INCLUDE[tsql](../../includes/tsql-md.md)] любая инструкция **SELECT** , которая возвращает ноль или более строк, отправляет результаты в «канал» подключенного вызывающего.  
  
 Результаты по объектам базы данных CLR, работающей на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], могут отправляться в подключенный канал при помощи методов **Send** объекта **SqlPipe** . Обратитесь к свойству **Pipe** объекта **SqlContext** , чтобы получить объект **SqlPipe** . Класс **SqlPipe** принципиально подобен классу **Response** в ASP.NET. Дополнительные сведения см. в справочной документации по классу SqlPipe в пакете средств разработки программного обеспечения .NET Framework.  
  
## <a name="returning-tabular-results-and-messages"></a>Возврат табличных результатов и сообщений  
 Класс **SqlPipe** имеет метод **Send** , который имеет три перегрузки. Подробные сведения.  
  
-   `void Send(string message)`  
  
-   `void Send(SqlDataReader reader)`  
  
-   `void Send(SqlDataRecord record)`  
  
 Метод **Send** пересылает данные напрямую клиенту или вызывающему. Обычно клиент использует выход из **SqlPipe**, но в случае вложенных хранимых процедур CLR потребителем выхода также может быть хранимая процедура. Например, Procedure1 вызывает SqlCommand.ExecuteReader() с текстом команды «EXEC Procedure2». Procedure2 — это также управляемая хранимая процедура. Если Procedure2 вызывает SqlPipe.Send( SqlDataRecord ), строка передается модулю чтения Procedure1, но не клиенту.  
  
 Класс **Send** посылает строку сообщения, которая отображается на клиенте как информационное сообщение, эквивалентное PRINT в [!INCLUDE[tsql](../../includes/tsql-md.md)]. Метод может также послать однострочный результирующий набор с помощью **SqlDataRecord**или многострочный результирующий набор с использованием **SqlDataReader**.  
  
 Объект **SqlPipe** также имеет метод **ExecuteAndSend** . Этот метод можно использовать, чтобы выполнять команды (переданные как объект **SqlCommand** ) и напрямую отправлять результаты назад вызывающему. Если в представленной команде есть ошибки, исключения передаются в канал, но копия пересылается также вызывающему управляемому коду. Если вызывающий код не перехватывает исключение, оно распространяется по стеку в код [!INCLUDE[tsql](../../includes/tsql-md.md)] и дважды появляется в выходе. Если вызывающий код перехватывает исключение, потребитель канала по-прежнему видит ошибку, но повторяющейся ошибки нет.  
  
 Он может принять только команду **SqlCommand** , которая ассоциирована с контекстным соединением. Этот метод не может принять команду, которая сопоставлена соединению вне данного контекста.  
  
## <a name="returning-custom-result-sets"></a>Возвращение пользовательских результирующих наборов  
 Управляемые хранимые процедуры могут отправлять результирующие наборы, которые не исходят из **SqlDataReader**. Метод **SendResultsStart** вместе с методами **SendResultsRow** и **SendResultsEnd**позволяет хранимым процедурам отправлять клиенту пользовательские результирующие наборы.  
  
 Метод**SendResultsStart** принимает объект **SqlDataRecord** в качестве ввода. Он отмечает начало результирующего набора и при помощи метаданных записи составляет метаданные, описывающие результирующий набор. Он не отправляет значение записи с **SendResultsStart**. Все последующие строки, отправленные при помощи метода **SendResultsRow**, должны соответствовать этому определению метаданных.  
  
> [!NOTE]  
>  После вызова метода **SendResultsStart** можно вызвать только методы **SendResultsRow** и **SendResultsEnd** . Вызов любого другого метода в том же экземпляре объекта **SqlPipe** приводит к исключению **InvalidOperationException**. Метод**SendResultsEnd** возвращает объект **SqlPipe** в исходное состояние, в котором можно вызывать другие методы.  
  
### <a name="example"></a>Пример  
 Хранимая процедура **uspGetProductLine** возвращает название, номер продукта, цвет и цену по прейскуранту всех продуктов в указанной линейке продуктов. Эта хранимая процедура принимает точные совпадения с *prodLine*.  
  
 C#  
  
```  
using System;  
using System.Data;  
using System.Data.SqlClient;  
using System.Data.SqlTypes;  
using Microsoft.SqlServer.Server;  
  
public partial class StoredProcedures  
{  
[Microsoft.SqlServer.Server.SqlProcedure]  
public static void uspGetProductLine(SqlString prodLine)  
{  
    // Connect through the context connection.  
    using (SqlConnection connection = new SqlConnection("context connection=true"))  
    {  
        connection.Open();  
  
        SqlCommand command = new SqlCommand(  
            "SELECT Name, ProductNumber, Color, ListPrice " +  
            "FROM Production.Product " +   
            "WHERE ProductLine = @prodLine;", connection);  
  
        command.Parameters.AddWithValue("@prodLine", prodLine);  
  
        try  
        {  
            // Execute the command and send the results to the caller.  
            SqlContext.Pipe.ExecuteAndSend(command);  
        }  
        catch (System.Data.SqlClient.SqlException ex)  
        {  
            // An error occurred executing the SQL command.  
        }  
     }  
}  
};  
```  
  
 Visual Basic  
  
```  
Imports System  
Imports System.Data  
Imports System.Data.SqlClient  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
  
Partial Public Class StoredProcedures  
<Microsoft.SqlServer.Server.SqlProcedure()> _  
Public Shared Sub uspGetProductLine(ByVal prodLine As SqlString)  
    Dim command As SqlCommand  
  
    ' Connect through the context connection.  
    Using connection As New SqlConnection("context connection=true")  
        connection.Open()  
  
        command = New SqlCommand( _  
        "SELECT Name, ProductNumber, Color, ListPrice " & _  
        "FROM Production.Product " & _  
        "WHERE ProductLine = @prodLine;", connection)  
        command.Parameters.AddWithValue("@prodLine", prodLine)  
  
        Try  
            ' Execute the command and send the results   
            ' directly to the caller.  
            SqlContext.Pipe.ExecuteAndSend(command)  
        Catch ex As System.Data.SqlClient.SqlException  
            ' An error occurred executing the SQL command.  
        End Try  
    End Using  
End Sub  
End Class  
```  
  
 Следующая инструкция [!INCLUDE[tsql](../../includes/tsql-md.md)] выполняет процедуру **uspGetProduct** , которая возвращает список продуктов, относящихся к категории туристических велосипедов.  
  
```  
EXEC uspGetProductLineVB 'T';  
```  
  
## <a name="see-also"></a>См. также  
 [Объект SqlDataRecord](../../relational-databases/clr-integration-data-access-in-process-ado-net/sqldatarecord-object.md)   
 [Хранимые процедуры CLR](http://msdn.microsoft.com/library/bbdd51b2-a9b4-4916-ba6f-7957ac6c3f33)   
 [Внутрипроцессные расширения SQL Server для ADO.NET](../../relational-databases/clr-integration-data-access-in-process-ado-net/sql-server-in-process-specific-extensions-to-ado-net.md)  
  
  
