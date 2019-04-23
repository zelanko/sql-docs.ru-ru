---
title: Триггеры CLR | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
dev_langs:
- TSQL
- VB
- CSharp
helpviewer_keywords:
- inserted tables
- database objects [CLR integration], triggers
- common language runtime [SQL Server], triggers
- updated columns
- building database objects [CLR integration], triggers
- triggers [CLR integration]
- deleted tables
- EventData property
- SqlTriggerContext class
- transactions [CLR integration]
ms.assetid: 302a4e4a-3172-42b6-9cc0-4a971ab49c1c
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 87d822e97a75bbd08375980fe6a6f0341d8f9c60
ms.sourcegitcommit: b87c384e10d6621cf3a95ffc79d6f6fad34d420f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60158540"
---
# <a name="clr-triggers"></a>Триггеры CLR
  Благодаря тому что [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] интегрирован со средой [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] CLR, для создания триггеров CLR можно использовать любой язык [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]. В настоящем разделе рассматриваются сведения, касающиеся реализации триггеров в условиях интеграции со средой CLR. Полное описание триггеров, см. в разделе [триггеры DDL](../../relational-databases/triggers/ddl-triggers.md).  
  
## <a name="what-are-triggers"></a>Что такое триггеры?  
 Триггером называют хранимую процедуру особого типа, которая автоматически выполняется при возникновении языкового события. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает два основных типа триггеров: языка обработки данных (DML) и триггеры языка DDL для определения данных. Триггеры DML можно использовать, когда инструкция `INSERT`, `UPDATE` или `DELETE` изменяет данные в указанной таблице или представлении. Триггеры DDL вызывают срабатывание хранимых процедур в ответ на самые разнообразные инструкции DDL. Как правило, это инструкции, начинающиеся со слов `CREATE`, `ALTER` и `DROP`. Триггеры DDL могут быть использованы в административных задачах, таких как аудит и регулирование операций базы данных.  
  
## <a name="unique-capabilities-of-clr-triggers"></a>Уникальные возможности триггеров CLR  
 Триггеры, код которых написан на языке [!INCLUDE[tsql](../../includes/tsql-md.md)], позволяют определить обновленные столбцы в представлении или таблице, активизировавшей триггер, с помощью функций `UPDATE(column)` и `COLUMNS_UPDATED()`.  
  
 Триггеры, код которых написан на одном из языков среды CLR, отличаются от других объектов интеграции со средой CLR в нескольких существенных чертах. Триггеры CLR позволяют:  
  
-   ссылаться на данные в таблицах `INSERTED` и `DELETED`;  
  
-   определять, какие столбцы были изменены в результате операции `UPDATE`;  
  
-   получать доступ к сведениям об объектах базы данных, затронутых в результате выполнения инструкций языка DDL.  
  
 Эти возможности предоставляются непосредственно в языке запросов или с помощью класса `SqlTriggerContext`. Дополнительные сведения о преимуществах интеграции со средой CLR и выборе между управляемым кодом и [!INCLUDE[tsql](../../includes/tsql-md.md)], см. в разделе [Общие сведения об интеграции со средой CLR](../../relational-databases/clr-integration/clr-integration-overview.md).  
  
## <a name="using-the-sqltriggercontext-class"></a>Использование класса SqlTriggerContext  
 Класс `SqlTriggerContext` не может быть создан как общедоступный и может быть получен только путем доступа к свойству `SqlContext.TriggerContext` в коде триггера CLR. Класс `SqlTriggerContext` можно получить из активного контекста `SqlContext` путем вызова свойства `SqlContext.TriggerContext`:  
  
 `SqlTriggerContext myTriggerContext = SqlContext.TriggerContext;`  
  
 Класс `SqlTriggerContext` предоставляет сведения контекста о триггере. К этим контекстным сведениям относится тип действия, которое вызвало запуск триггера, столбцы, измененные в операции UPDATE, а в случае триггера DDL — структура XML `EventData`, описывающая операцию запуска триггера. Дополнительные сведения см. в разделе [EVENTDATA &#40;Transact-SQL&#41;](/sql/t-sql/functions/eventdata-transact-sql).  
  
### <a name="determining-the-trigger-action"></a>Определение триггерного действия  
 После получения значения `SqlTriggerContext` его можно использовать для определения типа действия, которое вызвало запуск триггера. К этим данным можно обращаться с помощью свойства `TriggerAction` класса `SqlTriggerContext`.  
  
 Что касается триггеров DML, то свойство `TriggerAction` может иметь одно из следующих значений.  
  
-   TriggerAction.Update (0x1)  
  
-   TriggerAction.Insert (0x2)  
  
-   TriggerAction.Delete (0x3)  
  
-   Что касается триггеров DDL, то список возможных значений TriggerAction намного больше. Дополнительные сведения см. в разделе «Перечисления TriggerAction» пакета SDK для платформы .NET Framework.  
  
### <a name="using-the-inserted-and-deleted-tables"></a>Использование таблиц inserted и deleted  
 В инструкциях триггеров DML используются два вида специальных таблиц: **вставлены** таблицы и **удалены** таблицы. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] автоматически создает эти таблицы и управляет ими. Указанные временные таблицы можно использовать для проверки эффективности определенных операций модификации данных и для задания условий выполнения некоторых действий триггера DML; однако изменять данные в этих таблицах напрямую нельзя.  
  
 Триггеры CLR можно получить доступ к **вставлены** и **удалены** таблиц с помощью внутрипроцессного поставщика среды CLR. Это осуществляется путем получения объекта `SqlCommand` из объекта SqlContext. Пример:  
  
 C#  
  
```  
SqlConnection connection = new SqlConnection ("context connection = true");  
connection.Open();  
SqlCommand command = connection.CreateCommand();  
command.CommandText = "SELECT * from " + "inserted";  
```  
  
 Visual Basic  
  
```  
Dim connection As New SqlConnection("context connection=true")  
Dim command As SqlCommand  
connection.Open()  
command = connection.CreateCommand()  
command.CommandText = "SELECT * FROM " + "inserted"  
```  
  
### <a name="determining-updated-columns"></a>Определение обновленных столбцов  
 Определить количество столбцов, которые были изменены операцией UPDATE, можно с помощью свойства `ColumnCount` объекта `SqlTriggerContext`. Чтобы определить, был ли обновлен столбец, можно использовать метод `IsUpdatedColumn`, принимающий в качестве входного параметра порядковый номер столбца. Значение `True` указывает, что столбец был обновлен.  
  
 Например, этот фрагмент кода (из триггера EmailAudit, приведенного далее в этом разделе) перечисляет все обновляемые столбцы:  
  
 C#  
  
```  
reader = command.ExecuteReader();  
reader.Read();  
for (int columnNumber = 0; columnNumber < triggContext.ColumnCount; columnNumber++)  
{  
   pipe.Send("Updated column "  
      + reader.GetName(columnNumber) + "? "  
   + triggContext.IsUpdatedColumn(columnNumber).ToString());  
 }  
  
 reader.Close();  
```  
  
 Visual Basic  
  
```  
reader = command.ExecuteReader()  
reader.Read()  
Dim columnNumber As Integer  
  
For columnNumber=0 To triggContext.ColumnCount-1  
  
   pipe.Send("Updated column " & reader.GetName(columnNumber) & _  
   "? " & triggContext.IsUpdatedColumn(columnNumber).ToString() )  
  
Next  
  
reader.Close()  
```  
  
### <a name="accessing-eventdata-for-clr-ddl-triggers"></a>Доступ к функции EventData для триггеров CLR DDL  
 Триггеры DDL, как и обычные триггеры, вызывают срабатывание хранимых процедур в ответ на событие. Однако, в отличие от триггеров DML, они не срабатывают в ответ на инструкции UPDATE, INSERT или DELETE для таблицы или представления. Вместо этого они запускаются в ответ на выполнение целого ряда инструкций DDL, которые главным образом представляют собой инструкции, начинающиеся с ключевых слов CREATE, ALTER и DROP. Триггеры DDL могут использоваться для выполнения таких административных задач, как аудит и контроль над выполнением операций базы данных и изменения схемы.  
  
 Сведения о событии, запускающем триггер DDL, доступны в свойстве `EventData` класса `SqlTriggerContext`. Это свойство содержит значение `xml`. Эта XML-схема включает следующую информацию:  
  
-   время формирования события;  
  
-   идентификатор системного процесса (SPID) для соединения, во время которого был выполнен триггер;  
  
-   тип события, которое привело к срабатыванию триггера.  
  
 В зависимости от типа события эта схема включает также дополнительные сведения, такие как сведения о базе данных, в которой было сформировано событие, об объекте, в контексте которого оно было сформировано, и о команде [!INCLUDE[tsql](../../includes/tsql-md.md)], сформировавшей событие.  
  
 В следующем примере следующий триггер DDL возвращает необработанное значение свойства `EventData`.  
  
> [!NOTE]  
>  В этом примере отправка результатов и сообщений через объект `SqlPipe` показана только в иллюстративных целях и, как правило, не рекомендуется для применения в коде производственного назначения при программировании триггеров CLR. Возврат дополнительных данных может оказаться непредвиденным и привести к ошибкам приложения.  
  
 C#  
  
```  
using System;  
using System.Data;  
using System.Data.Sql;  
using Microsoft.SqlServer.Server;  
using System.Data.SqlClient;  
using System.Data.SqlTypes;  
using System.Xml;  
using System.Text.RegularExpressions;  
  
public class CLRTriggers  
{  
   public static void DropTableTrigger()  
   {  
       SqlTriggerContext triggContext = SqlContext.TriggerContext;             
  
       switch(triggContext.TriggerAction)  
       {  
           case TriggerAction.DropTable:  
           SqlContext.Pipe.Send("Table dropped! Here's the EventData:");  
           SqlContext.Pipe.Send(triggContext.EventData.Value);  
           break;  
  
           default:  
           SqlContext.Pipe.Send("Something happened! Here's the EventData:");  
           SqlContext.Pipe.Send(triggContext.EventData.Value);  
           break;  
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
  
'The Partial modifier is only required on one class definition per project.  
Partial Public Class CLRTriggers   
  
    Public Shared Sub DropTableTrigger()  
        Dim triggContext As SqlTriggerContext  
        triggContext = SqlContext.TriggerContext  
  
        Select Case triggContext.TriggerAction  
           Case TriggerAction.DropTable  
              SqlContext.Pipe.Send("Table dropped! Here's the EventData:")  
              SqlContext.Pipe.Send(triggContext.EventData.Value)  
  
           Case Else  
              SqlContext.Pipe.Send("Something else happened! Here's the EventData:")  
              SqlContext.Pipe.Send(triggContext.EventData.Value)  
  
        End Select  
    End Sub  
End Class     
```  
  
 Следующая выходная выборка является значением свойства `EventData` после того, как событие `CREATE TABLE` вызвало срабатывание триггера DDL:  
  
 `<EVENT_INSTANCE><PostTime>2004-04-16T21:17:16.160</PostTime><SPID>58</SPID><EventType>CREATE_TABLE</EventType><ServerName>MACHINENAME</ServerName><LoginName>MYDOMAIN\myname</LoginName><UserName>MYDOMAIN\myname</UserName><DatabaseName>AdventureWorks</DatabaseName><SchemaName>dbo</SchemaName><ObjectName>UserName</ObjectName><ObjectType>TABLE</ObjectType><TSQLCommand><SetOptions ANSI_NULLS="ON" ANSI_NULL_DEFAULT="ON" ANSI_PADDING="ON" QUOTED_IDENTIFIER="ON" ENCRYPTED="FALSE" /><CommandText>create table dbo.UserName  
(  
 UserName varchar(50),  
 RealName varchar(50)  
)  
</CommandText></TSQLCommand></EVENT_INSTANCE>`  
  
 Помимо сведений, доступ к которым можно получить через класс `SqlTriggerContext`, запросы могут также ссылаться на `COLUMNS_UPDATED` и inserted/deleted в тексте команды, выполняемой внутри процесса.  
  
## <a name="sample-clr-trigger"></a>Образец триггера CLR  
 В этом примере рассматривается сценарий, в котором пользователю предоставляется возможность выбрать любой идентификатор, но требуется определить, какие именно пользователи ввели в качестве идентификатора адрес электронной почты. Описанный ниже триггер обнаруживает эти данные и регистрирует их в таблице аудита.  
  
> [!NOTE]  
>  В этом примере отправка результатов и сообщений через объект `SqlPipe` показана только в иллюстративных целях и, как правило, не рекомендуется для применения в коде производственного назначения. Возврат дополнительных данных может оказаться непредвиденным и привести к ошибкам приложения.  
  
```csharp  
using System;  
using System.Data;  
using System.Data.Sql;  
using Microsoft.SqlServer.Server;  
using System.Data.SqlClient;  
using System.Data.SqlTypes;  
using System.Xml;  
using System.Text.RegularExpressions;  
  
public class CLRTriggers  
{  
   [SqlTrigger(Name = @"EmailAudit", Target = "[dbo].[Users]", Event = "FOR INSERT, UPDATE, DELETE")]  
   public static void EmailAudit()  
   {  
      string userName;  
      string realName;  
      SqlCommand command;  
      SqlTriggerContext triggContext = SqlContext.TriggerContext;  
      SqlPipe pipe = SqlContext.Pipe;  
      SqlDataReader reader;  
  
      switch (triggContext.TriggerAction)  
      {  
         case TriggerAction.Insert:  
         // Retrieve the connection that the trigger is using  
         using (SqlConnection connection  
            = new SqlConnection(@"context connection=true"))  
         {  
            connection.Open();  
            command = new SqlCommand(@"SELECT * FROM INSERTED;",  
               connection);  
            reader = command.ExecuteReader();  
            reader.Read();  
            userName = (string)reader[0];  
            realName = (string)reader[1];  
            reader.Close();  
  
            if (IsValidEMailAddress(userName))  
            {  
               command = new SqlCommand(  
                  @"INSERT [dbo].[UserNameAudit] VALUES ('"  
                  + userName + @"', '" + realName + @"');",  
                  connection);  
               pipe.Send(command.CommandText);  
               command.ExecuteNonQuery();  
               pipe.Send("You inserted: " + userName);  
            }  
         }  
  
         break;  
  
         case TriggerAction.Update:  
         // Retrieve the connection that the trigger is using  
         using (SqlConnection connection  
            = new SqlConnection(@"context connection=true"))  
         {  
            connection.Open();  
            command = new SqlCommand(@"SELECT * FROM INSERTED;",  
               connection);  
            reader = command.ExecuteReader();  
            reader.Read();  
  
            userName = (string)reader[0];  
            realName = (string)reader[1];  
  
            pipe.Send(@"You updated: '" + userName + @"' - '"  
               + realName + @"'");  
  
            for (int columnNumber = 0; columnNumber < triggContext.ColumnCount; columnNumber++)  
            {  
               pipe.Send("Updated column "  
                  + reader.GetName(columnNumber) + "? "  
                  + triggContext.IsUpdatedColumn(columnNumber).ToString());  
            }  
  
            reader.Close();  
         }  
  
         break;  
  
         case TriggerAction.Delete:  
            using (SqlConnection connection  
               = new SqlConnection(@"context connection=true"))  
               {  
                  connection.Open();  
                  command = new SqlCommand(@"SELECT * FROM DELETED;",  
                     connection);  
                  reader = command.ExecuteReader();  
  
                  if (reader.HasRows)  
                  {  
                     pipe.Send(@"You deleted the following rows:");  
                     while (reader.Read())  
                     {  
                        pipe.Send(@"'" + reader.GetString(0)  
                        + @"', '" + reader.GetString(1) + @"'");  
                     }  
  
                     reader.Close();  
  
                     //alternately, to just send a tabular resultset back:  
                     //pipe.ExecuteAndSend(command);  
                  }  
                  else  
                  {  
                     pipe.Send("No rows affected.");  
                  }  
               }  
  
               break;  
            }  
        }  
  
     public static bool IsValidEMailAddress(string email)  
     {  
         return Regex.IsMatch(email, @"^([\w-]+\.)*?[\w-]+@[\w-]+\.([\w-]+\.)*?[\w]+$");  
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
Imports System.Text.RegularExpressions  
  
'The Partial modifier is only required on one class definition per project.  
Partial Public Class CLRTriggers   
  
    <SqlTrigger(Name:="EmailAudit", Target:="[dbo].[Users]", Event:="FOR INSERT, UPDATE, DELETE")> _  
    Public Shared Sub EmailAudit()  
        Dim userName As String  
        Dim realName As String  
        Dim command As SqlCommand  
        Dim triggContext As SqlTriggerContext  
        Dim pipe As SqlPipe  
        Dim reader As SqlDataReader    
  
        triggContext = SqlContext.TriggerContext      
        pipe = SqlContext.Pipe    
  
        Select Case triggContext.TriggerAction  
           Case TriggerAction.Insert  
              Using connection As New SqlConnection("context connection=true")  
                 connection.Open()  
                 command = new SqlCommand("SELECT * FROM INSERTED;", connection)  
  
                 reader = command.ExecuteReader()  
                 reader.Read()  
  
                 userName = CType(reader(0), String)  
                 realName = CType(reader(1), String)  
  
                 reader.Close()  
  
                 If IsValidEmailAddress(userName) Then  
                     command = New SqlCommand("INSERT [dbo].[UserNameAudit] VALUES ('" & _  
                       userName & "', '" & realName & "');", connection)  
  
                    pipe.Send(command.CommandText)  
                    command.ExecuteNonQuery()  
                    pipe.Send("You inserted: " & userName)  
  
                 End If  
              End Using  
  
           Case TriggerAction.Update  
              Using connection As New SqlConnection("context connection=true")  
                 connection.Open()  
                 command = new SqlCommand("SELECT * FROM INSERTED;", connection)  
  
                 reader = command.ExecuteReader()  
                 reader.Read()  
  
                 userName = CType(reader(0), String)  
                 realName = CType(reader(1), String)  
  
                 pipe.Send("You updated: " & userName & " - " & realName)  
  
                 Dim columnNumber As Integer  
  
                 For columnNumber=0 To triggContext.ColumnCount-1  
  
                    pipe.Send("Updated column " & reader.GetName(columnNumber) & _  
                      "? " & triggContext.IsUpdatedColumn(columnNumber).ToString() )  
  
                 Next  
  
                 reader.Close()  
              End Using  
  
           Case TriggerAction.Delete  
              Using connection As New SqlConnection("context connection=true")  
                 connection.Open()  
                 command = new SqlCommand("SELECT * FROM DELETED;", connection)  
  
                 reader = command.ExecuteReader()  
  
                 If reader.HasRows Then  
                    pipe.Send("You deleted the following rows:")  
  
                    While reader.Read()  
  
                       pipe.Send( reader.GetString(0) & ", " & reader.GetString(1) )  
  
                    End While   
  
                    reader.Close()  
  
                    ' Alternately, just send a tabular resultset back:  
                    ' pipe.ExecuteAndSend(command)  
  
                 Else  
                   pipe.Send("No rows affected.")  
                 End If  
  
              End Using   
        End Select  
    End Sub  
  
    Public Shared Function IsValidEMailAddress(emailAddress As String) As Boolean  
  
       return Regex.IsMatch(emailAddress, "^([\w-]+\.)*?[\w-]+@[\w-]+\.([\w-]+\.)*?[\w]+$")  
    End Function      
End Class  
```  
  
 Предположим, что в базе данных имеются две таблицы со следующими определениями:  
  
```  
CREATE TABLE Users  
(  
    UserName nvarchar(200) NOT NULL,  
    RealName nvarchar(200) NOT NULL  
);  
GO CREATE TABLE UserNameAudit  
(  
    UserName nvarchar(200) NOT NULL,  
    RealName nvarchar(200) NOT NULL  
)  
```  
  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] Инструкцию, которая создает триггер в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выглядит следующим образом и предполагает, что сборка **SQLCLRTest** уже зарегистрирован в текущем [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базы данных.  
  
```  
CREATE TRIGGER EmailAudit  
ON Users  
FOR INSERT, UPDATE, DELETE  
AS  
EXTERNAL NAME SQLCLRTest.CLRTriggers.EmailAudit  
```  
  
## <a name="validating-and-canceling-invalid-transactions"></a>Проверка и отмена недопустимых транзакций  
 Применение триггеров для проверки и отмены недопустимых транзакций INSERT, UPDATE или DELETE либо для предотвращения изменения схемы базы данных является стандартным. Достигается это за счет внедрения логики проверки в код триггера и отката текущей транзакции, если действие не удовлетворяет критериям проверки.  
  
 При вызове метода `Transaction.Rollback` или SqlCommand внутри триггера с текстом команды «TRANSACTION ROLLBACK» возникает исключение с неоднозначным сообщением об ошибке; этот метод необходимо упаковать в блок TRY/CATCH. Отображается примерно следующее сообщение об ошибке.  
  
```  
Msg 6549, Level 16, State 1, Procedure trig_InsertValidator, Line 0  
A .NET Framework error occurred during execution of user defined routine or aggregate 'trig_InsertValidator':   
System.Data.SqlClient.SqlException: Transaction is not allowed to roll back inside a user defined routine, trigger or aggregate because the transaction is not started in that CLR level. Change application logic to enforce strict transaction nesting... User transaction, if any, will be rolled back.  
```  
  
 Это ожидаемое исключение, поэтому для продолжения выполнения кода необходим блок try-catch. По завершении выполнения кода триггера возникает еще одно исключение.  
  
```  
Msg 3991, Level 16, State 1, Procedure trig_InsertValidator, Line 1   
The context transaction which was active before entering user defined routine, trigger or aggregate "trig_InsertValidator" has been ended inside of it, which is not allowed. Change application logic to enforce strict transaction nesting.  
The statement has been terminated.  
```  
  
 Это исключение также является ожидаемым, а блок TRY/CATCH вокруг инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)], которая выполняет действие, вызывающее срабатывание триггера, необходим, чтобы выполнение продолжилось. Несмотря на возникновение двух исключений, откат транзакции выполняется, а изменения не фиксируются в таблицу. Основная разница между триггерами CLR и триггерами [!INCLUDE[tsql](../../includes/tsql-md.md)] состоит в том, что триггеры [!INCLUDE[tsql](../../includes/tsql-md.md)] могут продолжать работать после выполнения отката.  
  
### <a name="example"></a>Пример  
 Следующий триггер выполняет простую проверку инструкций INSERT для таблицы. Если вставляемое целое значение равно единице, будет выполнен откат транзакции, а значение не будет вставлено в таблицу. Все остальные целые значения будут вставлены в таблицу. Заметьте, что вокруг метода `Transaction.Rollback` расположен блок TRY/CATCH. Скрипт [!INCLUDE[tsql](../../includes/tsql-md.md)] создает тестовую таблицу, сборку и управляемую хранимую процедуру. Следует отметить, что две инструкции INSERT упакованы в блок TRY/CATCH с тем, чтобы перехватить исключения, которые возникают при завершении выполнения триггера.  
  
 C#  
  
```  
using System;  
using System.Data.SqlClient;  
using Microsoft.SqlServer.Server;  
using System.Transactions;  
  
public partial class Triggers  
{  
    // Enter existing table or view for the target and uncomment the attribute line  
    // [Microsoft.SqlServer.Server.SqlTrigger (Name="trig_InsertValidator", Target="Table1", Event="FOR INSERT")]  
    public static void trig_InsertValidator()  
    {  
        using (SqlConnection connection = new SqlConnection(@"context connection=true"))  
        {  
            SqlCommand command;  
            SqlDataReader reader;  
            int value;  
  
            // Open the connection.  
            connection.Open();  
  
            // Get the inserted value.  
            command = new SqlCommand(@"SELECT * FROM INSERTED", connection);  
            reader = command.ExecuteReader();  
            reader.Read();  
            value = (int)reader[0];  
            reader.Close();  
  
            // Rollback the transaction if a value of 1 was inserted.  
            if (1 == value)  
            {  
                try  
                {  
                    // Get the current transaction and roll it back.  
                    Transaction trans = Transaction.Current;  
                    trans.Rollback();                      
                }  
                catch (SqlException ex)  
                {  
                    // Catch the expected exception.                      
                }  
            }  
            else  
            {  
                // Perform other actions here.  
            }  
  
            // Close the connection.  
            connection.Close();              
        }  
    }  
}  
```  
  
 Visual Basic  
  
```  
Imports System  
Imports System.Data.SqlClient  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
Imports System.Transactions  
  
Partial Public Class Triggers  
' Enter existing table or view for the target and uncomment the attribute line  
' <Microsoft.SqlServer.Server.SqlTrigger(Name:="trig_InsertValidator", Target:="Table1", Event:="FOR INSERT")> _  
Public Shared Sub  trig_InsertValidator ()  
    Using connection As New SqlConnection("context connection=true")  
  
        Dim command As SqlCommand  
        Dim reader As SqlDataReader  
        Dim value As Integer  
  
        ' Open the connection.  
        connection.Open()  
  
        ' Get the inserted value.  
        command = New SqlCommand("SELECT * FROM INSERTED", connection)  
        reader = command.ExecuteReader()  
        reader.Read()  
        value = CType(reader(0), Integer)  
        reader.Close()  
  
        ' Rollback the transaction if a value of 1 was inserted.  
        If value = 1 Then  
  
            Try  
                ' Get the current transaction and roll it back.  
                Dim trans As Transaction  
                trans = Transaction.Current  
                trans.Rollback()  
  
            Catch ex As SqlException  
  
                ' Catch the exception.                      
            End Try  
        Else  
  
            ' Perform other actions here.  
        End If  
  
        ' Close the connection.  
        connection.Close()  
    End Using  
End Sub  
End Class  
```  
  
 Transact-SQL  
  
```  
-- Create the test table, assembly, and trigger.  
CREATE TABLE Table1(c1 int);  
go  
  
CREATE ASSEMBLY ValidationTriggers from 'E:\programming\ ValidationTriggers.dll';  
go  
  
CREATE TRIGGER trig_InsertValidator  
ON Table1  
FOR INSERT  
AS EXTERNAL NAME ValidationTriggers.Triggers.trig_InsertValidator;  
go  
  
-- Use a Try/Catch block to catch the expected exception  
BEGIN TRY  
   INSERT INTO Table1 VALUES(42)  
   INSERT INTO Table1 VALUES(1)  
END TRY  
BEGIN CATCH  
  SELECT ERROR_NUMBER() AS ErrorNum, ERROR_MESSAGE() AS ErrorMessage  
END CATCH;  
  
-- Clean up.  
DROP TRIGGER trig_InsertValidator;  
DROP ASSEMBLY ValidationTriggers;  
DROP TABLE Table1;  
```  
  
## <a name="see-also"></a>См. также  
 [CREATE TRIGGER (Transact-SQL)](/sql/t-sql/statements/create-trigger-transact-sql)   
 [Триггеры DML](../../relational-databases/triggers/dml-triggers.md)   
 [Триггеры DDL](../../relational-databases/triggers/ddl-triggers.md)   
 [TRY...CATCH (Transact-SQL)](/sql/t-sql/language-elements/try-catch-transact-sql)   
 [Построение объектов базы данных с помощью среды CLR &#40;CLR&#41; интеграции](../../relational-databases/clr-integration/database-objects/building-database-objects-with-common-language-runtime-clr-integration.md)   
 [EVENTDATA (Transact-SQL)](/sql/t-sql/functions/eventdata-transact-sql)  
  
  
