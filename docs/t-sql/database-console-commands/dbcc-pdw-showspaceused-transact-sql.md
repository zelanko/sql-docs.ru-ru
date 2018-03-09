---
title: "PDW_SHOWSPACEUSED DBCC (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 07/17/2017
ms.prod: 
ms.prod_service: sql-data-warehouse, pdw
ms.reviewer: 
ms.service: sql-data-warehouse
ms.component: t-sql|database-console-commands
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 73f598cf-b02a-4dba-8d89-9fc0b55a12b8
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8c564a6debb9c110cb41f8fc90a7cc1c0c5a01f7
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="dbcc-pdwshowspaceused-transact-sql"></a>PDW_SHOWSPACEUSED DBCC (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

Отображает количество строк, зарезервированное место на диске и дисковое пространство, используемое для конкретной таблицы или для всех таблиц в [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] или [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] базы данных.
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "значок ссылки на раздел") [синтаксические обозначения Transact-SQL &#40; Transact-SQL &#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```sql
-- Show the space used for all user tables and system tables in the current database  
DBCC PDW_SHOWSPACEUSED  
[;]  
  
-- Show the space used for a table  
DBCC PDW_SHOWSPACEUSED ( " [ database_name . [ schema_name ] . ] | [ schema_name .] table_name  " )  
[;]  
```  
  
## <a name="arguments"></a>Аргументы  
 [ *database_name* . [ *schema_name* ] . | *schema_name* . ] *table_name*  
 Одно-, двух или трех частей имя таблицы для отображения. Для двух или трех частей таблицы имен, имя необходимо заключать в двойные кавычки (»»). Использование в кавычки имя одной части таблицы является необязательным. Если имя таблицы не указан, отображается текст в текущей базе данных.  
  
## <a name="permissions"></a>Разрешения  
Необходимо разрешение VIEW SERVER STATE.
  
## <a name="result-sets"></a>Результирующие наборы  
Это результирующий набор для всех таблиц.
  
|Столбец|Тип данных|Описание|  
|------------|---------------|-----------------|  
|reserved_space|bigint|Общее пространство, используемые в базе данных, в КБ.|  
|data_space|bigint|Пространство, используемое для данных, в КБ.|  
|index_space|bigint|Пространство, используемое для индексов, в КБ.|  
|unused_space|bigint|Пространство, которое является частью зарезервированного пространства и не используется, в КБ.|  
|pdw_node_id|int|Вычислительный узел, который используется для данных.|  
  
Это результирующий набор для одной таблицы.
  
|Столбец|Тип данных|Описание|Диапазон|  
|------------|---------------|-----------------|-----------|  
|rows|bigint|Количество строк.||  
|reserved_space|bigint|Общее пространство, зарезервированное для объекта, в КБ.||  
|data_space|bigint|Пространство, используемое для отображения данных в КБ.||  
|index_space|bigint|Пространство, используемое для индексов, в КБ.||  
|unused_space|bigint|Пространство, которое является частью зарезервированного пространства и не используется, в КБ.||  
|pdw_node_id|int|Вычислительный узел, который используется для создания отчетов для использования пространства.||  
|distribution_id|int|Распределение, которое используется для создания отчетов для использования пространства.|Значение-1 для реплицированных таблиц.|  
  
## <a name="examples-includesssdwincludessssdw-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] и[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
### <a name="a-dbcc-pdwshowspaceused-basic-syntax"></a>A. Базовый синтаксис инструкции DBCC PDW_SHOWSPACEUSED  
В следующих примерах Показать несколько способов отображения количество строк, зарезервированное место на диске и место на диске для этой таблицы FactInternetSales в [!INCLUDE[ssawPDW](../../includes/ssawpdw-md.md)] базы данных.
  
```sql
-- Uses AdventureWorks  
  
DBCC PDW_SHOWSPACEUSED ( "AdventureWorksPDW2012.dbo.FactInternetSales" );  
DBCC PDW_SHOWSPACEUSED ( "AdventureWorksPDW2012..FactInternetSales" );  
DBCC PDW_SHOWSPACEUSED ( "dbo.FactInternetSales" );  
DBCC PDW_SHOWSPACEUSED ( FactInternetSales );  
```  
  
### <a name="b-show-the-disk-space-used-by-all-tables-in-the-current-database"></a>Б. Показать места на диске, используемого всех таблиц в текущей базе данных  
 В следующем примере показано место на диске зарезервировано и используется для всех пользовательских таблиц и системных таблиц в [!INCLUDE[ssawPDW](../../includes/ssawpdw-md.md)] базы данных.  
  
```sql
-- Uses AdventureWorks  
  
DBCC PDW_SHOWSPACEUSED;  
```  
 ## <a name="see-also"></a>См. также:
[: DBCC PDW_SHOWEXECUTIONPLAN &#40; Transact-SQL &#41;](dbcc-pdw-showexecutionplan-transact-sql.md)  
[DBCC PDW_SHOWPARTITIONSTATS &#40; Transact-SQL &#41;](dbcc-pdw-showpartitionstats-transact-sql.md)

  
