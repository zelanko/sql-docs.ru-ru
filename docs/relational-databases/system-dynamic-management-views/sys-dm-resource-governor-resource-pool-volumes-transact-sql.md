---
title: sys.dm_resource_governor_resource_pool_volumes (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_resource_governor_resource_pool_volumes_TSQL
- dm_resource_governor_resource_pool_volumes_TSQL
- dm_resource_governor_resource_pool_volumes
- sys.dm_resource_governor_resource_pool_volumes
dev_langs:
- TSQL
helpviewer_keywords:
- dm_resource_governor_resource_pool_volumes
- sys.dm_resource_governor_resource_pool_volumes
ms.assetid: fa692e56-c561-4533-97c5-bc12c600553f
caps.latest.revision: 6
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 49c3cc7312978f313ed55147530c371bdde69675
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "37969226"
---
# <a name="sysdmresourcegovernorresourcepoolvolumes-transact-sql"></a>sys.dm_resource_governor_resource_pool_volumes (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2014-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-xxxx-xxxx-xxx-md.md)]

  Возвращает сведения о текущей статистики ввода-вывода для каждого тома диска пула ресурсов. Эта информация доступна также на уровне пула ресурсов в [sys.dm_resource_governor_resource_pools &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-resource-pools-transact-sql.md).  
  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|pool_id|**int**|Идентификатор пула ресурсов. Не допускает значение NULL.|  
|volume_name|**sysname**|Имя тома диска. Не допускает значение NULL.|  
|read_io_queued_total|**int**|Общая сумма операций ввода-вывода чтения, поставленных в очередь после сброса регулятора ресурсов. Не допускает значение NULL.|  
|read_io_issued_total|**int**|Общая сумма выполненных операций ввода-вывода с момента сброса регулятора ресурсов. Не допускает значение NULL.|  
|read_ios_completed_total|**int**|Общая сумма завершенных операций ввода-вывода с момента сброса регулятора ресурсов. Не допускает значение NULL.|  
|read_ios_throttled_total|**int**|Общая сумма отрегулированных операций чтения с момента сброса регулятора ресурсов. Не допускает значение NULL.|  
|read_bytes_total|**bigint**|Общее число байтов, считанных с момента сброса статистики регулятора ресурсов. Не допускает значение NULL.|  
|read_io_stall_total_ms|**bigint**|Общее время (в миллисекундах) между получением ввода-вывода и завершением. Не допускает значение NULL.|  
|read_io_stall_queued_ms|**bigint**|Общее время (в миллисекундах) между получением ввода-вывода при чтении и проблемой. Это задержка, вызванная регулированием ресурсов ввода-вывода. Не допускает значение NULL.|  
|write_io_queued_total|**int**|Общее количество записей операций ввода-вывода в очереди после сброса статистики регулятора ресурсов. Не допускает значение NULL.|  
|write_io_issued_total|**int**|Общая сумма выполненных операций ввода-вывода записи с момента сброса регулятора ресурсов. Не допускает значение NULL.|  
|write_io_completed_total|**int**|Общая сумма завершенных операций ввода-вывода записи с момента сброса регулятора ресурсов. Не допускает значение NULL.|  
|write_io_throttled_total|**int**|Общая сумма отрегулированных операций записи с момента сброса регулятора ресурсов. Не допускает значение NULL.|  
|write_bytes_total|**bigint**|Общее число байтов, записанных с момента сброса статистики регулятора ресурсов. Не допускает значение NULL.|  
|write_io_stall_total_ms|**bigint**|Общее время (в миллисекундах) между проблемой ввода-вывода при записи и завершением. Не допускает значение NULL.|  
|write_io_stall_queued_ms|**bigint**|Общее время (в миллисекундах) между получением ввода-вывода при записи и проблемой. Это задержка, вызванная регулированием ресурсов ввода-вывода. Не допускает значение NULL.|  
|io_issue_violations_total|**int**|Общее количество проблем с вводом-выводом. Иными словами, количество раз, когда скорость ввода-вывода при проблеме была ниже, чем резервная. Не допускает значение NULL.|  
|io_issue_delay_total_ms|**bigint**|Общее время (в миллисекундах) между запланированной проблемой и фактической проблемой ввода-вывода. Не допускает значение NULL.|  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение VIEW SERVER STATE.  
  
## <a name="see-also"></a>См. также  
 [Динамические административные представления и функции (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [sys.dm_resource_governor_workload_groups (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-workload-groups-transact-sql.md)   
 [sys.resource_governor_resource_pools &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-resource-governor-resource-pools-transact-sql.md)   
 [ALTER RESOURCE GOVERNOR (Transact-SQL)](../../t-sql/statements/alter-resource-governor-transact-sql.md)  
  
  

