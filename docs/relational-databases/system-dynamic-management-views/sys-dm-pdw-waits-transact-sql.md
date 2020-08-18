---
description: sys. dm_pdw_waits (Transact-SQL)
title: sys. dm_pdw_waits (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 5130e498-1c77-4ae3-a80b-9aae396494e9
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 1214a5e7f4d6d64d739440f0ecebf35d39a81dd8
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88397840"
---
# <a name="sysdm_pdw_waits-transact-sql"></a>sys. dm_pdw_waits (Transact-SQL)
[!INCLUDE[applies-to-version/asa-pdw](../../includes/applies-to-version/asa-pdw.md)]

  Содержит сведения обо всех состояниях ожидания, возникших во время выполнения запроса или запроса, включая блокировки, ожидание очередей передачи и т. д.  
  
|Имя столбца|Тип данных|Description|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|wait_id|**bigint**|Уникальный числовой идентификатор, связанный с состоянием ожидания.<br /><br /> Ключ для этого представления.|Уникальный для всех ожиданий в системе.|  
|session_id|**nvarchar(32)**|Идентификатор сеанса, в котором произошло состояние ожидания.|См. раздел session_id в [sys. dm_pdw_exec_sessions &#40;&#41;Transact-SQL ](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-sessions-transact-sql.md).|  
|type|**nvarchar(255)**|Тип ожидания, который представляет эта запись.|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|  
|object_type|**nvarchar(255)**|Тип объекта, на который влияет ожидание.|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|  
|object_name|**nvarchar (386)**|Имя или идентификатор GUID указанного объекта, на который влияет ожидание.||  
|request_id|**nvarchar(32)**|Идентификатор запроса, для которого произошло состояние ожидания.|См. раздел request_id в [sys. dm_pdw_exec_requests &#40;&#41;Transact-SQL ](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md).|  
|request_time|**datetime**|Время запроса состояния ожидания.||  
|acquire_time|**datetime**|Время, когда был получен блокировка или ресурс.||  
|Состояние|**nvarchar(50)**|Состояние состояния ожидания.|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|  
|priority|**int**|Приоритет ожидающего элемента.|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|  
  
## <a name="see-also"></a>См. также:  
 [Динамические административные представления хранилища данных SQL и параллельного хранилища данных &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)   
 [sys. dm_pdw_wait_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-wait-stats-transact-sql.md)  
  
  
