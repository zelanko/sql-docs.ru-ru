---
title: DBCC PDW_SHOWPARTITIONSTATS (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 07/17/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.reviewer: ''
ms.service: sql-data-warehouse
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
caps.latest.revision: 10
author: edmacauley
ms.author: umajay
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 40f8af57d1caff81e7738fabfab0788154f90772
ms.sourcegitcommit: d2573a8dec2d4102ce8882ee232cdba080d39628
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/07/2018
---
# <a name="dbcc-pdwshowpartitionstats-transact-sql"></a>DBCC PDW_SHOWPARTITIONSTATS (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

Отображает размер и число строк для каждой секции таблицы в базе данных [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] или [!INCLUDE[ssPDW](../../includes/sspdw-md.md)].
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL (Transact-SQL)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```sql
Show the partition stats for a table  
DBCC PDW_SHOWPARTITIONSTATS ( " [ database_name . [ schema_name ] . ] | [ schema_name.] table_name  ")  
[;]  
```  
  
## <a name="arguments"></a>Аргументы  
 [ *database_name* . [ *schema_name* ] . | *schema_name* . ] *table_name*  
 Имя отображаемой таблицы, состоящее из одной, двух или трех частей.  Если имя таблицы состоит из двух или трех частей, оно должно заключаться в двойные кавычки (""). Заключать однокомпонентное имя таблицы в кавычки необязательно.  
  
## <a name="permissions"></a>Разрешения
Необходимо разрешение **VIEW SERVER STATE**.
  
## <a name="result-sets"></a>Результирующие наборы  
Это результат выполнения команды DBCC PDW_SHOWPARTITIONSTATS.
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|partition_number|ssNoversion|Номер секции.|  
|used_page_count|BIGINT|Число страниц, используемых для данных.|  
|reserved_page_count|BIGINT|Число страниц, выделенных для секции.|  
|row_count|BIGINT|Число строк в секции.|  
|pdw_node_id|ssNoversion|Вычислительный узел для данных.|  
|distribution_id|ssNoversion|Идентификатор распространения для данных.|  
  
## <a name="examples-includesssdwincludessssdw-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] и [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
### <a name="a-dbcc-pdwshowpartitionstats-basic-syntax-examples"></a>A. Примеры базового синтаксиса DBCC PDW_SHOWPARTITIONSTATS  
В приведенных ниже примерах отображается занимаемое пространство и число строк для каждой секции таблицы FactInternetSales в базе данных [!INCLUDE[ssawPDW](../../includes/ssawpdw-md.md)].
  
```sql
DBCC PDW_SHOWPARTITIONSTATS ("ssawPDW.dbo.FactInternetSales");  
DBCC PDW_SHOWPARTITIONSTATS ("dbo.FactInternetSales");  
DBCC PDW_SHOWPARTITIONSTATS (FactInternetSales);  
```  
## <a name="see-also"></a>См. также раздел
[DBCC PDW_SHOWEXECUTIONPLAN (Transact-SQL)](dbcc-pdw-showexecutionplan-transact-sql.md)  
[DBCC PDW_SHOWSPACEUSED (Transact-SQL)](dbcc-pdw-showspaceused-transact-sql.md)  
  
