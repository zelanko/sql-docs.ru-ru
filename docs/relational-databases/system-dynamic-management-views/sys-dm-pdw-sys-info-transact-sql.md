---
title: sys.dm_pdw_sys_info (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/07/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 686976b4-2d5d-4d64-bf12-56eba1dc59b1
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: ad7311759e2ea38f5b9b375785b7f035d1dcdbfa
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47821522"
---
# <a name="sysdmpdwsysinfo-transact-sql"></a>sys.dm_pdw_sys_info (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Предоставляет набор счетчиков уровня устройства, отражающие действие на устройстве.  
  
|Имя столбца|Тип данных|Описание|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|total_sessions|**int**|Количество сеансов, в настоящее время в системе.|0, чтобы max_active_sessions (см. ниже).|  
|idle_sessions|**int**|Количество сеансов, которые в настоящее время простоя.||  
|active_requests|**int**|Число текущих активных запросов.||  
|queued_requests|**int**|Число запросов в настоящее время в очереди.||  
|active_loads|**int**|Количество нагрузок, выполняющихся в системе.||  
|queued_loads|**int**|Количество нагрузок в очереди, ожидающих выполнения.||  
|active_backups|**int**|Количество текущих резервных копий.||  
|active_restores|**int**|Номер резервного копирования восстанавливает запущена.||  
  
## <a name="see-also"></a>См. также  
 [Хранилище данных SQL и параллельные хранилища данных динамические административные представления &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
