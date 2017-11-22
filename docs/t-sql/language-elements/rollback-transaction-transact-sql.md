---
title: "Инструкция ROLLBACK TRANSACTION (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 09/12/2017
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
- ROLLBACK TRANSACTION
- ROLLBACK
- ROLLBACK_TSQL
- ROLLBACK_TRANSACTION_TSQL
dev_langs: TSQL
helpviewer_keywords:
- transaction rollbacks [SQL Server]
- ROLLBACK TRANSACTION statement
- erasing data modifications [SQL Server]
- rolling back transactions, ROLLBACK TRANSACTION
- roll back transactions [SQL Server]
- savepoints [SQL Server]
ms.assetid: 6882c5bc-ff74-476a-984b-164aeb036c66
caps.latest.revision: "52"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: be1bbb9e63ccb710b42e007c91c1c588a1e8ae1d
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="rollback-transaction-transact-sql"></a>ROLLBACK TRANSACTION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-asdb-asdw-pdw-md.md)]

  Откатывает явные или неявные транзакции до начала или до точки сохранения транзакции. ROLLBACK TRANSACTION можно использовать для отмены всех изменений данных, произведенных с начала транзакции или до точки сохранения. Она также освобождает ресурсы, используемые транзакцией.  
  

 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
ROLLBACK { TRAN | TRANSACTION }   
     [ transaction_name | @tran_name_variable  
     | savepoint_name | @savepoint_variable ]   
[ ; ]  
```  
  
## <a name="arguments"></a>Аргументы  
 *transaction_name*  
 Имя, присвоенное транзакции в BEGIN TRANSACTION. *transaction_name* должны соответствовать правилам для идентификаторов, но используются только первые 32 символа имени транзакции. При вложении транзакций *transaction_name* должно быть имя из внешней инструкции BEGIN TRANSACTION. *transaction_name* всегда учитывается регистр, даже если экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не учитывается регистр знаков.  
  
 **@***tran_name_variable*  
 Имя определенной пользователем переменной, содержащей допустимое имя транзакции. Переменная должна быть объявлена с **char**, **varchar**, **nchar**, или **nvarchar** тип данных.  
  
 *savepoint_name*  
 — *Savepoint_name* из инструкции SAVE TRANSACTION. *savepoint_name* должны соответствовать правилам для идентификаторов. Используйте *savepoint_name* при откат по условию должен влиять только часть транзакции.  
  
 **@***savepoint_variable*  
 Имя пользовательской переменной, содержащей допустимое имя точки сохранения. Переменная должна быть объявлена с **char**, **varchar**, **nchar**, или **nvarchar** тип данных.  
  
## <a name="error-handling"></a>Обработка ошибок  
 Инструкция ROLLBACK TRANSACTION не выдает никаких сообщений пользователю. Если нужны предупреждения в хранимой процедуре или триггере, используйте инструкции RAISERROR или PRINT. Инструкция RAISERROR предпочтительна для отображения ошибок.  
  
## <a name="general-remarks"></a>Общие замечания  
 Инструкция ROLLBACK TRANSACTION без *savepoint_name* или *transaction_name* выполняет откат начало транзакции. При наличии вложенных транзакций эта инструкция откатывает все внутренние транзакции к началу самой внешней инструкции BEGIN TRANSACTION. В обоих случаях инструкция ROLLBACK TRANSACTION уменьшает @@TRANCOUNT системная функция 0. Инструкция ROLLBACK TRANSACTION *savepoint_name* не уменьшает@TRANCOUNT.  
  
 Инструкция ROLLBACK TRANSACTION не может ссылаться на *savepoint_name* в распределенных транзакциях, запущенных явно с помощью BEGIN DISTRIBUTED TRANSACTION или вызванных из локальной транзакции.  
  
 Нельзя выполнить откат транзакции после выполнения инструкции COMMIT TRANSACTION, кроме случая, когда инструкция COMMIT TRANSACTION связана с вложенной транзакцией, которая содержится внутри откатываемой транзакции. В этом случае будет вложенные транзакции выполняется откат, даже если для нее была выполнена инструкция COMMIT TRANSACTION.  
  
 Внутри транзакции допускается использование повторяющихся имен точки сохранения, но инструкция ROLLBACK TRANSACTION, использующая повторяющееся имя точки сохранения, откатывает транзакцию лишь к самой последней точке, установленной с помощью инструкции SAVE TRANSACTION для этого имени.  
  
## <a name="interoperability"></a>Совместимость  
 В хранимых процедурах инструкция ROLLBACK TRANSACTION без *savepoint_name* или *transaction_name* откатывает все инструкции внешней инструкции BEGIN TRANSACTION. Инструкция ROLLBACK TRANSACTION в хранимой процедуре, которая приводит @@TRANCOUNT иметь другое значение, при завершении хранимой процедуры, чем @@TRANCOUNT значение при вызове хранимой процедуры вызывает информационное сообщение. Это сообщение не влияет на последующую обработку.  
  
 Если инструкция ROLLBACK TRANSACTION запускается в триггере, происходит следующее:  
  
-   Все изменения данных, сделанные к настоящему времени в текущей базе данных, откатываются, включая изменения, сделанные триггером.  
  
-   Триггер продолжает выполнять все оставшиеся инструкции после инструкции ROLLBACK. Если какая-нибудь из инструкций изменит данные, откат этих изменений выполнен не будет. Вложенные триггеры не выполняются при выполнении оставшихся инструкций.  
  
-   Инструкции в пакете, следующие за инструкцией, вызвавшей срабатывание триггера, не выполняются.  
  
@@TRANCOUNT увеличивается на единицу при срабатывании триггера даже в режиме автоматической фиксации. (Система обрабатывает триггер как неявную вложенную транзакцию.)  
  
Инструкция ROLLBACK TRANSACTION в хранимой процедуре не влияет на последующие инструкции в пакете, вызвавшем процедуру; последующие инструкции в пакете выполняются. Инструкции ROLLBACK TRANSACTION в триггерах уничтожают пакет, содержащий инструкцию, вызвавшую триггер; последующие инструкции в пакете не выполняются.  
  
Эффект, оказываемый инструкцией ROLLBACK на курсоры, определяется тремя правилами:  
  
1.  Если параметр CURSOR_CLOSE_ON_COMMIT установлен в ON, инструкция ROLLBACK закрывает, но не освобождает все открытые курсоры.  
  
2.  Если параметр CURSOR_CLOSE_ON_COMMIT установлен в OFF, инструкция ROLLBACK не влияет на открытые синхронные курсоры типа STATIC или INSENSITIVE или асинхронные курсоры типа STATIC, которые были полностью заполнены. Открытые курсоры любого другого типа закрываются, но не освобождаются.  
  
3.  Ошибка, которая уничтожает пакет и формирует внутренний откат, освобождает все курсоры, которые были объявлены в пакете, содержащем ошибочную инструкцию. Все курсоры освобождаются в зависимости от их типа или установок параметра CURSOR_CLOSE_ON_COMMIT. Это относится и к курсорам, объявленным в хранимых процедурах, вызываемых ошибочным пакетом. Курсоры, объявленные в пакете перед ошибочным, подчиняются правилам 1 и 2. Ошибка взаимоблокировки является примером ошибки такого типа. Инструкция ROLLBACK в триггере также автоматически формирует этот тип ошибки.  
  
## <a name="locking-behavior"></a>Режим блокировки  
 Значение типа, указывающее инструкцию ROLLBACK TRANSACTION *savepoint_name* снимает все блокировки, полученные после точки сохранения, за исключением укрупненных и блокировок преобразования. Такие блокировки не освобождаются и не переводятся в прежний режим.  
  
## <a name="permissions"></a>Permissions  
 Необходимо быть членом роли **public** .  
  
## <a name="examples"></a>Примеры  
 В следующем примере демонстрируется эффект отката именованной транзакции: После создания таблицы, следующие инструкции запустить именованной транзакции вставки двух строк и откатить транзакцию с именем в переменной @TransactionName. Другой оператор вне именованные транзакции вставляются две строки. Запрос возвращает результаты предыдущих инструкций.   
  
```sql    
USE tempdb;  
GO  
CREATE TABLE ValueTable ([value] int);  
GO  
  
DECLARE @TransactionName varchar(20) = 'Transaction1';  
  
BEGIN TRAN @TransactionName  
       INSERT INTO ValueTable VALUES(1), (2);  
ROLLBACK TRAN @TransactionName;  
  
INSERT INTO ValueTable VALUES(3),(4);  
  
SELECT [value] FROM ValueTable;  
  
DROP TABLE ValueTable;  
```  
[!INCLUDE[ssresult-md](../../includes/ssresult-md.md)]  
```  
value  
-----   
3    
4  
```  
  
  
## <a name="see-also"></a>См. также:  
 [BEGIN DISTRIBUTED TRANSACTION (Transact-SQL)](../../t-sql/language-elements/begin-distributed-transaction-transact-sql.md)   
 [BEGIN TRANSACTION (Transact-SQL)](../../t-sql/language-elements/begin-transaction-transact-sql.md)   
 [COMMIT TRANSACTION (Transact-SQL)](../../t-sql/language-elements/commit-transaction-transact-sql.md)   
 [ФИКСАЦИЯ РАБОЧЕГО &#40; Transact-SQL &#41;](../../t-sql/language-elements/commit-work-transact-sql.md)   
 [ROLLBACK WORK &#40; Transact-SQL &#41;](../../t-sql/language-elements/rollback-work-transact-sql.md)   
 [SAVE TRANSACTION (Transact-SQL)](../../t-sql/language-elements/save-transaction-transact-sql.md)  
  
  
