---
title: "BEGIN TRANSACTION (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: sql-data-warehouse, database-engine, pdw, sql-database
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- BEGIN_TRANSACTION_TSQL
- TRANSACTION_TSQL
- TRANSACTION
- BEGIN TRANSACTION
- BEGIN TRAN
- BEGIN_TRAN_TSQL
dev_langs: TSQL
helpviewer_keywords:
- transaction logs [SQL Server], BEGIN TRANSACTION statement
- marked transactions [SQL Server], BEGIN TRANSACTION statement
- BEGIN TRANSACTION statement
- local transactions [SQL Server]
- marking transactions [SQL Server]
- transactions [SQL Server], starting
- transaction names [SQL Server]
- starting point marked for transactions
- starting transactions
ms.assetid: c6258df4-11f1-416a-816b-54f98c11145e
caps.latest.revision: "56"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: d1e327dc8e5ce590ee3d2123b6049bbfc470d7b6
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="begin-transaction-transact-sql"></a>BEGIN TRANSACTION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-asdb-asdw-pdw-md.md)]

  Отмечает начальную точку явной локальной транзакции. Явные транзакции, начинаться с инструкции BEGIN TRANSACTION и заканчивается инструкцией COMMIT или ROLLBACK.  

 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
--Applies to SQL Server and Azure SQL Database
 
BEGIN { TRAN | TRANSACTION }   
    [ { transaction_name | @tran_name_variable }  
      [ WITH MARK [ 'description' ] ]  
    ]  
[ ; ]  
```  
 
```  
--Applies to Azure SQL Data Warehouse and Parallel Data Warehouse
 
BEGIN { TRAN | TRANSACTION }   
[ ; ]  
```  

  
## <a name="arguments"></a>Аргументы  
 *transaction_name*  
 **ПРИМЕНЯЕТСЯ к:** SQL Server (начиная с 2008), база данных SQL Azure
 
 Имя, присвоенное транзакции. *transaction_name* должны соответствовать правилам для идентификаторов, однако идентификаторы длиннее 32 символов не допускаются. Имена транзакций используются только для самых внешних вложенных инструкций BEGIN...COMMIT или BEGIN...ROLLBACK. *transaction_name* — всегда учитывается регистр, даже если экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] регистр не учитывается.  
  
 @*tran_name_variable*  
 **ПРИМЕНЯЕТСЯ к:** SQL Server (начиная с 2008), база данных SQL Azure
 
 Имя определенной пользователем переменной, содержащей допустимое имя транзакции. Переменная должна быть объявлена с **char**, **varchar**, **nchar**, или **nvarchar** тип данных. Если переменной передается больше 32 символов, используются только 32 первых символа, а остальные усекаются.  
  
 WITH MARK ["*описание*"]  
**ПРИМЕНЯЕТСЯ к:** SQL Server (начиная с 2008), база данных SQL Azure

Указывает, что транзакция отмечается в журнале. *Описание* — это строка, описывающая отметку. Объект *описание* более чем из 128 символов усекается до 128 символов перед сохранением в таблицу msdb.dbo.logmarkhistory.  
  
 Если используется предложение WITH MARK, необходимо указать имя транзакции. Предложение WITH MARK позволяет восстановить журнал транзакций до именованной отметки.  
  
## <a name="general-remarks"></a>Общие замечания
BEGIN TRANSACTION увеличивает значение@TRANCOUNT на 1.
  
Инструкция BEGIN TRANSACTION предоставляет точку, где гарантируется логическая и физическая согласованность данных, на которые ссылается соединение. При обнаружении ошибки, все изменения данных, сделанные после BEGIN TRANSACTION можно откат для возврата к известному состоянию согласованности данных. Каждая транзакция продолжается до тех пор, пока она не завершается без ошибок и выполняется инструкция COMMIT TRANSACTION, чтобы внести изменения в базу данных. В случае возникновения ошибок все изменения удаляются с помощью инструкции ROLLBACK TRANSACTION.  
  
Инструкция BEGIN TRANSACTION запускает локальную транзакцию для соединения, выполняющего эту инструкцию. В зависимости от текущих параметров уровня изоляции транзакции многие ресурсы, необходимые для поддержки выполняемых соединением инструкций языка [!INCLUDE[tsql](../../includes/tsql-md.md)], блокируются транзакцией до ее завершения с помощью инструкций COMMIT TRANSACTION и ROLLBACK TRANSACTION. Транзакции, долгое время ожидающие обработки, могут препятствовать доступу других пользователей к заблокированным ресурсам и усечения транзакций в журнале.  
  
 Хотя инструкция BEGIN TRANSACTION запускает локальную транзакцию, она не записывается в журнал транзакций, пока приложение не выполнит действие, которое должно быть записано в журнал, например инструкцию INSERT, UPDATE или DELETE. Приложение может выполнять такие действия, как получение блокировки для защиты уровня изоляции транзакции инструкции SELECT, но ни одно действие не записывается в журнал, пока приложение не выполнит действие, изменяющее данные.  
  
 Присвоение имен нескольким транзакциям в последовательности вложенных транзакций мало влияет на транзакцию. Системой регистрируется только первое (самое внешнее) имя транзакции. Откат к другому имени (не считая допустимого имени точки сохранения) приводит к формированию ошибки. В момент возникновения такой ошибки на самом деле не выполняется откат инструкций. Для этих инструкций выполняется откат только при откате внешней транзакции.  
  
 Локальная транзакция, запущенная инструкцией BEGIN TRANSACTION, повышается до распределенной транзакции, если до фиксации или отката инструкции выполняются следующие действия.  
  
-   Выполняется инструкция INSERT, DELETE или UPDATE, ссылающаяся на удаленную таблицу или связанный сервер. Инструкции INSERT, UPDATE или DELETE завершается сбоем, если поставщик OLE DB, используемый для доступа к связанному серверу не поддерживает интерфейс ITransactionJoin.  
  
-   Вызывается удаленная хранимая процедура, если для параметра REMOTE_PROC_TRANSACTIONS установлено значение ON.  
  
 Локальная копия [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] становится контроллером транзакции и использует [!INCLUDE[msCoName](../../includes/msconame-md.md)] координатора распределенных транзакций (MS DTC) для управления распределенной транзакцией.  
  
 Транзакция может выполняться явно как распределенная с помощью инструкции BEGIN DISTRIBUTED TRANSACTION. Дополнительные сведения см. в разделе [BEGIN DISTRIBUTED TRANSACTION &#40; Transact-SQL &#41; ](../../t-sql/language-elements/begin-distributed-transaction-transact-sql.md).  
  
 Если SET IMPLICIT_TRANSACTIONS задано как ON, то инструкция BEGIN TRANSACTION создает две вложенные транзакции. Дополнительные сведения см. в разделе [SET IMPLICIT_TRANSACTIONS &#40; Transact-SQL &#41;](../../t-sql/statements/set-implicit-transactions-transact-sql.md)  
  
## <a name="marked-transactions"></a>Помеченные транзакции  
 Если используется параметр WITH MARK, имя транзакции помещается в журнал транзакций. При восстановлении базы данных из копии до прежнего состояния вместо даты и времени может использоваться помеченная транзакция. Дополнительные сведения см. в разделе [использование помеченных транзакций для согласованного восстановления связанных баз данных &#40; Модель полного восстановления &#41; ](../../relational-databases/backup-restore/use-marked-transactions-to-recover-related-databases-consistently.md) и [восстановления &#40; Transact-SQL &#41; ](../../t-sql/statements/restore-statements-transact-sql.md).  
  
 Кроме того, отметки в журнале транзакций необходимы, если нужно восстановить набор взаимосвязанных баз данных до логически согласованного состояния. Отметки можно записывать в журналы транзакций взаимосвязанных баз данных с помощью распределенной транзакции. Восстановление набора взаимосвязанных баз данных по журналу до этих отметок приводит к транзакционной согласованности этого набора баз данных. Размещение отметок в связанных базах данных требует использования специальных процедур.  
  
 Отметка записывается в журнал транзакций только в том случае, если база данных обновляется помеченной транзакцией. Транзакции, не изменяющие данные, не отмечаются.  
  
 BEGIN TRAN *новое_имя* WITH MARK можно вкладывать в уже существующей транзакции, не помечены. При этом, *новое_имя* становится именем метки транзакции, несмотря на то, что транзакция может имя. В следующем примере `M2` является именем метки.  
  
```  
BEGIN TRAN T1;  
UPDATE table1 ...;  
BEGIN TRAN M2 WITH MARK;  
UPDATE table2 ...;  
SELECT * from table1;  
COMMIT TRAN M2;  
UPDATE table3 ...;  
COMMIT TRAN T1;  
```  
  
 При существовании вложенности транзакций попытка отметить транзакцию, уже имеющую метку, приводит к следующему предупреждению (не ошибке):  
  
 BEGIN TRAN T1 WITH MARK ...;  
  
 UPDATE table1 ...;  
  
 BEGIN TRAN M2 WITH MARK ...;  
  
 «Сервер: сообщение 3920, уровень 16, состояние 1, строка 3»  
  
 «Параметр WITH MARK применяется только к первой инструкции BEGIN TRAN WITH MARK.»  
  
 «Параметр не обрабатывается.»  
  
## <a name="permissions"></a>Permissions  
 Требуется членство в роли public.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-using-an-explicit-transaction"></a>A. С помощью явной транзакции
**ПРИМЕНЯЕТСЯ к:** SQL Server (начиная с 2008), база данных SQL Azure, хранилище данных SQL Azure, параллельное хранилище данных

В этом примере используется AdventureWorks. 

```
BEGIN TRANSACTION;  
DELETE FROM HumanResources.JobCandidate  
    WHERE JobCandidateID = 13;  
COMMIT;  
```

### <a name="b-rolling-back-a-transaction"></a>Б. Откат транзакции
**ПРИМЕНЯЕТСЯ к:** SQL Server (начиная с 2008), база данных SQL Azure, хранилище данных SQL Azure, параллельное хранилище данных

В следующем примере показано влияние откат транзакции. В этом примере инструкция ROLLBACK приведет к откату инструкции INSERT, но будет по-прежнему существовать созданную таблицу.

```
 
CREATE TABLE ValueTable (id int);  
BEGIN TRANSACTION;  
       INSERT INTO ValueTable VALUES(1);  
       INSERT INTO ValueTable VALUES(2);  
ROLLBACK;  

```

### <a name="c-naming-a-transaction"></a>В. Присвоение транзакции имени 
**ПРИМЕНЯЕТСЯ к:** SQL Server (начиная с 2008), база данных SQL Azure

В следующем примере показано, как присвоить транзакции имя.  
  
```  
DECLARE @TranName VARCHAR(20);  
SELECT @TranName = 'MyTransaction';  
  
BEGIN TRANSACTION @TranName;  
USE AdventureWorks2012;  
DELETE FROM AdventureWorks2012.HumanResources.JobCandidate  
    WHERE JobCandidateID = 13;  
  
COMMIT TRANSACTION @TranName;  
GO  
```  
  
### <a name="d-marking-a-transaction"></a>Г. Пометка транзакции  
**ПРИМЕНЯЕТСЯ к:** SQL Server (начиная с 2008), база данных SQL Azure

В следующем примере показано, как пометить транзакцию. Транзакция `CandidateDelete` помечена.  
  
```  
BEGIN TRANSACTION CandidateDelete  
    WITH MARK N'Deleting a Job Candidate';  
GO  
USE AdventureWorks2012;  
GO  
DELETE FROM AdventureWorks2012.HumanResources.JobCandidate  
    WHERE JobCandidateID = 13;  
GO  
COMMIT TRANSACTION CandidateDelete;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [BEGIN DISTRIBUTED TRANSACTION (Transact-SQL)](../../t-sql/language-elements/begin-distributed-transaction-transact-sql.md)   
 [COMMIT TRANSACTION (Transact-SQL)](../../t-sql/language-elements/commit-transaction-transact-sql.md)   
 [ФИКСАЦИЯ РАБОЧЕГО &#40; Transact-SQL &#41;](../../t-sql/language-elements/commit-work-transact-sql.md)   
 [ROLLBACK TRANSACTION (Transact-SQL)](../../t-sql/language-elements/rollback-transaction-transact-sql.md)   
 [ROLLBACK WORK &#40; Transact-SQL &#41;](../../t-sql/language-elements/rollback-work-transact-sql.md)   
 [SAVE TRANSACTION (Transact-SQL)](../../t-sql/language-elements/save-transaction-transact-sql.md)  
  
  
