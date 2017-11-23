---
title: "sys.dm_db_incremental_stats_properties (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 11/16/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server 2014
f1_keywords:
- sys.dm_db_incremental_stats_properties
- sys.dm_db_incremental_stats_properties_TSQL
- dm_db_incremental_stats_properties
- dm_db_incremental_stats_properties_TSQL
dev_langs: TSQL
helpviewer_keywords: sys.dm_db_incremental_stats_properties
ms.assetid: aa0db893-34d1-419c-b008-224852e71307
caps.latest.revision: "7"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ce7ab395a01f3b1ab6d35edb3c260f1f4338044e
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmdbincrementalstatsproperties-transact-sql"></a>sys.dm_db_incremental_stats_properties (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2014-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-xxxx-xxxx-xxx-md.md)]

  Возвращает свойства добавочной статистики для указанного объекта базы данных (таблицы) из текущей базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Использование `sys.dm_db_incremental_stats_properties` (который содержит номер секции) аналогичен `sys.dm_db_stats_properties` , который используется для недобавочной статистики. 
  
  Эта функция появилась в [!INCLUDE[ssSQL14_md](../../includes/sssql14-md.md)] с пакетом обновления 2 и [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] с пакетом обновления 1.
  
 
## <a name="syntax"></a>Синтаксис  
  
```  
sys.dm_db_incremental_stats_properties (object_id, stats_id)  
```  
  
## <a name="arguments"></a>Аргументы  
 *object_id*  
 Идентификатор объекта текущей базы данных, для которого запрашиваются свойства одной из добавочных статистик. *object_id* имеет тип **int**.  
  
 *stats_id*  
 Идентификатор статистики для указанного аргумента *object_id*. Идентификатор статистики может быть получен из динамического административного представления [sys.stats](../../relational-databases/system-catalog-views/sys-stats-transact-sql.md) . *stats_id* имеет тип **int**.  
  
## <a name="table-returned"></a>Возвращаемая таблица  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|object_id|**int**|Идентификатор объекта (таблицы), для которого возвращаются свойства объекта статистики.|  
|stats_id|**int**|Идентификатор объекта статистики. Уникален в пределах таблицы. Дополнительные сведения см. в статье [sys.stats &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-stats-transact-sql.md).|
|partition_number|**int**|Номер секции, содержащей часть таблицы.|  
|last_updated|**datetime2**|Дата и время последнего обновления объекта статистики.|  
|rows|**bigint**|Общее число строк в таблице при последнем обновлении статистики. Если статистика отфильтрована или соответствует отфильтрованному индексу, количество строк может быть меньше, чем количество строк в таблице.|  
|rows_sampled|**bigint**|Общее количество строк, выбранных для статистических вычислений.|  
|шаги|**int**|Число шагов в гистограмме. Дополнительные сведения см. в статье [DBCC SHOW_STATISTICS &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-show-statistics-transact-sql.md).|  
|unfiltered_rows|**bigint**|Общее количество строк в таблице до применения критерия фильтра (для отфильтрованной статистики). Если статистика не отфильтрована, то unfiltered_rows равно значению, которое возвращается в столбце rows.|  
|modification_counter|**bigint**|Общее количество изменений в начальном столбце статистики (на основе которого строится гистограмма) с момента последнего обновления статистики.<br /><br /> Этот столбец не содержит сведения для таблиц, оптимизированных для памяти.|  
  
## <a name="remarks"></a>Замечания  
 `sys.dm_db_incremental_stats_properties` возвращает пустой набор строк, если выполняется любое из следующих условий:  
  
-   `object_id` или `stats_id` имеет значение NULL.   
-   Указанный объект не найден или не соответствует таблице с добавочной статистикой.  
-   Указанный идентификатор статистики не соответствует имеющейся статистике для указанного идентификатора объекта статистики.  
-   Текущий пользователь не имеет разрешений на просмотр объекта статистики.

 
 Это поведение позволяет безопасно использовать представление `sys.dm_db_incremental_stats_properties` при перекрестном применении к строкам в таких представлениях, как `sys.objects` и `sys.stats`. Этот метод может возвращать для статистики свойства, соответствующие каждой секции. Чтобы просмотреть свойства по всем секциям для объединенной статистики, используйте вместо этого sys.dm_db_stats_properties. 
  
## <a name="permissions"></a>Permissions  
 Требуется наличие у пользователя разрешения на выбор столбцов статистики либо то, чтобы пользователь был владельцем таблицы или членом предопределенной роли сервера `sysadmin`, предопределенной роли базы данных `db_owner` или предопределенной роли базы данных `db_ddladmin`.  
  
## <a name="examples"></a>Примеры  

### <a name="a-simple-example"></a>A. Простой пример
Следующий пример возвращает статистику для таблицы `PartitionTable` , описанной в разделе [Создание секционированных таблиц и индексов](../../relational-databases/partitions/create-partitioned-tables-and-indexes.md).

```
SELECT * FROM sys.dm_db_incremental_stats_properties (object_id('PartitionTable'), 1);
``` 

Дополнительные предложения по использованию см. в разделе  [sys.dm_db_stats_properties](../../relational-databases/system-dynamic-management-views/sys-dm-db-stats-properties-transact-sql.md).
  
  
## <a name="see-also"></a>См. также:  
 [sys.dm_db_stats_properties](../../relational-databases/system-dynamic-management-views/sys-dm-db-stats-properties-transact-sql.md)   
 [DBCC SHOW_STATISTICS (Transact-SQL)](../../t-sql/database-console-commands/dbcc-show-statistics-transact-sql.md)   
 [sys.stats &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-stats-transact-sql.md)   
 [Динамические административные представления и функции, связанные с объектом &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/object-related-dynamic-management-views-and-functions-transact-sql.md)   
 [Динамические административные представления и функции &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)

