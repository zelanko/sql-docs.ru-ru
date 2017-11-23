---
title: "sys.memory_optimized_tables_internal_attributes (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.memory_optimized_tables_internal_attributes
- sys.memory_optimized_tables_internal_attributes_TSQL
- memory_optimized_tables_internal_attributes
- memory_optimized_tables_internal_attributes_TSQL
dev_langs: TSQL
helpviewer_keywords: sys.memory_optimized_tables_internal_attributes catalog view
ms.assetid: 78ef5807-0504-4de8-9a01-ede6c03c7ff1
caps.latest.revision: "13"
author: jodebrui
ms.author: jodebrui
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 3ab05ef27e9687be506db960e628868cb08184d3
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="sysmemoryoptimizedtablesinternalattributes-transact-sql"></a>sys.memory_optimized_tables_internal_attributes (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

Содержит строку для каждой внутренней оптимизированной для памяти таблицы, которая используются для хранения пользовательских таблиц, оптимизированных для памяти. Каждая пользовательская таблица соответствует одной или нескольким внутренним таблицам. Одна таблица используется для хранения основных данных. Дополнительные внутренние таблицы используются для поддержки таких функций, как темпоральные таблицы, индекс columnstore и хранилище (LOB) "вне строки" для таблиц, оптимизированных для памяти.
 
| Имя столбца  | Тип данных  | Description |
| :------ |:----------| :-----|
|object_id  |**int**|       Идентификатор пользовательской таблицы. Внутренние оптимизированные для памяти таблицы, служащие для поддержки пользовательской таблицы (например, хранилища вне строки или удаленных строк в случае сочетания Hk/Columnstore), имеют то же значение object_id, что и их родительский объект. |
|xtp_object_id  |**bigint**|    Идентификатор объекта выполняющейся в памяти OLTP, который соответствует внутренней оптимизированной для памяти таблице, используемой для поддержки пользовательской таблицы. Он уникален в пределах базы данных и может изменяться за время существования объекта. 
|Тип|  **int** |   Тип внутренней таблицы.<br/><br/> 0 => DELETED_ROWS_TABLE <br/> 1 => USER_TABLE <br/> 2 => DICTIONARIES_TABLE<br/>3 => SEGMENTS_TABLE<br/>4 => ROW_GROUPS_INFO_TABLE<br/>5 => INTERNAL OFF-ROW DATA TABLE<br/>252 => INTERNAL_TEMPORAL_HISTORY_TABLE | 
|type_desc| **nvarchar(60)**|   Описание типа<br/><br/>DELETED_ROWS_TABLE — внутренняя таблица, отслеживающая удаленные строки для индекса columnstore<br/>USER_TABLE — таблица, содержащая данные пользователя в строке<br/>DICTIONARIES_TABLE — словари для индекса columnstore<br/>SEGMENTS_TABLE — сжатые сегменты для индекса columnstore<br/>ROW_GROUPS_INFO_TABLE — метаданные для групп сжатых строк индекса columnstore<br/>INTERNAL OFF-ROW DATA TABLE — внутренняя таблица, используемая для хранения столбца вне строки. В данном случае minor_id отражает столбец column_id.<br/>INTERNAL_TEMPORAL_HISTORY_TABLE — оперативный заключительный фрагмент таблицы журнала на диске. Вставляемые в журнал строки сначала вставляются во внутреннюю таблицу, оптимизированную для памяти. Существует фоновая задача, которая асинхронно перемещает строки из этой внутренней таблицы в таблицу журнала на диске. |
|minor_id|  **int**|    Значение 0 указывает на пользователя или внутреннюю таблицу<br/><br/>Ненулевое значение обозначает идентификатор столбца, хранящегося вне строки. Соединяется с column_id в sys.columns.<br/><br/>Каждый столбец, хранящийся вне строки, имеет соответствующую строку в этом системном представлении.|

## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-returning-all-columns-that-are-stored-off-row"></a>A. Возвращение всех столбцов, которые хранятся вне строки

В следующем скрипте T-SQL показана таблица с несколькими большими столбцами, не относящимися к типу LOB, и одним столбцом LOB:

```Transact-SQL
CREATE TABLE dbo.LargeTableSample
(
      Id   int IDENTITY PRIMARY KEY NONCLUSTERED,
      C1   nvarchar(4000),
      C2   nvarchar(4000),
      C3   nvarchar(4000),
      C4   nvarchar(4000),
      Misc nvarchar(max)
) WITH (MEMORY_OPTIMIZED = ON);
GO
```

В следующем запросе показаны все столбцы, которые хранятся вне строки, а также их размер. Размер-1 обозначает столбец LOB. Все столбцы LOB хранятся вне строки.

```Transact-SQL
SELECT 
  QUOTENAME(SCHEMA_NAME(o.schema_id)) + N'.' + QUOTENAME(OBJECT_NAME(moa.object_id)) AS 'table', 
  c.name AS 'column', 
  c.max_length
FROM sys.memory_optimized_tables_internal_attributes moa
     JOIN sys.columns c ON moa.object_id = c.object_id AND moa.minor_id=c.column_id
     JOIN sys.objects o on moa.object_id=o.object_id 
WHERE moa.type=5;
```

### <a name="b-returning-memory-consumption-of-all-columns-that-are-stored-off-row"></a>Б. Возвращение сведений о потреблении памяти для всех столбцов, которые хранятся вне строки

Чтобы получить дополнительные сведения о потреблении памяти для столбцов, хранящихся вне строки, можно использовать следующий запрос, который показывает потребление памяти для всех внутренних таблиц и их индексов, используемых для хранения столбцов вне строки:

```Transact-SQL
SELECT
  QUOTENAME(SCHEMA_NAME(o.schema_id)) + N'.' + QUOTENAME(OBJECT_NAME(moa.object_id)) AS 'table',
  c.name AS 'column',
  c.max_length,
  mc.memory_consumer_desc,
  mc.index_id,
  mc.allocated_bytes,
  mc.used_bytes
FROM sys.memory_optimized_tables_internal_attributes moa
   JOIN sys.columns c ON moa.object_id = c.object_id AND moa.minor_id=c.column_id
   JOIN sys.dm_db_xtp_memory_consumers mc ON moa.xtp_object_id=mc.xtp_object_id
   JOIN sys.objects o on moa.object_id=o.object_id 
WHERE moa.type=5;
```

### <a name="c-returning-memory-consumption-of-columnstore-indexes-on-memory-optimized-tables"></a>В. Возвращение сведений о потреблении памяти для индексов columnstore в таблицах, оптимизированных для памяти

Чтобы показать потребление памяти индексов columnstore для таблиц, оптимизированных для памяти, используйте следующий запрос:

```Transact-SQL
SELECT
  QUOTENAME(SCHEMA_NAME(o.schema_id)) + N'.' + QUOTENAME(OBJECT_NAME(moa.object_id)) AS 'table',
  i.name AS 'columnstore index',
  SUM(mc.allocated_bytes) / 1024 as [allocated_kb],
  SUM(mc.used_bytes) / 1024 as [used_kb]
FROM sys.memory_optimized_tables_internal_attributes moa
   JOIN sys.indexes i ON moa.object_id = i.object_id AND i.type in (5,6)
   JOIN sys.dm_db_xtp_memory_consumers mc ON moa.xtp_object_id=mc.xtp_object_id
   JOIN sys.objects o on moa.object_id=o.object_id
WHERE moa.type IN (0, 2, 3, 4)
GROUP BY o.schema_id, moa.object_id, i.name;
```

Используйте следующий запрос декомпозиции потребление памяти для внутренних структур, используемых для индексов columnstore в таблицах, оптимизированных для памяти:

```Transact-SQL
SELECT
  QUOTENAME(SCHEMA_NAME(o.schema_id)) + N'.' + QUOTENAME(OBJECT_NAME(moa.object_id)) AS 'table',
  i.name AS 'columnstore index',
  moa.type_desc AS 'internal table',
  mc.index_id AS 'index',
  mc.memory_consumer_desc,
  mc.allocated_bytes / 1024 as [allocated_kb],
  mc.used_bytes / 1024 as [used_kb]
FROM sys.memory_optimized_tables_internal_attributes moa
   JOIN sys.indexes i ON moa.object_id = i.object_id AND i.type in (5,6)
   JOIN sys.dm_db_xtp_memory_consumers mc ON moa.xtp_object_id=mc.xtp_object_id
   JOIN sys.objects o on moa.object_id=o.object_id
WHERE moa.type IN (0, 2, 3, 4)
```


