---
title: sys. dm_pdw_sys_info (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 686976b4-2d5d-4d64-bf12-56eba1dc59b1
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 0bc6c97f4d41023b822f42a6bbe4c5b193d42e45
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68088763"
---
# <a name="sysdm_pdw_sys_info-transact-sql"></a>sys. dm_pdw_sys_info (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Предоставляет набор счетчиков уровня устройства, отражающих общую активность устройства.  
  
|Имя столбца|Тип данных|Описание|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|total_sessions|**int**|Число сеансов, в настоящее время находящихся в системе.|от 0 до max_active_sessions (см. ниже).|  
|idle_sessions|**int**|Число сеансов в состоянии бездействия.||  
|active_requests|**int**|Число активных запросов, выполняемых в данный момент.||  
|queued_requests|**int**|Количество запросов в очереди.||  
|active_loads|**int**|Количество нагрузок, выполняющихся в системе в данный момент.||  
|queued_loads|**int**|Количество находящихся в очереди загрузок, ожидающих выполнения.||  
|active_backups|**int**|Количество операций резервного копирования, выполняемых в данный момент.||  
|active_restores|**int**|Число восстановлений резервных копий, выполняемых в данный момент.||  
  
## <a name="see-also"></a>См. также:  
 [Динамические административные представления хранилища данных SQL и параллельного хранилища данных &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
