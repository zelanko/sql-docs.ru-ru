---
title: sys.dm_exec_background_job_queue_stats (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_exec_background_job_queue_stats
- sys.dm_exec_background_job_queue_stats
- dm_exec_background_job_queue_stats_TSQL
- sys.dm_exec_background_job_queue_stats_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_background_job_queue_stats dynamic management view
ms.assetid: 27f62ab5-46c4-417e-814d-8d6437034d1c
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: fa06da06ae057839a9d0e6433e57edb1f8a603d1
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63013511"
---
# <a name="sysdmexecbackgroundjobqueuestats-transact-sql"></a>sys.dm_exec_background_job_queue_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает строку, в которой предоставляются статистические данные для каждого задания обработчика запросов, передаваемого для асинхронного (фонового) выполнения.  
  
> [!NOTE]  
>  Вызывать его из [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] или [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], используйте имя **sys.dm_pdw_nodes_exec_background_job_queue_stats**.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**queue_max_len**|**int**|Максимальная длина очереди.|  
|**enqueued_count**|**int**|Количество запросов, успешно поставленных в очередь.|  
|**started_count**|**int**|Количество запросов, начавших выполнение.|  
|**ended_count**|**int**|Количество запросов, обслуженных до успешного или неудачного завершения.|  
|**failed_lock_count**|**int**|Количество закончившихся ошибкой запросов из-за состязания блокировок или из-за взаимоблокировки.|  
|**failed_other_count**|**int**|Количество запросов, закончившихся ошибкой по другим причинам.|  
|**failed_giveup_count**|**int**|Количество закончившихся ошибкой запросов из-за достижения предельного значения количества повторных попыток.|  
|**enqueue_failed_full_count**|**int**|Количество неудачных попыток постановки в очередь из-за ее заполненности.|  
|**enqueue_failed_duplicate_count**|**int**|Количество дублированных попыток постановки в очередь.|  
|**elapsed_avg_ms**|**int**|Среднее время с момента начала выполнения запроса (в миллисекундах).|  
|**elapsed_max_ms**|**int**|Время с момента начала выполнения самого длинного запроса (в миллисекундах).|  
|**pdw_node_id**|**int**|**Применяется к**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Идентификатор для узла, это распределение является на.|  
  
## <a name="remarks"></a>Примечания  
 Это представление возвращает сведения только для заданий асинхронного обновления статистики. Дополнительные сведения об асинхронном обновлении статистики см. в разделе [статистики](../../relational-databases/statistics/statistics.md).  
  
## <a name="permissions"></a>Разрешения

На [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], требуется `VIEW SERVER STATE` разрешение.   
На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], требуется `VIEW DATABASE STATE` разрешение в базе данных.   

## <a name="examples"></a>Примеры  
  
### <a name="a-determining-the-percentage-of-failed-background-jobs"></a>A. Определение процента неудачно завершенных фоновых заданий  
 В следующем примере возвращается процент фоновых заданий, завершившихся со сбоем, для всех выполненных запросов.  
  
```  
SELECT   
        CASE ended_count WHEN 0   
                THEN 'No jobs ended'   
                ELSE CAST((failed_lock_count + failed_giveup_count + failed_other_count) / CAST(ended_count AS float) * 100 AS varchar(20))   
        END AS [Percent Failed]  
FROM sys.dm_exec_background_job_queue_stats;  
GO  
```  
  
### <a name="b-determining-the-percentage-of-failed-enqueue-attempts"></a>Б. Определение процента неудачно завершенных попыток постановки в очередь  
 В следующем примере возвращается процент попыток постановки в очередь, завершившихся со сбоем, для всех выполненных запросов.  
  
```  
SELECT   
        CASE enqueued_count WHEN 0   
                THEN 'No jobs posted'   
                ELSE CAST((enqueue_failed_full_count + enqueue_failed_duplicate_count) / CAST(enqueued_count + enqueue_failed_full_count + enqueue_failed_duplicate_count AS float) * 100 AS varchar(20))   
        END AS [Percent Enqueue Failed]  
FROM sys.dm_exec_background_job_queue_stats;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Динамические административные представления и функции (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Динамические административные представления и функции, связанные с выполнением (Transact-SQL)](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)  
  
  


