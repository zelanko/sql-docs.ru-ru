---
title: sys.dm_exec_compute_node_status (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
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
caps.latest.revision: 7
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: 8e54bb1e05da7a8575b6b6a9b84abeea7cb9984a
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/06/2018
ms.locfileid: "39540424"
---
# <a name="sysdmexeccomputenodestatus-transact-sql"></a>sys.dm_exec_compute_node_status (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-pdw-md.md)]

  Содержит дополнительные сведения о производительности и состояние всех узлов PolyBase. Содержит одну строку для каждого узла.  
  
|Имя столбца|Тип данных|Описание|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|compute_node_id|**int**|Уникальный числовой идентификатор, связанный с узлом.|Уникальный для горизонтального масштабирования кластера, независимо от типа.|  
|process_id|**int**|||  
|имя_процесса|**nvarchar(255)**|Логическое имя узла.|Любая строка соответствующей длины.|  
|allocated_memory|**bigint**|Общий объем выделенной памяти на данном узле.||  
|available_memory|**bigint**|Общий объем памяти на данном узле.||  
|process_cpu_usage|**bigint**|Всего ЦП процессом, в тактах.||  
|total_cpu_usage|**bigint**|Общее использование ЦП, в тактах.||  
|thread_count|**bigint**|Общее число потоков, используемых на данном узле.||  
|handle_count|**bigint**|Общее число дескрипторов, используемых на данном узле.||  
|total_elapsed_time|**bigint**|Общее время, истекшее с момента системы, запуска или перезапуска.|Общее время, истекшее с момента системы, запуска или перезапуска. Если total_elapsed_time превышает максимальное значение для целого числа (24,8 дня в миллисекундах), он вызывает ошибку материализации из-за переполнения. Максимальное значение в миллисекундах соответствует 24,8 дня.|  
|is_available|**bit**|Флаг, указывающий, доступен ли этот узел.||  
|sent_time|**datetime**|Время последнего пакета сети было отправлено это||  
|received_time|**datetime**|Время последнего пакета сети было отправлено данным узлом.||  
|error_id|**nvarchar(36)**|Уникальный идентификатор последней ошибки, возникшей на данном узле.||  
  
## <a name="see-also"></a>См. также  
 [PolyBase, устранение неполадок с помощью динамических административных представлений](http://msdn.microsoft.com/library/ce9078b7-a750-4f47-b23e-90b83b783d80)   
 [Динамические административные представления и функции (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Динамические административные представления, относящиеся к базе данных &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)  
  
  
