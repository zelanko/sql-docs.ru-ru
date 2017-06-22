---
title: "Атомарные блоки | Документация Майкрософт"
ms.custom: 
ms.date: 12/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 40e0e749-260c-4cfc-a848-444d30c09d85
caps.latest.revision: 13
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 40d88b09043e3b21326dde6cb85ced071f2b89b5
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="atomic-blocks-in-native-procedures"></a>Атомарные блоки в собственных процедурах
  **BEGIN ATOMIC** — часть стандарта ANSI SQL. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает атомарные блоки на верхнем уровне хранимых процедур, скомпилированных в собственном коде, а также для скомпилированных в собственном коде скалярных пользовательских функций. Дополнительные сведения об этих функциях см. в разделе [Скалярные определяемые пользователем функции для выполняющейся в памяти OLTP](../../relational-databases/in-memory-oltp/scalar-user-defined-functions-for-in-memory-oltp.md).  
  
-   Каждая хранимая процедура, скомпилированная в собственном коде, содержит только один блок инструкций [!INCLUDE[tsql](../../includes/tsql-md.md)] . Это блок ATOMIC.  
  
-   Интерпретированные хранимые процедуры [!INCLUDE[tsql](../../includes/tsql-md.md)] , скомпилированные не в собственном коде, и нерегламентированные пакеты не поддерживают блоки ATOMIC.  
  
 Блоки ATOMIC выполняются (атомарным образом) в рамках транзакции. Либо все инструкции в блоке выполняются успешно, либо весь блок будет подвергнут откату до точки сохранения, созданной в начале блока. Кроме того, параметры сеанса фиксируются для блока ATOMIC. Выполнение того же блока ATOMIC в сеансах с различными параметрами приведет к тому же поведению независимо от параметров текущего сеанса.  
  
## <a name="transactions-and-error-handling"></a>Транзакции и обработка ошибок  
 Если транзакция уже существует в сеансе (поскольку пакет выполнил инструкцию **BEGIN TRANSACTION** и транзакция остается активной), то при запуске блока ATOMIC создается точка сохранения в транзакции. Если блок выходит без исключения, точка сохранения, которая была создана для блока, фиксируется, но транзакция не будет фиксироваться до тех пор, пока не будет зафиксирована транзакция на уровне сеанса. Если блок вызывает исключение, то результаты блока подвергаются откату, но транзакция на уровне сеанса продолжается, если исключение не приводит к ошибке транзакции. Например, конфликт записи приводит к ошибке транзакции, но не к ошибке приведения типов.  
  
 Если отсутствуют активные транзакции в сеансе, то **BEGIN ATOMIC** запускает новую транзакцию. Если вне блока не возникло исключение, то транзакция будет зафиксирована в конце блока. Если блок вызывает исключение (то есть исключение не обрабатывается и не перехватывается внутри блока), то будет произведен откат этой транзакции. Для транзакций, которые охватывают один блок ATOMIC (одна хранимая процедура, скомпилированная в собственном коде), нет необходимости записывать явные инструкции **BEGIN TRANSACTION** и **COMMIT** или **ROLLBACK** .  
  
 Все хранимые процедуры, скомпилированные в собственном коде, поддерживают конструкции **TRY**, **CATCH**и **THROW** для обработки ошибок. Функция**RAISERROR** не поддерживается.  
  
 Следующий пример иллюстрирует работу функции обработки ошибок с блоками ATOMIC и хранимыми процедурами, скомпилированными в собственном коде:  
  
```tsql  
-- sample table  
CREATE TABLE dbo.t1 (  
  c1 int not null primary key nonclustered  
)  
WITH (MEMORY_OPTIMIZED=ON)  
GO  
  
-- sample proc that inserts 2 rows  
CREATE PROCEDURE dbo.usp_t1 @v1 bigint not null, @v2 bigint not null  
WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
AS  
BEGIN ATOMIC  
WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'us_english', DELAYED_DURABILITY = ON)  
  
  INSERT dbo.t1 VALUES (@v1)  
  INSERT dbo.t1 VALUES (@v2)  
  
END  
GO  
  
-- insert two rows  
EXEC dbo.usp_t1 1, 2  
GO  
  
-- verify we have no active transaction  
SELECT @@TRANCOUNT  
GO  
  
-- verify the rows 1 and 2 were committed  
SELECT c1 FROM dbo.t1  
GO  
  
-- execute proc with arithmetic overflow  
EXEC dbo.usp_t1 3, 4444444444444  
GO  
-- expected error message:  
-- Msg 8115, Level 16, State 0, Procedure usp_t1  
-- Arithmetic overflow error converting bigint to data type int.  
  
-- verify we have no active transaction  
SELECT @@TRANCOUNT  
GO  
  
-- verify rows 3 was not committed; usp_t1 has been rolled back  
SELECT c1 FROM dbo.t1  
GO  
  
-- start a new transaction  
BEGIN TRANSACTION  
  -- insert rows 3 and 4  
  EXEC dbo.usp_t1 3, 4  
  
  -- verify there is still an active transaction  
  SELECT @@TRANCOUNT  
  
  -- verify the rows 3 and 4 were inserted  
  SELECT c1 FROM dbo.t1 WITH (SNAPSHOT)   
  ORDER BY c1  
  
  -- catch the arithmetic overflow error  
  BEGIN TRY  
    EXEC dbo.usp_t1 5, 4444444444444  
  END TRY  
  BEGIN CATCH  
    PRINT N'Error occurred: ' + error_message()  
  END CATCH  
  
  -- verify there is still an active transaction  
  SELECT @@TRANCOUNT  
  
  -- verify rows 3 and 4 are still in the table, and row 5 has not been inserted  
  SELECT c1 FROM dbo.t1 WITH (SNAPSHOT)   
  ORDER BY c1  
  
COMMIT  
GO  
  
-- verify we have no active transaction  
SELECT @@TRANCOUNT  
GO  
  
-- verify rows 3 and 4 has been committed  
SELECT c1 FROM dbo.t1  
ORDER BY c1  
GO  
```  
  
 Следующие сообщения об ошибке, относящиеся к таблицам с оптимизацией для памяти, указывают на неудачу транзакции. Если они встречаются в атомарном блок, это приведет к тому, что транзакция будет прервана: 10772, 41301, 41302, 41305, 41325, 41332 и 41333.  
  
## <a name="session-settings"></a>Параметры сеанса  
 Параметры сеанса в блоках ATOMIC фиксируются, если выполнена компиляция хранимой процедуры. Некоторые параметры могут быть заданы с помощью **BEGIN ATOMIC** , тогда как другие параметры всегда фиксируются в одно и то же значение.  
  
 Требуются следующие параметры с **BEGIN ATOMIC**.  
  
|Обязательный параметр|Description|  
|----------------------|-----------------|  
|**TRANSACTION ISOLATION LEVEL**|Поддерживаются значения **SNAPSHOT**, **REPEATABLEREAD**и **SERIALIZABLE**.|  
|**LANGUAGE**|Определяет форматы даты и времени и системных сообщений. Все языки и псевдонимы в [sys.syslanguages &#40; Transact-SQL &#41;](../../relational-databases/system-compatibility-views/sys-syslanguages-transact-sql.md)поддерживаются.|  
  
 Следующие параметры являются необязательными.  
  
|Необязательный параметр|Description|  
|----------------------|-----------------|  
|**DATEFORMAT**|Поддерживаются все форматы даты, отличные от [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Если он указан, параметр **DATEFORMAT** переопределяет формат даты по умолчанию, связанный с объектом **LANGUAGE**.|  
|**DATEFIRST**|Если он указан, параметр **DATEFIRST** переопределяет значение по умолчанию, связанное с **LANGUAGE**.|  
|**DELAYED_DURABILITY**|Поддерживаются значения **OFF** и **ON**.<br /><br /> Фиксации транзакций [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] могут быть полностью устойчивыми (вариант по умолчанию) или отложенно устойчивыми. Дополнительные сведения см. в статье [Управление устойчивостью транзакций](../../relational-databases/logs/control-transaction-durability.md).|  
  
 Следующие параметры SET имеют одно и то же значение по умолчанию для всех блоков ATOMIC во всех хранимых процедурах, скомпилированных в собственном коде.  
  
|Установленный параметр|Системные значения по умолчанию для блоков ATOMIC|  
|----------------|--------------------------------------|  
|ANSI_NULLS|ON|  
|ANSI_PADDING|ON|  
|ANSI_WARNING|ON|  
|ARITHABORT|ON|  
|ARITHIGNORE|OFF|  
|CONCAT_NULL_YIELDS_NULL|ON|  
|IDENTITY_INSERT|OFF|  
|NOCOUNT|ON|  
|NUMERIC_ROUNDABORT|OFF|  
|QUOTED_IDENTIFIER|ON|  
|ROWCOUNT|0|  
|TEXTSIZE|0|  
|XACT_ABORT|OFF<br /><br /> Неперехваченные исключения приводят к откату блока ATOMIC, но не вызывают прерывание транзакции, если ошибка не критична для транзакции.|  
  
## <a name="see-also"></a>См. также:  
 [Скомпилированные в собственном коде хранимые процедуры](../../relational-databases/in-memory-oltp/natively-compiled-stored-procedures.md)  
  
  

