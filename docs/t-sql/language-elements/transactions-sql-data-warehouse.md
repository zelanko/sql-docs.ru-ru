---
title: "Транзакции (хранилище данных SQL) | Документы Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 87e5e593-a121-4428-9d3c-3af876224e35
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 4ea7244857dcd25b1e36f3420811ef035d4ee3b2
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="transactions-sql-data-warehouse"></a>Транзакции (хранилище данных SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Транзакция — это группа инструкций одной или нескольких баз данных, которые либо полностью фиксируются, либо полностью откатываются. Транзакции атомарны, согласованы, изолированы и устойчивы (atomic, consistent, isolated, durable — ACID). Если транзакция выполнена успешно, все инструкции в ней фиксируются. Если транзакция завершается ошибкой, то если хотя бы одна инструкция в группе завершается ошибкой, выполняется откат всей группы.  
  
 Начало и конец транзакции зависят от параметра AUTOCOMMIT и инструкций BEGIN TRANSACTION, COMMIT и ROLLBACK. [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] поддерживает следующие типы транзакций:  
  
-   *Явные транзакции* начинаются с инструкции BEGIN TRANSACTION и заканчиваются инструкцией COMMIT или ROLLBACK.  
  
-   *Транзакции с автофиксацией* автоматически запускаются в рамках сеанса и не начинаются с инструкции BEGIN TRANSACTION. Если для параметра AUTOCOMMIT установлено значение ON, каждая инструкция выполняется в транзакции, и явные инструкции COMMIT или ROLLBACK не требуются. Если для параметра AUTOCOMMIT установлено значение OFF, для определения результата транзакции требуется инструкция COMMIT или ROLLBACK. В [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] транзакции с автофиксацией начинаются сразу после инструкции COMMIT или ROLLBACK или после инструкции SET AUTOCOMMIT OFF.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL (Transact-SQL)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
BEGIN TRANSACTION [;]  
COMMIT [ TRAN | TRANSACTION | WORK ] [;]  
ROLLBACK [ TRAN | TRANSACTION | WORK ] [;]  
SET AUTOCOMMIT { ON | OFF } [;]  
SET IMPLICIT_TRANSACTIONS { ON | OFF } [;]  
```  
  
## <a name="arguments"></a>Аргументы  
 BEGIN TRANSACTION  
 Отмечает начальную точку явной транзакции.  
  
 COMMIT [ WORK ]  
 Отмечает завершение явной транзакции или транзакции с автофиксацией. Эта инструкция вызывает изменения в транзакции, чтобы всегда быть зафиксированной в базе данных. Инструкция COMMIT идентична инструкциям COMMIT WORK, COMMIT TRAN и COMMIT TRANSACTION.  
  
 ROLLBACK [ WORK ]  
 Выполняет откат транзакции на начало транзакции. Никакие изменения транзакции не фиксируются в базе данных. Инструкция ROLLBACK идентична инструкциям ROLLBACK WORK, ROLLBACK TRAN и ROLLBACK TRANSACTION.  
  
 SET AUTOCOMMIT { **ON** | OFF }  
 Определяет метод запуска и завершения транзакций.  
  
 ON  
 Каждая инструкция выполняется в своей транзакции, явные инструкции COMMIT или ROLLBACK не требуются. Явные транзакции разрешены, когда для параметра AUTOCOMMIT установлено значение ON.  
  
 OFF  
 [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] автоматически запускает транзакцию, если транзакция уже не выполняется. Все последующие инструкции выполняются в рамках транзакции, и инструкции COMMIT или ROLLBACK необходимы для определения результата транзакции. Как только транзакция фиксируется или откатывается в этом режиме, значение OFF сохраняется, а [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] запускает новую транзакцию. Явные транзакции не разрешены, если AUTOCOMMIT имеет значение OFF.  
  
 Если изменить параметр AUTOCOMMIT в активной транзакции, этот параметр не повлияет на текущую транзакцию и вступит в силу только после завершения транзакции.  
  
 Если для параметра AUTOCOMMIT установлено значение ON, выполнение другой инструкции SET AUTOCOMMIT ON не будет иметь результата. Подобным образом, если для параметра AUTOCOMMIT установлено значение OFF, выполнение другой инструкции SET AUTOCOMMIT OFF не будет иметь результата.  
  
 SET IMPLICIT_TRANSACTIONS { ON | **OFF** }  
 Включает те же режимы, что и SET AUTOCOMMIT. Присвоение параметру SET IMPLICIT_TRANSACTIONS значения ON устанавливает для соединения режим неявных транзакций. Значение OFF возвращает подключение в режим автофиксации.  Дополнительные сведения см. в разделе [SET IMPLICIT_TRANSACTIONS (Transact-SQL)](../../t-sql/statements/set-implicit-transactions-transact-sql.md).  
  
## <a name="permissions"></a>Разрешения  
 Для выполнения инструкций, связанных с транзакциями, не нужны конкретные разрешения. Разрешения необходимы для запуска инструкций внутри транзакции.  
  
## <a name="error-handling"></a>Обработка ошибок  
 Если выполнить инструкции COMMIT или ROLLBACK без активной транзакции, возникает ошибка.  
  
 Если выполнить инструкцию BEGIN TRANSACTION во время выполнения транзакции, возникает ошибка. Это может произойти, если инструкция BEGIN TRANSACTION выполняется после успешного запуска инструкции BEGIN TRANSACTION или для сеанса установлено SET AUTOCOMMIT OFF.  
  
 Если ошибка делает невозможным успешное выполнение транзакции, [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] автоматически выполняет ее откат и освобождает ресурсы, удерживаемые транзакцией. Это не относится к ошибкам во время выполнения инструкции. Например, если сетевое подключение клиента к экземпляру компонента [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] разорвано или клиент выходит из приложения, то после того, как экземпляр получит уведомление от сети о разрыве подключения, выполняется откат всех незафиксированных транзакций для этого подключения.  
  
 Если ошибка во время выполнения инструкции возникает в пакетном режиме, [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] ведет себя так, будто для параметра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**XACT_ABORT** установлено значение **ON**, и выполняет откат всей транзакции. Дополнительные сведения о параметре **XACT_ABORT** см. в разделе [SET XACT_ABORT (Transact-SQL)](http://msdn.microsoft.com/library/ms188792.aspx).  
  
## <a name="general-remarks"></a>Общие замечания  
 Сеанс может одновременно выполнять только одну транзакцию. Точки сохранения и вложенные транзакции не поддерживаются.  
  
 Обязанностью программиста на языке [!INCLUDE[DWsql](../../includes/dwsql-md.md)] является вызов инструкции COMMIT только в том случае, когда все данные, относящиеся к транзакции, логически верны.  
  
 Если сеанс закрывается до завершения транзакции, транзакция откатывается.  
  
 Управление режимами транзакций выполняется на уровне сеанса. Например, если один сеанс запускает явную транзакцию или устанавливает для параметра AUTOCOMMIT значение OFF или для параметра IMPLICIT_TRANSACTIONS значение ON, это не влияет на режимы транзакции в других сеансах.  
  
## <a name="limitations-and-restrictions"></a>Ограничения  
 Нельзя произвести откат транзакции после вызова инструкции COMMIT, так как измененные данные уже стали частью базы данных.  
  
 Команды [CREATE DATABASE (Хранилище данных SQL Azure)](../../t-sql/statements/create-database-azure-sql-data-warehouse.md) и [DROP DATABASE (Transact-SQL)](../../t-sql/statements/drop-database-transact-sql.md) не могут использоваться в явной транзакции.  
  
 [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] не поддерживает механизм общего доступа к транзакциям. Это означает, что в любой момент времени только один сеанс может работать с транзакцией в системе.  
  
## <a name="locking-behavior"></a>Режим блокировки  
 [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] использует блокировку для гарантии целостности транзакций и поддержания согласованности баз данных, когда несколько пользователей обращаются к одним и тем же данным в одно и то же время. Блокировка используется в явных и неявных транзакциях. Каждая транзакция запрашивает блокировку разных типов ресурсов, например таблиц или баз данных, от которых эта транзакция зависит. Все блокировки [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] выполняются на уровне таблиц или выше. Блокировка не дает другим транзакциям изменять ресурсы, чтобы избежать ошибок в транзакции, запросившей блокировку. Каждая транзакция снимает свои блокировки, если больше не зависит от заблокированных ресурсов. Явные транзакции сохраняют блокировки до завершения транзакции — ее фиксации или отката.  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="a-using-an-explicit-transaction"></a>A. Использование явной транзакции  
  
```  
BEGIN TRANSACTION;  
DELETE FROM HumanResources.JobCandidate  
    WHERE JobCandidateID = 13;  
COMMIT;  
```  
  
### <a name="b-rolling-back-a-transaction"></a>Б. Откат транзакции  
 В приведенном ниже примере демонстрируется результат отката транзакции.  В этом примере инструкция ROLLBACK приведет к откату инструкции INSERT, но созданная таблица будет по-прежнему существовать.  
  
```  
CREATE TABLE ValueTable (id int);  
BEGIN TRANSACTION;  
       INSERT INTO ValueTable VALUES(1);  
       INSERT INTO ValueTable VALUES(2);  
ROLLBACK;  
```  
  
### <a name="c-setting-autocommit"></a>В. Настройка параметра AUTOCOMMIT  
 В следующем примере для параметра AUTOCOMMIT устанавливается значение `ON`.  
  
```  
SET AUTOCOMMIT ON;  
```  
  
 В следующем примере для параметра AUTOCOMMIT устанавливается значение `OFF`.  
  
```  
SET AUTOCOMMIT OFF;  
```  
  
### <a name="d-using-an-implicit-multi-statement-transaction"></a>Г. Использование неявных транзакций из нескольких инструкций  
  
```  
SET AUTOCOMMIT OFF;  
CREATE TABLE ValueTable (id int);  
INSERT INTO ValueTable VALUES(1);  
INSERT INTO ValueTable VALUES(2);  
COMMIT;  
```  
  
## <a name="see-also"></a>См. также:  
 [SET IMPLICIT_TRANSACTIONS (Transact-SQL)](../../t-sql/statements/set-implicit-transactions-transact-sql.md)   
 [SET TRANSACTION ISOLATION LEVEL (Transact-SQL)](../../t-sql/statements/set-transaction-isolation-level-transact-sql.md)   
 [@@TRANCOUNT &#40;Transact-SQL&#41;](../../t-sql/functions/trancount-transact-sql.md)  
  
  
