---
title: "PDW_SHOWPARTITIONSTATS DBCC (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 07/17/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.service: sql-data-warehouse
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
caps.latest.revision: 10
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 9d1a4659deeab00589a09e66d885d7f7005f7a43
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="dbcc-pdwshowpartitionstats-transact-sql"></a>PDW_SHOWPARTITIONSTATS DBCC (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw_md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

Отображает размер и число строк для каждой секции таблицы в [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] или [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] базы данных.
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "значок ссылки на раздел") [синтаксические обозначения Transact-SQL &#40; Transact-SQL &#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```sql
Show the partition stats for a table  
DBCC PDW_SHOWPARTITIONSTATS ( " [ database_name . [ schema_name ] . ] | [ schema_name.] table_name  ")  
[;]  
```  
  
## <a name="arguments"></a>Аргументы  
 [ *имя_базы_данных* . [ *schema_name* ]. | *schema_name* . ] *имя_таблицы*  
 Одно-, двух или трех частей имя таблицы для отображения.  Для двух или трех частей таблицы имен, имя необходимо заключать в двойные кавычки (»»). Использование в кавычки имя одной части таблицы является необязательным.  
  
## <a name="permissions"></a>Permissions
Требуется **VIEW SERVER STATE** разрешение.
  
## <a name="result-sets"></a>Результирующие наборы  
Это результаты для команды DBCC PDW_SHOWPARTITIONSTATS.
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|partition_number|int|Номер секции.|  
|used_page_count|bigint|Количество страниц, используемых для данных.|  
|reserved_page_count|bigint|Число страниц, выделенных для секции.|  
|row_count|bigint|Количество строк в секции.|  
|pdw_node_id|int|Вычислительный узел для данных.|  
|distribution_id|int|Идентификатор распределения данных.|  
  
## <a name="examples-includesssdwincludessssdw-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] и[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
### <a name="a-dbcc-pdwshowpartitionstats-basic-syntax-examples"></a>A. Примеры базовый синтаксис инструкции DBCC PDW_SHOWPARTITIONSTATS  
В следующих примерах показаны используемого пространства и количество строк в секции для таблицы FactInternetSales в [!INCLUDE[ssawPDW](../../includes/ssawpdw-md.md)] базы данных.
  
```sql
DBCC PDW_SHOWPARTITIONSTATS ("ssawPDW.dbo.FactInternetSales");  
DBCC PDW_SHOWPARTITIONSTATS ("dbo.FactInternetSales");  
DBCC PDW_SHOWPARTITIONSTATS (FactInternetSales);  
```  
## <a name="see-also"></a>См. также:
[: DBCC PDW_SHOWEXECUTIONPLAN &#40; Transact-SQL &#41;](dbcc-pdw-showexecutionplan-transact-sql.md)  
[DBCC PDW_SHOWSPACEUSED &#40; Transact-SQL &#41;](dbcc-pdw-showspaceused-transact-sql.md)  
  

