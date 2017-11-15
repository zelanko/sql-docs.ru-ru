---
title: "Мониторинг оптимизированных для памяти темпоральных таблиц с системным управлением версиями | Документация Майкрософт"
ms.custom: SQL2016_New_Updated
ms.date: 03/28/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: dbe-tables
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7a06785d-dbcb-44de-b95c-26b131471bee
caps.latest.revision: "11"
author: CarlRabeler
ms.author: carlrab
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 0469d41e4bab668d3f5d83d67489f79c0a0bad91
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="monitoring-memory-optimized-system-versioned-temporal-tables"></a>Мониторинг оптимизированных для памяти темпоральных таблиц с системным управлением версиями
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Существующие представления можно использовать для отслеживания подробных и сводных данных о потреблении памяти для каждой оптимизированной для памяти таблицы с системным управлением версиями.  
  
 Подробные сведения о потреблении памяти (разделение между основной таблицей с системным управлением версиями и внутренней промежуточной таблицей):  
  
```  
--Details of memory consumption   
WITH InMemoryTemporalTables   
AS   
(   
   SELECT SCHEMA_NAME ( T1.schema_id ) AS TemporalTableSchema  
      , T1.object_id AS TemporalTableObjectId  
      , IT.object_id AS InternalTableObjectId  
      , OBJECT_NAME ( IT.parent_object_id ) AS TemporalTableName  
      , IT.Name AS InternalHistoryStagingName   
   FROM sys.internal_tables IT    
   JOIN sys.tables T1 ON IT.parent_object_id = T1.object_id   
   WHERE T1.is_memory_optimized  = 1 AND T1.temporal_type = 2    
)   
  
SELECT   
     TemporalTableSchema  
   , T.TemporalTableName  
   , T.InternalHistoryStagingName,    
     CASE   
        WHEN C.object_id = T.TemporalTableObjectId   
        THEN 'Temporal Table Consumption'   
         ELSE 'Internal Table Consumption'   
         END ConsumedBy  
     , C.*   
   FROM sys.dm_db_xtp_memory_consumers C   
   JOIN InMemoryTemporalTables T   
      ON C.object_id = T.TemporalTableObjectId OR C.object_id = T.InternalTableObjectId   
   WHERE T.TemporalTableSchema = 'dbo' AND  T.TemporalTableName = 'FXCurrencyPairs' ;  
  
```  
  
 Сводка по потреблению памяти (итог для оптимизированной для памяти таблицы с системным управлением версиями).  
  
```  
--Summary of memory consumption   
WITH InMemoryTemporalTables   
AS   
(   
   SELECT SCHEMA_NAME ( T1.schema_id ) AS TemporalTableSchema  
     , T1.object_id AS TemporalTableObjectId  
     , IT.object_id AS InternalTableObjectId  
     , OBJECT_NAME ( IT.parent_object_id ) AS TemporalTableName  
     , IT.Name AS InternalHistoryStagingName   
   FROM sys.internal_tables IT    
   JOIN sys.tables T1 ON IT.parent_object_id = T1.object_id   
   WHERE T1.is_memory_optimized  = 1 AND T1.temporal_type = 2    
)   
, DetailedConsumption   
AS   
(   
   SELECT TemporalTableSchema  
      , T.TemporalTableName  
      , T.InternalHistoryStagingName  
      , CASE   
           WHEN C.object_id = T.TemporalTableObjectId   
           THEN 'Temporal Table Consumption'   
           ELSE 'Internal Table Consumption'   
           END ConsumedBy  
      , C.*   
    FROM sys.dm_db_xtp_memory_consumers C   
   JOIN InMemoryTemporalTables T   
      ON C.object_id = T.TemporalTableObjectId OR C.object_id = T.InternalTableObjectId   
)   
  
SELECT TemporalTableSchema  
     TemporalTableName  
   , sum ( allocated_bytes ) AS allocated_bytes  
   , sum ( used_bytes ) AS used_bytes   
FROM DetailedConsumption   
WHERE TemporalTableSchema = 'dbo' AND  TemporalTableName = 'FXCurrencyPairs'   
GROUP BY TemporalTableSchema, TemporalTableName ;  
  
```  
  
## <a name="did-this-article-help-you-were-listening"></a>Эта статья помогла вам? Мы слушаем  
 Какие сведения вы искали и удалось ли вам их найти? Мы прислушиваемся к вашим отзывам для совершенствования материалов. Отправляйте свои комментарии по адресу [sqlfeedback@microsoft.com](mailto:sqlfeedback@microsoft.com?subject=Your%20feedback%20about%20the%20Monitoring%20Memory-Optimized%20System-Versioned%20Temporal%20Tables%20page)  
  
## <a name="see-also"></a>См. также:  
 [Темпоральные таблицы с системным управлением версиями и таблицы, оптимизированные для памяти](../../relational-databases/tables/system-versioned-temporal-tables-with-memory-optimized-tables.md)   
 [Создание оптимизированной для памяти темпоральной таблицы с системным управлением версиями](../../relational-databases/tables/creating-a-memory-optimized-system-versioned-temporal-table.md)   
 [Работа с оптимизированными для памяти темпоральными таблицами с системным управлением версиями](../../relational-databases/tables/working-with-memory-optimized-system-versioned-temporal-tables.md)   
 [Вопросы производительности темпоральных таблиц с системным управлением версиями, оптимизированных для памяти](../../relational-databases/tables/memory-optimized-system-versioned-temporal-tables-performance.md)   
 [Темпоральные таблицы](../../relational-databases/tables/temporal-tables.md)   
 [Проверка согласованности системной темпоральной таблицы](../../relational-databases/tables/temporal-table-system-consistency-checks.md)   
 [Управление хранением данных журнала в темпоральных таблицах с системным управлением версиями](../../relational-databases/tables/manage-retention-of-historical-data-in-system-versioned-temporal-tables.md)   
 [Представления и функции метаданных для временной таблицы](../../relational-databases/tables/temporal-table-metadata-views-and-functions.md)  
  
  
