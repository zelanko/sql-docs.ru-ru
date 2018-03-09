---
title: "Транзакции (хранилище данных SQL) | Документы Microsoft"
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

  Транзакция — это группа инструкций один или несколько баз данных, полностью зафиксирована или полностью выполнен откат. Каждая транзакция атомарные согласованные, изолированные и устойчивые (ACID). Если транзакция выполнена успешно, все инструкции в нем не фиксируются. Если транзакция завершится неудачно, это по крайней мере один из операторов в группе завершается ошибкой, то выполняется откат всей группы.  
  
 Начало и конец транзакции зависит от параметра автоматической ФИКСАЦИИ и инструкции BEGIN TRANSACTION, COMMIT и ROLLBACK. [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]поддерживает следующие типы транзакций:  
  
-   *Явные транзакции* начинается с инструкции BEGIN TRANSACTION и заканчиваются инструкцией COMMIT или ROLLBACK.  
  
-   *Автоматической фиксации транзакций* инициировать автоматически в ходе сеанса и начинается с инструкции BEGIN TRANSACTION. Если параметр автоматической ФИКСАЦИИ имеет значение ON, каждая инструкция выполняется в транзакции, и нет явного COMMIT или ROLLBACK не требуется. При автоматической ФИКСАЦИИ параметр имеет значение OFF, для определения результата транзакции требуется инструкцией COMMIT или ROLLBACK. В [!INCLUDE[ssSDW](../../includes/sssdw-md.md)], автоматическая фиксация транзакций начинается сразу после инструкции COMMIT или ROLLBACK или после инструкции SET автоматической ФИКСАЦИИ OFF.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "значок ссылки на раздел") [синтаксические обозначения Transact-SQL &#40; Transact-SQL &#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
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
  
 ФИКСАЦИЯ [ТРУДОЗАТРАТЫ]  
 Отмечает завершение явной или автоматической фиксации транзакции. Эта инструкция вызывает изменения в транзакцию, чтобы быть зафиксированы в базе данных без возможности восстановления. Инструкция COMMIT идентична COMMIT WORK, инструкция COMMIT TRANSACTION и COMMIT TRAN.  
  
 ROLLBACK [ WORK ]  
 Откат транзакции до начала транзакции. Нет изменений для транзакции не фиксируются в базе данных. Инструкция ROLLBACK идентична ROLLBACK WORK, ROLLBACK TRAN и ROLLBACK TRANSACTION.  
  
 РЕЖИМ АВТОМАТИЧЕСКОЙ ФИКСАЦИИ НАБОР { **ON** | {OFF}  
 Определяет, как запускать и завершать транзакции.  
  
 ON  
 Каждая инструкция выполняется в свою собственную транзакцию и не явные инструкции COMMIT или ROLLBACK не требуется. Если включен режим автоматической ФИКСАЦИИ допускаются явные транзакции.  
  
 OFF  
 [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]автоматически запускает транзакцию, если транзакция уже не выполняется. Все последующие инструкции выполняются в рамках транзакции и COMMIT или ROLLBACK, необходимые для определения результата транзакции. Как только транзакция фиксирует или откатывает назад в этот режим работы, режиме остается установленным в OFF, а [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] запускает новую транзакцию. Явные транзакции не разрешены при автоматической ФИКСАЦИИ имеет значение OFF.  
  
 При изменении параметра режим автоматической ФИКСАЦИИ внутри активной транзакции, параметр влияет на текущую транзакцию и вступает в силу до завершения транзакции.  
  
 Если режим автоматической ФИКСАЦИИ имеет значение ON, выполнение другой инструкции SET автоматической ФИКСАЦИИ ON не оказывает влияния. Аналогично Если режим автоматической ФИКСАЦИИ имеет значение OFF, запущен другой SET автоматической ФИКСАЦИИ OFF не оказывает влияния.  
  
 SET IMPLICIT_TRANSACTIONS {ON | **OFF** }  
 Это сочетание переключает режимы же, как ЗАДАТЬ режим автоматической ФИКСАЦИИ. Присвоение параметру SET IMPLICIT_TRANSACTIONS значения ON устанавливает для соединения режим неявных транзакций. При значении OFF возвращает соединение в режим автоматической фиксации.  Дополнительные сведения см. в разделе [SET IMPLICIT_TRANSACTIONS &#40; Transact-SQL &#41; ](../../t-sql/statements/set-implicit-transactions-transact-sql.md).  
  
## <a name="permissions"></a>Разрешения  
 Нет специальные разрешения необходимы для выполнения инструкций, связанных с транзакциями. Необходимые разрешения для запуска инструкций внутри транзакции.  
  
## <a name="error-handling"></a>Обработка ошибок  
 Если нет активной транзакции выполняются COMMIT или ROLLBACK, возникает ошибка.  
  
 Если BEGIN TRANSACTION запускается транзакция уже во время выполнения, возникает ошибка. Это может произойти, если BEGIN TRANSACTION возникает после успешной инструкции BEGIN TRANSACTION или сеанс находится в разделе SET автоматической ФИКСАЦИИ OFF.  
  
 Если ошибка отличное от ошибки во время выполнения инструкции препятствует успешному явной транзакции, [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] автоматически выполняет откат транзакции и освобождает все ресурсы, удерживаемые транзакцией. Например если сетевое подключение клиента к экземпляру [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] повреждена или клиент выйдет из приложения, являются откат всех незафиксированных транзакций для соединения при сети уведомляет экземпляр разрыва.  
  
 При возникновении ошибки во время выполнения инструкции в пакете, [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] поведение согласуется с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **XACT_ABORT** значение **ON** и выполняет откат всей транзакции. Дополнительные сведения о **XACT_ABORT** , просмотреть [SET XACT_ABORT (Transact-SQL)](http://msdn.microsoft.com/library/ms188792.aspx).  
  
## <a name="general-remarks"></a>Общие замечания  
 В данный момент; в сеансе может выполняться только одна транзакция точки сохранения и вложенные транзакции не поддерживаются.  
  
 Он отвечает [!INCLUDE[DWsql](../../includes/dwsql-md.md)] программист должен выдавать ФИКСАЦИИ только в том случае, если все данные, относящиеся к транзакции, логически верны.  
  
 Если сеанс закрывается до завершения транзакции, транзакция откатывается.  
  
 Управление режимами транзакций выполняется на уровне сеанса. Например если один сеанс начинает явную транзакцию или задает режим автоматической ФИКСАЦИИ OFF или устанавливает свойство IMPLICIT_TRANSACTIONS — в значение ON, она имеет не влияет на режимы транзакций других сеансов.  
  
## <a name="limitations-and-restrictions"></a>Ограничения  
 Вы не может отменить транзакцию после выдачи инструкции COMMIT, так как данные были произведены изменения постоянной частью базы данных.  
  
 [Создание базы данных &#40; Хранилище данных Azure SQL &#41; ](../../t-sql/statements/create-database-azure-sql-data-warehouse.md) и [удалить базы данных &#40; Transact-SQL &#41; ](../../t-sql/statements/drop-database-transact-sql.md) команды не может использоваться внутри явной транзакции.  
  
 [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]не поддерживает транзакции, механизма для управления доступом. Это означает, что в любой момент времени только один сеанс может выполнять работу в любой транзакции в системе.  
  
## <a name="locking-behavior"></a>Режим блокировки  
 [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]использует блокировки для обеспечения целостности транзакций и поддержания согласованности баз данных, когда несколько пользователей имеют доступ к данным, в то же время. Блокировка используется в явных и неявных транзакциях. Каждая транзакция запрашивает блокировку разных типов ресурсов, например таблиц или баз данных, от которых зависит данная транзакция. Все [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] блокировки, таблицы или более высокого уровня. Блокировка не дает другим транзакциям изменять ресурсы, чтобы избежать ошибок в транзакции, запросившей блокировку. Каждая транзакция освобождает свои блокировки, если больше не имеет зависимость от блокируемого ресурса; явные транзакции сохраняют блокировки до завершения транзакции, при ее фиксации или отката.  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="a-using-an-explicit-transaction"></a>A. С помощью явной транзакции  
  
```  
BEGIN TRANSACTION;  
DELETE FROM HumanResources.JobCandidate  
    WHERE JobCandidateID = 13;  
COMMIT;  
```  
  
### <a name="b-rolling-back-a-transaction"></a>Б. Откат транзакции  
 В следующем примере показано влияние откат транзакции.  В этом примере инструкция ROLLBACK приведет к откату инструкции INSERT, но будет по-прежнему существовать созданную таблицу.  
  
```  
CREATE TABLE ValueTable (id int);  
BEGIN TRANSACTION;  
       INSERT INTO ValueTable VALUES(1);  
       INSERT INTO ValueTable VALUES(2);  
ROLLBACK;  
```  
  
### <a name="c-setting-autocommit"></a>В. Параметр автоматической ФИКСАЦИИ  
 В следующем примере задается параметр автоматической ФИКСАЦИИ `ON`.  
  
```  
SET AUTOCOMMIT ON;  
```  
  
 В следующем примере задается параметр автоматической ФИКСАЦИИ `OFF`.  
  
```  
SET AUTOCOMMIT OFF;  
```  
  
### <a name="d-using-an-implicit-multi-statement-transaction"></a>Г. С помощью неявные транзакции из нескольких инструкций  
  
```  
SET AUTOCOMMIT OFF;  
CREATE TABLE ValueTable (id int);  
INSERT INTO ValueTable VALUES(1);  
INSERT INTO ValueTable VALUES(2);  
COMMIT;  
```  
  
## <a name="see-also"></a>См. также  
 [SET IMPLICIT_TRANSACTIONS &#40; Transact-SQL &#41;](../../t-sql/statements/set-implicit-transactions-transact-sql.md)   
 [SET TRANSACTION ISOLATION LEVEL &#40; Transact-SQL &#41;](../../t-sql/statements/set-transaction-isolation-level-transact-sql.md)   
 [@@TRANCOUNT &#40;Transact-SQL&#41;](../../t-sql/functions/trancount-transact-sql.md)  
  
  
