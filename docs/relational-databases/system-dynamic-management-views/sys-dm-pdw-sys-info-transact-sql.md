---
description: sys.dm_pdw_sys_info (Transact-SQL)
title: sys.dm_pdw_sys_info (Transact-SQL) | Документация Майкрософт
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
ms.openlocfilehash: c98d2ee4dd5dca1b902963976309fbdc005225cc
ms.sourcegitcommit: 22dacedeb6e8721e7cdb6279a946d4002cfb5da3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/14/2020
ms.locfileid: "92035217"
---
# <a name="sysdm_pdw_sys_info-transact-sql"></a>sys.dm_pdw_sys_info (Transact-SQL)
[!INCLUDE[applies-to-version/asa-pdw](../../includes/applies-to-version/asa-pdw.md)]

  Предоставляет набор счетчиков уровня устройства, отражающих общую активность устройства.  
  
|Имя столбца|Тип данных|Description|Диапазон|  
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
 [Динамические административные представления Azure синапсе Analytics и Параллельное хранилище данных &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
