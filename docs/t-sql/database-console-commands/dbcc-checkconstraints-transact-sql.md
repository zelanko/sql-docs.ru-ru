---
title: "DBCC CHECKCONSTRAINTS (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 11/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|database-console-commands
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DBCC CHECKCONSTRAINTS
- DBCC_CHECKCONSTRAINTS_TSQL
- CHECKCONSTRAINTS
- CHECKCONSTRAINTS_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- DBCC CHECKCONSTRAINTS statement
- consistency [SQL Server], constraints
- checking constraint consistency
- constraints [SQL Server], consistency checks
- integrity [SQL Server], constraints
ms.assetid: da6c9cee-6687-46e8-b504-738551f9068b
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 2ff75ba3c32d138d9124eba5cfe170cf146d5778
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="dbcc-checkconstraints-transact-sql"></a>DBCC CHECKCONSTRAINTS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Проверяет целостность указанного ограничения или всех ограничений заданной таблицы в текущей базе данных.
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```sql
DBCC CHECKCONSTRAINTS  
[   
    (   
    table_name | table_id | constraint_name | constraint_id   
    )  
]  
    [ WITH   
    [ { ALL_CONSTRAINTS | ALL_ERRORMSGS } ]  
    [ , ] [ NO_INFOMSGS ]   
    ]  
```  
  
## <a name="arguments"></a>Аргументы  
 *table_name* | *table_id* | *constraint_name* | *constraint_id*  
 Проверяемая таблица или ограничение. Когда *table_name* или *table_id* будет указан, проверяются все включенные ограничения на данной таблице. Когда *constraint_name* или *constraint_id* будет указан, проверяется только ограничение. Если не указаны ни идентификатор таблицы, ни идентификатор ограничения, проверяются все включенные ограничения всех таблиц в текущей базе данных.  
 Имя ограничения однозначно определяет таблицу, к которой оно принадлежит. Дополнительные сведения см. в разделе [Database Identifiers](../../relational-databases/databases/database-identifiers.md).  
  
 на  
 Позволяет задавать параметры.  
  
 ALL_CONSTRAINTS  
 Проверяет все включенные и отключенные ограничения таблицы, если указано имя таблицы или отмечены все таблицы. В противном случае проверяет только включенные ограничения. ALL_CONSTRAINTS не работает, если указано имя ограничения.  
  
 ALL_ERRORMSGS  
 Возвращает все строки, которые не соответствуют ограничениям в проверяемой таблице. По умолчанию, это первые 200 строк.  
  
 NO_INFOMSGS  
 Подавляет вывод всех информационных сообщений.  
  
## <a name="remarks"></a>Remarks  
Команда DBCC CHECKCONSTRAINTS создает и выполняет запрос для всех ограничений FOREIGN KEY и CHECK в таблице.
  
Например, запрос внешних ключей имеет такой вид:
  
```sql
SELECT <columns>  
FROM <table_being_checked> LEFT JOIN <referenced_table>  
    ON <table_being_checked.fkey1> = <referenced_table.pkey1>   
    AND <table_being_checked.fkey2> = <referenced_table.pkey2>  
WHERE <table_being_checked.fkey1> IS NOT NULL   
    AND <referenced_table.pkey1> IS NULL  
    AND <table_being_checked.fkey2> IS NOT NULL  
    AND <referenced_table.pkey2> IS NULL  
```  
  
Данные запроса хранятся во временной таблице. После того, как все указанные таблицы или ограничения были проверены, возвращается результирующий набор.
DBCC CHECKCONSTRAINTS проверяет целостность ограничений FOREIGN KEY и CHECK, но не проверяет целостность дисковых структур данных таблицы. Проверки этих структур данных, которые могут выполняться с помощью [инструкции DBCC CHECKDB](../../t-sql/database-console-commands/dbcc-checkdb-transact-sql.md) и [DBCC CHECKTABLE](../../t-sql/database-console-commands/dbcc-checktable-transact-sql.md).
  
**Применяется к**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] через[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
Если *table_name* или *table_id* указан и включена для системы управления версиями, DBCC CHECKCONSTRAINTS также выполняет проверку согласованности темпоральных данных для указанной таблицы. Когда *NO_INFOMSGS* не указан, эта команда возвращает каждое нарушение согласованности в выходных данных в отдельной строке. Формат вывода будет ([pkcol1] [pkcol2]..) = (\<pkcol1_value >, \<pkcol2_value >...) И \<неверные записи временная таблица >.
  
|Проверить|Дополнительные сведения в выходных данных, если не удалось выполнить проверку|  
|-----------|-----------------------------------------------|  
|PeriodEndColumn ≥ PeriodStartColumn (текущая)|[sys_end] = «{0}» и MAX(DATETIME2) = "9999-12-31 23:59:59.99999"|  
|PeriodEndColumn ≥ PeriodStartColumn (текущее, журнал)|[sys_start] = «{0}» и [sys_end] = «{1}»|  
|PeriodStartColumn < current_utc_time (текущая)|[sys_start] = «{0}» и SYSUTCTIME|  
|PeriodEndColumn < current_utc_time (журнал)|[sys_end] = «{0}» и SYSUTCTIME|  
|Оператор OVERLAPS|(sys_start1 sys_end1), (sys_start2 sys_end2) для двух перекрывающихся записей.<br /><br /> При наличии более чем 2 перекрывающихся записей, выходные данные будут иметь несколько строк, каждый из которых показывает пару перекрытий.|  
  
Нет возможности указать constraint_name или constraint_id для выполнения проверок только темпоральной согласованности.
  
## <a name="result-sets"></a>Результирующие наборы  
DBCC CHECKCONSTRAINTS возвращает набор строк со следующими столбцами.
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|Имя таблицы|**varchar**|Имя таблицы.|  
|Constraint Name|**varchar**|Имя нарушенного ограничения.|  
|Where|**varchar**|Значения столбцов, которые идентифицируют строку или строки, которые нарушают ограничение.<br /><br /> Значение этого столбца может быть использовано в предложении WHERE инструкции SELECT, которая запрашивает строки, нарушающие ограничение.|  
  
## <a name="permissions"></a>Разрешения  
Необходимо быть членом предопределенной роли сервера **sysadmin** или предопределенной роли базы данных **db_owner** .
  
## <a name="examples"></a>Примеры  
  
### <a name="a-checking-a-table"></a>A. Проверка таблицы  
Следующий пример проверяет целостность ограничений таблицы `Table1` в базе данных `AdventureWorks`.
  
```sql  
USE AdventureWorks2012;  
GO  
CREATE TABLE Table1 (Col1 int, Col2 char (30));  
GO  
INSERT INTO Table1 VALUES (100, 'Hello');  
GO  
ALTER TABLE Table1 WITH NOCHECK ADD CONSTRAINT chkTab1 CHECK (Col1 > 100);  
GO  
DBCC CHECKCONSTRAINTS(Table1);  
GO  
```  
  
### <a name="b-checking-a-specific-constraint"></a>Б. Проверка конкретного ограничения  
Следующий пример проверяет целостность ограничения `CK_ProductCostHistory_EndDate`.
  
```sql  
USE AdventureWorks2012;  
GO  
DBCC CHECKCONSTRAINTS ('Production.CK_ProductCostHistory_EndDate');  
GO  
```  
  
### <a name="c-checking-all-enabled-and-disabled-constraints-on-all-tables"></a>В. Проверка всех включенных и отключенных ограничений всех таблиц  
 Следующий пример проверяет целостность всех включенных и отключенных ограничений всех таблиц текущей базы данных.  
  
```sql  
DBCC CHECKCONSTRAINTS WITH ALL_CONSTRAINTS;  
GO  
```  
  
## <a name="see-also"></a>См. также  
[DBCC CHECKDB (Transact-SQL)](../../t-sql/database-console-commands/dbcc-checkdb-transact-sql.md)  
[DBCC CHECKTABLE (Transact-SQL)](../../t-sql/database-console-commands/dbcc-checktable-transact-sql.md)  
[DBCC (Transact-SQL)](../../t-sql/database-console-commands/dbcc-transact-sql.md)
  
  
