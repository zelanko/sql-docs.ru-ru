---
title: sys.dm_db_xtp_hash_index_stats (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 08/29/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_db_xtp_hash_index_stats
- sys.dm_db_xtp_hash_index_stats_TSQL
- dm_db_xtp_hash_index_stats
- dm_db_xtp_hash_index_stats_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_xtp_hash_index_stats (dynamic management view)
ms.assetid: 45969884-cd61-48e8-aee5-c725c78e3e4c
caps.latest.revision: 18
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: fdb15a0c64b11eb0fc57772ccaf37adcc1cc599e
ms.sourcegitcommit: 7019ac41524bdf783ea2c129c17b54581951b515
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2018
ms.locfileid: "34465230"
---
# <a name="sysdmdbxtphashindexstats-transact-sql"></a>sys.dm_db_xtp_hash_index_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2014-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-asdb-xxxx-xxx-md.md)]

  Эти статистические данные могут быть полезными для понимания и настройки числа контейнеров. Их также можно использовать, чтобы определить наличие повторяющихся ключей индекса.  
  
 Большая средняя длина цепочки означает, что множество строк хэшируются в один контейнер. Это могло произойти по следующим причинам.  
  
-   Если количество пустых контейнеров небольшое или средняя и максимальная длина цепочки близки по значению, вероятно, что общее число контейнеров слишком мало. Это приводит к тому, что разные ключи индекса хэшируются в один контейнер.  
  
-   Если пустых контейнеров много или максимальная длина цепочки намного больше средней длины, вероятно, что существует множество строк с повторяющимися значениями ключа индекса или в значениях ключей возникло искажение. Все строки с одним значением ключа индекса хэшируются в один контейнер, следовательно, длина цепочки в этом контейнере высока.  
  
Длинные цепочки могут негативно повлиять на производительность всех операций DML в отдельных строках, в том числе SELECT и INSERT. Короткие цепочки и большое число пустых контейнеров указывают на то, что значение bucket_count слишком велико. Это приводит к снижению производительности просмотра индекса.  
  
> [!WARNING]
> **sys.dm_db_xtp_hash_index_stats** сканирует всю таблицу. Таким образом, при наличии больших таблиц в базе данных, **sys.dm_db_xtp_hash_index_stats** может занять длительное время выполнения.  
  
Дополнительные сведения см. в разделе [хэш-индексы для таблиц, оптимизированных для памяти](../../relational-databases/sql-server-index-design-guide.md#hash_index).  
  
|Имя столбца|Тип|Описание|  
|-----------------|----------|-----------------|  
|object_id|**int**|Идентификатор объекта родительской таблицы.|  
|xtp_object_id|**bigint**|Идентификатор таблицы, оптимизированные для памяти.|  
|index_id|**int**|Идентификатор индекса.|  
|total_bucket_count|**bigint**|Общее число хэш-контейнеров в индексе.|  
|empty_bucket_count|**bigint**|Общее число пустых хэш-контейнеров в индексе.|  
|avg_chain_length|**bigint**|Средняя длина цепочек строк во всех хэш-контейнерах в индексе.|  
|max_chain_length|**bigint**|Максимальная длина цепочек строки в хэш-контейнерах.|  
|xtp_object_id|**bigint**|Идентификатор объекта в памяти OLTP, соответствует таблице, оптимизированной для памяти.|  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение VIEW DATABASE STATE на сервере.  

## <a name="examples"></a>Примеры  
  
### <a name="a-troubleshooting-hash-index-bucket-count"></a>A. Устранение неполадок, связанных с числом контейнеров хэш-индекса

Следующий запрос может использоваться для устранения неполадок число контейнеров хэш-индексе существующей таблицы. Запрос возвращает статистику о процент пустых контейнеров и длина цепочки для всех хэш-индексов для пользовательских таблиц.

```sql
  SELECT  
    QUOTENAME(SCHEMA_NAME(t.schema_id)) + N'.' + QUOTENAME(OBJECT_NAME(h.object_id)) as [table],   
    i.name                   as [index],   
    h.total_bucket_count,  
    h.empty_bucket_count,  
    FLOOR((  
      CAST(h.empty_bucket_count as float) /  
        h.total_bucket_count) * 100)  
                             as [empty_bucket_percent],  
    h.avg_chain_length,   
    h.max_chain_length  
  FROM sys.dm_db_xtp_hash_index_stats as h   
  INNER JOIN sys.indexes as i  
            ON h.object_id = i.object_id  
           AND h.index_id  = i.index_id  
    INNER JOIN sys.memory_optimized_tables_internal_attributes ia ON h.xtp_object_id=ia.xtp_object_id
    INNER JOIN sys.tables t on h.object_id=t.object_id
  WHERE ia.type=1
  ORDER BY [table], [index];  
``` 

Дополнительные сведения о том, как интерпретировать результаты этого запроса см. в разделе [Устранение неполадок хэш-индексы для таблиц, оптимизированных для памяти](../../relational-databases/in-memory-oltp/hash-indexes-for-memory-optimized-tables.md) .  

### <a name="b-hash-index-statistics-for-internal-tables"></a>Б. Статистики хэш-индексов для внутренних таблиц

Некоторые возможности использовать внутренние таблицы, которые используют хэш-индексов, например индексы columnstore таблиц, оптимизированных для памяти. Следующий запрос возвращает статистику для хэш-индексы на внутренние таблицы, связанные с таблицами пользователя.

```sql
  SELECT  
    QUOTENAME(SCHEMA_NAME(t.schema_id)) + N'.' + QUOTENAME(OBJECT_NAME(h.object_id)) as [user_table],
    ia.type_desc as [internal_table_type],
    i.name                   as [index],   
    h.total_bucket_count,  
    h.empty_bucket_count,  
    h.avg_chain_length,   
    h.max_chain_length  
  FROM sys.dm_db_xtp_hash_index_stats as h   
  INNER JOIN sys.indexes as i  
            ON h.object_id = i.object_id  
           AND h.index_id  = i.index_id  
    INNER JOIN sys.memory_optimized_tables_internal_attributes ia ON h.xtp_object_id=ia.xtp_object_id
    INNER JOIN sys.tables t on h.object_id=t.object_id
  WHERE ia.type!=1
  ORDER BY [user_table], [internal_table_type], [index]; 
```

Обратите внимание, что нельзя изменить значение BUCKET_COUNT индекса по внутренним таблицам таким образом выходные данные этого запроса следует учитывать информативные только. Никаких действий не требуется.  

Этот запрос не должны возвращать все строки, если вы не используете функцию, которая использует хэш-индексы по внутренним таблицам. Следующая таблица оптимизированной для памяти содержит индекс columnstore. После создания этой таблицы, вы увидите хэш-индексы по внутренним таблицам.

```sql
  CREATE TABLE dbo.table_columnstore
  (
    c1 INT NOT NULL PRIMARY KEY NONCLUSTERED,
    INDEX ix_columnstore CLUSTERED COLUMNSTORE
  ) WITH (MEMORY_OPTIMIZED=ON)
```

## <a name="see-also"></a>См. также  
 [Оптимизированные для памяти динамические административные представления таблиц &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/memory-optimized-table-dynamic-management-views-transact-sql.md)  
  
  
