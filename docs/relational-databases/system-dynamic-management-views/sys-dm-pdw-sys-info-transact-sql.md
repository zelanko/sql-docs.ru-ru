---
title: sys.dm_pdw_sys_info (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/07/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.service: sql-data-warehouse
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 686976b4-2d5d-4d64-bf12-56eba1dc59b1
caps.latest.revision: 7
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 0392e3ad4907192ff06f9e6fcf33f190ae7fdc89
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="sysdmpdwsysinfo-transact-sql"></a>sys.dm_pdw_sys_info (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Предоставляет набор счетчиков уровня устройства, отражающие общую активность на устройстве.  
  
|Имя столбца|Тип данных|Описание|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|total_sessions|**int**|Количество сеансов, в настоящее время в системе.|от 0 до max_active_sessions (см. ниже).|  
|idle_sessions|**int**|Количество сеансов, которые в настоящее время простоя.||  
|active_requests|**int**|Число текущих активных запросов.||  
|queued_requests|**int**|Количество запросов в данный момент в очереди.||  
|active_loads|**int**|Количество нагрузок, выполняющихся в системе.||  
|queued_loads|**int**|Количество нагрузок в очереди, ожидающих выполнения.||  
|active_backups|**int**|Количество текущих резервных копий.||  
|active_restores|**int**|Номер резервного копирования восстанавливает запущен в настоящее время.||  
  
## <a name="see-also"></a>См. также  
 [Хранилище данных SQL и параллельные хранилища данных динамических административных представлений &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
