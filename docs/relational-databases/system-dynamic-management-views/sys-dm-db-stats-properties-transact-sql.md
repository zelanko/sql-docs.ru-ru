---
title: sys.dm_db_stats_properties (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 12/18/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_db_stats_properties_TSQL
- sys.dm_db_stats_properties
- dm_db_stats_properties_TSQL
- dm_db_stats_properties
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_stats_properties
ms.assetid: 8a54889d-e263-4881-9fcb-b1db410a9453
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 19a5f2f82fd46b8aa4c3f54b62287f447c8b2c1a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47845142"
---
# <a name="sysdmdbstatsproperties-transact-sql"></a>sys.dm_db_stats_properties (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает статистические свойства указанного объекта базы данных (таблицы или индексированного представления) из текущей базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Для секционированных таблиц см. в разделе аналогичного [sys.dm_db_incremental_stats_properties](../../relational-databases/system-dynamic-management-views/sys-dm-db-incremental-stats-properties-transact-sql.md). 
 
## <a name="syntax"></a>Синтаксис  
  
```  
sys.dm_db_stats_properties (object_id, stats_id)  
```  
  
## <a name="arguments"></a>Аргументы  
 *object_id*  
 Идентификатор объекта текущей базы данных, для которого запрашиваются статистические свойства. *object_id* имеет тип **int**.  
  
 *stats_id*  
 Идентификатор статистики для указанного аргумента *object_id*. Идентификатор статистики может быть получен из динамического административного представления [sys.stats](../../relational-databases/system-catalog-views/sys-stats-transact-sql.md) . *stats_id* имеет тип **int**.  
  
## <a name="table-returned"></a>Возвращаемая таблица  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|object_id|**int**|Идентификатор объекта (таблицы или индексированного представления), для которого возвращаются свойства объекта статистики.|  
|stats_id|**int**|Идентификатор объекта статистики. Является уникальным в пределах таблицы или индексированного представления. Дополнительные сведения см. в статье [sys.stats (Transact-SQL)](../../relational-databases/system-catalog-views/sys-stats-transact-sql.md).|  
|last_updated|**datetime2**|Дата и время последнего обновления объекта статистики. Дополнительные сведения см. в подразделе [Примечания](#Remarks) на этой странице.|  
|rows|**bigint**|Общее число строк в таблице или индексированном представлении при последнем обновлении статистики. Если статистика отфильтрована или соответствует отфильтрованному индексу, количество строк может быть меньше, чем количество строк в таблице.|  
|rows_sampled|**bigint**|Общее количество строк, выбранных для статистических вычислений.|  
|шаги|**int**|Число шагов в гистограмме. Дополнительные сведения см. в статье [DBCC SHOW_STATISTICS &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-show-statistics-transact-sql.md).|  
|unfiltered_rows|**bigint**|Общее количество строк в таблице до применения критерия фильтра (для отфильтрованной статистики). Если статистика не отфильтрована, то unfiltered_rows равно значению, которое возвращается в столбце rows.|  
|modification_counter|**bigint**|Общее количество изменений в начальном столбце статистики (на основе которого строится гистограмма) с момента последнего обновления статистики.<br /><br /> Оптимизированные для памяти таблицы: начиная [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] и в [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] этот столбец содержит: общее количество изменений для таблицы с момента последнего статистические данные о времени были обновлены или перезапуска базы данных.|  
|значение persisted_sample_percent|**float**|Процент материализованной выборки используется для обновлений статистики, где явно не указан процент выборки. Если значение равно нулю, процент материализованной выборки не устанавливается для этой статистики.<br /><br /> **Применимо к:** [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP1 CU4|  
  
## <a name="Remarks"></a> Замечания  
 **sys.dm_db_stats_properties** возвращает пустой набор строк выполняется любое из следующих условий:  
  
-   **object_id** или **stats_id** имеет значение NULL.    
-   Указанный объект не найден или не соответствует таблице или индексированному представлению.    
-   Указанный идентификатор статистики не соответствует имеющейся статистике для указанного идентификатора объекта статистики.    
-   Текущий пользователь не имеет разрешений на просмотр объекта статистики.  
  
 Это поведение позволяет безопасно использовать представление **sys.dm_db_stats_properties** при перекрестном применении к строкам в представлениях, таких как **sys.objects** и **sys.stats**.  
 
Дата обновления статистики хранится в [большом двоичном объекте статистики](../../relational-databases/statistics/statistics.md#DefinitionQOStatistics) вместе с [гистограммой](../../relational-databases/statistics/statistics.md#histogram) и [вектором плотности](../../relational-databases/statistics/statistics.md#density), а не в метаданных. Если нет данных для создания статистических данных, большой двоичный объект статистики не создается, дата недоступна и *last_updated* столбец имеет значение NULL. Это происходит с отфильтрованной статистикой, для которой предикат не возвращает ни одной строки, или с новыми пустыми таблицами.
  
## <a name="permissions"></a>Разрешения  
 Требуется наличие у пользователя разрешения на выбор столбцов статистики либо то, чтобы пользователь был владельцем таблицы или членом предопределенной роли сервера `sysadmin`, предопределенной роли базы данных `db_owner` или предопределенной роли базы данных `db_ddladmin`.  
  
## <a name="examples"></a>Примеры  

### <a name="a-simple-example"></a>A. Простой пример
Следующий пример возвращает статистику для `Person.Person` таблицы в базе данных AdventureWorks.

```sql
SELECT * FROM sys.dm_db_stats_properties (object_id('Person.Person'), 1);
``` 
  
### <a name="b-returning-all-statistics-properties-for-a-table"></a>Б. Получение всех статистических свойств таблицы  
 В следующем примере показано получение всех статистических свойств, имеющихся для таблицы TEST.  
  
```sql  
SELECT sp.stats_id, name, filter_definition, last_updated, rows, rows_sampled, steps, unfiltered_rows, modification_counter   
FROM sys.stats AS stat   
CROSS APPLY sys.dm_db_stats_properties(stat.object_id, stat.stats_id) AS sp  
WHERE stat.object_id = object_id('TEST');  
```  
  
### <a name="c-returning-statistics-properties-for-frequently-modified-objects"></a>В. Получение статистических свойств часто изменяемых объектов.  
 В следующем примере показано получение всех таблиц, индексированных представлений и статистических свойств из текущей базы данных, где начальный столбец менялся более 1000 раз с момента последнего обновления статистики.  
  
```sql  
SELECT obj.name, obj.object_id, stat.name, stat.stats_id, last_updated, modification_counter  
FROM sys.objects AS obj   
INNER JOIN sys.stats AS stat ON stat.object_id = obj.object_id  
CROSS APPLY sys.dm_db_stats_properties(stat.object_id, stat.stats_id) AS sp  
WHERE modification_counter > 1000;  
```  
  
## <a name="see-also"></a>См. также  
 [DBCC SHOW_STATISTICS (Transact-SQL)](../../t-sql/database-console-commands/dbcc-show-statistics-transact-sql.md)   
 [sys.stats &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-stats-transact-sql.md)   
 [Динамические административные представления и функции, связанные с объектом &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/object-related-dynamic-management-views-and-functions-transact-sql.md)   
 [Динамические административные представления и функции (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)  
 [sys.dm_db_incremental_stats_properties (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-db-incremental-stats-properties-transact-sql.md)  
 [sys.dm_db_stats_histogram (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-db-stats-histogram-transact-sql.md) 
  

