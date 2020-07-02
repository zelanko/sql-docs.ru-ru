---
title: Доступ к текущей транзакции | Документация Майкрософт
description: В SQL Server интеграции со средой CLR текущее свойство класса System. Transactions. Transaction позволяет получить доступ к текущей транзакции.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- current transaction access
- Current property
- Transaction class
ms.assetid: 1a4e2ce5-f627-4c81-8960-6a9968cefda2
author: rothja
ms.author: jroth
ms.openlocfilehash: c82c4e4f5b1f1af6194ff409a684ca239881487a
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85765401"
---
# <a name="accessing-the-current-transaction"></a>Доступ к текущей транзакции
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Если транзакция является активной в той точке, в которой вызывается код среды CLR, применяемой в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , то транзакция становится доступной через класс **System.Transactions.Transaction** . Для доступа к текущей транзакции используется свойство **Transaction.Current** . В большинстве случаев в получении явного доступа к транзакции нет необходимости. Что касается подключений к базам данных, то в ADO.NET автоматически происходят проверка **Transaction.Current** при вызове метода **Connection.Open** и явное прикрепление соединения к этой транзакции (если только в строке соединения ключевое слово **Enlist** не задано равным false).  
  
 Необходимость в непосредственном использовании объекта **Transaction** может возникнуть в следующих случаях:  
  
-   если необходимо прикрепить ресурс, для которого не осуществляется автоматическое прикрепление, или который по какой-либо причине не был прикреплен во время инициализации;  
  
-   если необходимо явно прикрепить ресурс в транзакции;  
  
-   если необходимо завершить внешнюю транзакцию внутри хранимой процедуры или функции. В этом случае используется <xref:System.Transactions.TransactionScope>. Например, выполнение следующего кода приведет к откату текущей транзакции:  
  
    ```  
    using(TransactionScope transactionScope = new TransactionScope(TransactionScopeOptions.Required)) { }  
    ```  
  
 В остальной части раздела рассматриваются другие способы отмены внешней транзакции.  
  
## <a name="canceling-an-external-transaction"></a>Отмена внешней транзакции  
 Внешнюю транзакцию можно отменить из управляемой процедуры или функции следующими способами.  
  
-   Управляемая процедура или функция может возвратить какое-либо значение с помощью выходного параметра. В вызове процедуры [!INCLUDE[tsql](../../includes/tsql-md.md)] может быть предусмотрена проверка возвращаемого значения, и, в случае необходимости, выполнение **ROLLBACK TRANSACTION**.  
  
-   Управляемая процедура или функция может активизировать пользовательское исключение. В вызове процедуры [!INCLUDE[tsql](../../includes/tsql-md.md)] может быть перехвачено исключение, активизируемое управляемой процедурой или функцией в блоке try-catch, и выполнена инструкция **ROLLBACK TRANSACTION**.  
  
-   Управляемая процедура или функция может отменить текущую транзакцию путем вызова метода **Transaction.Rollback** , если соблюдается определенное условие.  
  
 При вызове в управляемой процедуре или функции метод **Transaction.Rollback** активизирует исключение с неоднозначным сообщением об ошибке и может быть заключен в блок try-catch. Сообщение об ошибке подобно следующему:  
  
```  
Msg 3994, Level 16, State 1, Procedure uspRollbackFromProc, Line 0  
Transaction is not allowed to roll back inside a user defined routine, trigger or aggregate because the transaction is not started in that CLR level. Change application logic to enforce strict transaction nesting.  
```  
  
 Это ожидаемое исключение, поэтому для продолжения выполнения кода необходим блок try-catch. Без блока try-catch в вызывающей процедуре [!INCLUDE[tsql](../../includes/tsql-md.md)] будет немедленно активизировано исключение, и выполнение управляемого кода завершится. Если выполнение управляемого кода завершается, то вызывается другое исключение:  
  
```  
Msg 3991, Level 16, State 1, Procedure uspRollbackFromProc, Line 1   
The context transaction which was active before entering user defined routine, trigger or aggregate " uspRollbackFromProc " has been ended inside of it, which is not allowed. Change application logic to enforce strict transaction nesting. The statement has been terminated.  
```  
  
 Это исключение также является ожидаемым, и чтобы обеспечить дальнейшее выполнение, необходимо заключить в блок try-catch инструкцию [!INCLUDE[tsql](../../includes/tsql-md.md)] , которая выполняет действие, вызывающее запуск триггера. Несмотря на два активизированных исключения, происходит откат транзакции, а изменения не фиксируются.  
  
### <a name="example"></a>Пример  
 Ниже приведен пример транзакции, откат которой осуществляется из управляемой процедуры с помощью метода **Transaction.Rollback** . Обратите внимание на то, что метод **Transaction.Rollback** в управляемом коде заключен в блок try-catch. В скрипте [!INCLUDE[tsql](../../includes/tsql-md.md)] создаются сборка и управляемая хранимая процедура. Следует иметь в виду, что инструкция **EXEC uspRollbackFromProc** заключена в блок try-catch, поэтому происходит перехват исключения, активизируемого при завершении выполнения управляемой процедуры.  
  
```csharp  
using System;  
using System.Data;  
using System.Data.SqlClient;  
using System.Data.SqlTypes;  
using Microsoft.SqlServer.Server;  
using System.Transactions;  
  
public partial class StoredProcedures  
{  
[Microsoft.SqlServer.Server.SqlProcedure]  
public static void uspRollbackFromProc()  
{  
   using (SqlConnection connection = new SqlConnection(@"context connection=true"))  
   {  
      // Open the connection.  
      connection.Open();  
  
      bool successCondition = true;  
  
      // Success condition is met.  
      if (successCondition)  
      {  
         SqlContext.Pipe.Send("Success condition met in procedure.");   
         // Perform other actions here.  
      }  
  
      //  Success condition is not met, the transaction will be rolled back.  
      else  
      {  
         SqlContext.Pipe.Send("Success condition not met in managed procedure. Transaction rolling back...");  
         try  
         {  
               // Get the current transaction and roll it back.  
               Transaction trans = Transaction.Current;  
               trans.Rollback();  
         }  
         catch (SqlException ex)  
         {  
            // Catch the expected exception.   
            // This allows the connection to close correctly.                      
         }    
      }  
  
      // Close the connection.  
      connection.Close();  
   }  
}  
};  
```  
  
```vb  
Imports System  
Imports System.Data  
Imports System.Data.SqlClient  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
Imports System.Transactions  
  
Partial Public Class StoredProcedures  
<Microsoft.SqlServer.Server.SqlProcedure()> _  
Public Shared Sub  uspRollbackFromProc ()  
   Using connection As New SqlConnection("context connection=true")  
  
   ' Open the connection.  
   connection.Open()  
  
   Dim successCondition As Boolean  
   successCondition = False  
  
   ' Success condition is met.  
   If successCondition Then  
  
      SqlContext.Pipe.Send("Success condition met in procedure.")  
  
      ' Success condition is not met, the transaction will be rolled back.  
  
   Else  
      SqlContext.Pipe.Send("Success condition not met in managed procedure. Transaction rolling back...")  
      Try  
         ' Get the current transaction and roll it back.  
         Dim trans As Transaction  
         trans = Transaction.Current  
         trans.Rollback()  
  
      Catch ex As SqlException  
         ' Catch the exception instead of throwing it.    
         ' This allows the connection to close correctly.                      
      End Try  
  
   End If  
  
   ' Close the connection.  
   connection.Close()  
  
End Using  
End Sub  
End Class  
```  
  
 **Transact-SQL**  
  
```  
--Register assembly.  
CREATE ASSEMBLY TestProcs FROM 'C:\Programming\TestProcs.dll'   
Go  
CREATE PROCEDURE uspRollbackFromProc AS EXTERNAL NAME TestProcs.StoredProcedures.uspRollbackFromProc  
Go  
  
-- Execute procedure.  
BEGIN TRY  
BEGIN TRANSACTION   
-- Perform other actions.  
Exec uspRollbackFromProc  
-- Perform other actions.  
PRINT N'Commiting transaction...'  
COMMIT TRANSACTION  
END TRY  
  
BEGIN CATCH  
SELECT ERROR_NUMBER() AS ErrorNum, ERROR_MESSAGE() AS ErrorMessage  
PRINT N'Exception thrown, rolling back transaction.'  
ROLLBACK TRANSACTION  
PRINT N'Transaction rolled back.'   
END CATCH  
Go  
  
-- Clean up.  
DROP Procedure uspRollbackFromProc;  
Go  
DROP ASSEMBLY TestProcs;  
Go  
```  
  
## <a name="see-also"></a>См. также  
 [Интеграция со средой CLR и транзакции](../../relational-databases/clr-integration-data-access-transactions/clr-integration-and-transactions.md)  
  
  
