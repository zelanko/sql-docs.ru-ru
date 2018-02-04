---
title: "sys.dm_exec_compute_node_status (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DM_EXEC_COMPUTE_NODE_STATUS_TSQL
- DM_EXEC_COMPUTE_NODE_STATUS
dev_langs:
- TSQL
helpviewer_keywords:
- PolyBase,views
- PolyBase
- dm_exec_compute_node_status
- sys.dm_exec_compute_node_status management view
ms.assetid: b606f91f-3a08-4a4f-bb57-32ae155b3738
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f898f754f0b39b0f5746d8ed076c75d26354bccd
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/03/2018
---
# <a name="sysdmexeccomputenodestatus-transact-sql"></a>sys.dm_exec_compute_node_status (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-pdw-md.md)]

  Содержит дополнительные данные о производительности и состояние всех узлов PolyBase. Содержит одну строку для каждого узла.  
  
|Имя столбца|Тип данных|Описание|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|compute_node_id|**int**|Уникальный числовой идентификатор, связанный с узлом.|Уникален в пределах кластера масштабируемых независимо от типа.|  
|process_id|**int**|||  
|process_name|**nvarchar(255)**|Логическое имя узла.|Любая строка соответствующей длины.|  
|allocated_memory|**bigint**|Общий объем выделенной памяти на данном узле.||  
|available_memory|**bigint**|Общий объем памяти на данном узле.||  
|process_cpu_usage|**bigint**|Общий процесс ЦП, в тактах.||  
|total_cpu_usage|**bigint**|Общее использование ЦП в тактах.||  
|thread_count|**bigint**|Общее количество потоков, используемых на данном узле.||  
|handle_count|**bigint**|Общее число дескрипторов, используемых на данном узле.||  
|total_elapsed_time|**bigint**|Общее время, истекшее с момента системы запуска или перезапуска.|Общее время, истекшее с момента системы запуска или перезапуска. Если total_elapsed_time превышает максимальное значение для целого числа (24.8 дней в миллисекундах), это приведет к переполнению материализации сбой из-за. Максимальное значение в миллисекундах соответствует 24.8 дней.|  
|is_available|**бит**|Флаг, указывающий, доступен ли этот узел.||  
|sent_time|**datetime**|Время последнего пакета сети было отправлено это||  
|received_time|**datetime**|Время последней сетевой пакет был отправлен этот узел.||  
|error_id|**nvarchar(36)**|Уникальный идентификатор последней ошибки, возникшей на данном узле.||  
  
## <a name="see-also"></a>См. также  
 [PolyBase, устранение неполадок с помощью динамических административных представлений](http://msdn.microsoft.com/library/ce9078b7-a750-4f47-b23e-90b83b783d80)   
 [Динамические административные представления и функции (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Динамические административные представления &#40; относящиеся к базе данных Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)  
  
  
