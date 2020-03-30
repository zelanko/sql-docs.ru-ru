---
title: DBCC PDW_SHOWSPACEUSED (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 07/17/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 73f598cf-b02a-4dba-8d89-9fc0b55a12b8
author: pmasl
ms.author: umajay
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: f8c5d7ac822546d8334f1a174684f35733d9571b
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "68116491"
---
# <a name="dbcc-pdw_showspaceused-transact-sql"></a>DBCC PDW_SHOWSPACEUSED (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

Отображает число строк, зарезервированное место на диске и используемое место на диске для определенной таблицы или всех таблиц в базе данных [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] или [!INCLUDE[ssPDW](../../includes/sspdw-md.md)].
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL &#40;Transact-SQL&#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
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
 `[ database_name . [ schema_name ] . | schema_name . ] table_name`  
 Имя отображаемой таблицы, состоящее из одной, двух или трех частей. Если имя таблицы состоит из двух или трех частей, оно должно заключаться в двойные кавычки (""). Заключать однокомпонентное имя таблицы в кавычки необязательно. Если имя таблицы не указано, выводятся сведения для текущей базы данных.  
  
## <a name="permissions"></a>Разрешения  
Необходимо разрешение VIEW SERVER STATE.
  
## <a name="result-sets"></a>Результирующие наборы  
Это результирующий набор для всех таблиц.
  
|Столбец|Тип данных|Description|  
|------------|---------------|-----------------|  
|reserved_space|BIGINT|Общий размер пространства, используемого для базы данных, в КБ.|  
|data_space|BIGINT|Пространство, используемое для данных, в КБ.|  
|index_space|BIGINT|Пространство, используемое для индексов, в КБ.|  
|unused_space|BIGINT|Пространство, которое является частью зарезервированного пространства и не используется, в КБ.|  
|pdw_node_id|INT|Вычислительный узел, который используется для данных.|  
  
Это результирующий набор для одной таблицы.
  
|Столбец|Тип данных|Description|Диапазон|  
|------------|---------------|-----------------|-----------|  
|rows|BIGINT|Число строк.||  
|reserved_space|BIGINT|Общий размер пространства, зарезервированного для объекта, в КБ.||  
|data_space|BIGINT|Пространство, используемое для данных, в КБ.||  
|index_space|BIGINT|Пространство, используемое для индексов, в КБ.||  
|unused_space|BIGINT|Пространство, которое является частью зарезервированного пространства и не используется, в КБ.||  
|pdw_node_id|INT|Вычислительный узел, который применяется для предоставления сведений об использовании пространства.||  
|distribution_id|INT|Распределение, которое применяется для предоставления сведений об использовании пространства.|Для реплицированных таблиц значение равно –1.|  
  
## <a name="examples-sssdw-and-sspdw"></a>Примеры: [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] и [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
### <a name="a-dbcc-pdw_showspaceused-basic-syntax"></a>A. Базовый синтаксис DBCC PDW_SHOWSPACEUSED  
В приведенных ниже примерах показаны различные способы отображения числа строк, зарезервированного и используемого места на диске для таблицы FactInternetSales в базе данных [!INCLUDE[ssawPDW](../../includes/ssawpdw-md.md)].
  
```sql
-- Uses AdventureWorks  
  
DBCC PDW_SHOWSPACEUSED ( "AdventureWorksPDW2012.dbo.FactInternetSales" );  
DBCC PDW_SHOWSPACEUSED ( "AdventureWorksPDW2012..FactInternetSales" );  
DBCC PDW_SHOWSPACEUSED ( "dbo.FactInternetSales" );  
DBCC PDW_SHOWSPACEUSED ( FactInternetSales );  
```  
  
### <a name="b-show-the-disk-space-used-by-all-tables-in-the-current-database"></a>Б. Отображение места на диске, используемого всеми таблицами в текущей базе данных  
 В приведенном ниже примере отображается место на диске, зарезервированное и используемое всеми пользовательскими и системными таблицами в базе данных [!INCLUDE[ssawPDW](../../includes/ssawpdw-md.md)].  
  
```sql
-- Uses AdventureWorks  
  
DBCC PDW_SHOWSPACEUSED;  
```  
 ## <a name="see-also"></a>См. также раздел
[DBCC PDW_SHOWEXECUTIONPLAN (Transact-SQL)](dbcc-pdw-showexecutionplan-transact-sql.md)  
[DBCC PDW_SHOWPARTITIONSTATS (Transact-SQL)](dbcc-pdw-showpartitionstats-transact-sql.md)

  
