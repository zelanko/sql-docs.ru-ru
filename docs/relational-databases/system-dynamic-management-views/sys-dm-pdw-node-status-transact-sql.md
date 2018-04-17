---
title: sys.dm_pdw_node_status (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: pdw
ms.service: ''
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 8e263b65-81d0-49d0-8873-62ef424369d6
caps.latest.revision: 7
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 2ff2f23fcfc6314d06f55bca2b918d954f43514e
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="sysdmpdwnodestatus-transact-sql"></a>sys.dm_pdw_node_status (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Содержит дополнительные сведения (через [sys.dm_pdw_nodes &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-transact-sql.md)) о производительности и состояние всех узлов устройства. Он содержит одну строку для каждого узла в устройстве.  
  
|Имя столбца|Тип данных|Описание|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|pdw_node_id|**int**|Уникальный числовой идентификатор, связанный с узлом.<br /><br /> Ключ для этого представления.|Уникален в пределах устройства, независимо от типа.|  
|process_id|**int**|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]||  
|имя_процесса|**nvarchar(255)**|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]||  
|allocated_memory|**bigint**|Общий объем выделенной памяти на данном узле.||  
|available_memory|**bigint**|Общий объем памяти на данном узле.||  
|process_cpu_usage|**bigint**|Общий процесс ЦП, в тактах.||  
|total_cpu_usage|**bigint**|Общее использование ЦП в тактах.||  
|thread_count|**bigint**|Общее количество потоков, используемых на данном узле.||  
|handle_count|**bigint**|Общее число дескрипторов, используемых на данном узле.||  
|total_elapsed_time|**bigint**|Общее время, истекшее с момента системы запуска или перезапуска.|Общее время, истекшее с момента системы запуска или перезапуска. Если total_elapsed_time превышает максимальное значение для целого числа (24.8 дней в миллисекундах), это приведет к переполнению материализации сбой из-за.<br /><br /> Максимальное значение в миллисекундах соответствует 24.8 дней.|  
|is_available|**бит**|Флаг, указывающий, доступен ли этот узел.||  
|sent_time|**datetime**|Время последней сетевой пакет был отправлен этот узел.||  
|received_time|**datetime**|Время последней сетевой пакет был получен этот узел.||  
|error_id|**nvarchar(36)**|Уникальный идентификатор последней ошибки, возникшей на данном узле.||  
  
## <a name="see-also"></a>См. также  
 [Хранилище данных SQL и параллельные хранилища данных динамических административных представлений &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
