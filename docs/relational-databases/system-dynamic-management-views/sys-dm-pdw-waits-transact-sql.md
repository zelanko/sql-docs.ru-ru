---
title: sys.dm_pdw_waits (Transact-SQL) | Документация Майкрософт
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
ms.openlocfilehash: 476b2f251bd41480962eb9925af6e3619507e791
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68088750"
---
# <a name="sysdmpdwwaits-transact-sql"></a>sys.dm_pdw_waits (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Содержит сведения обо всех ожидания состояний во время выполнения запроса или запроса, включая блокировки, ожидает в очереди передачи и т. д.  
  
|Имя столбца|Тип данных|Описание|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|wait_id|**bigint**|Уникальный числовой идентификатор, связанный с состояния ожидания.<br /><br /> Ключ для этого представления.|Уникальными среди всех ожиданий в системе.|  
|session_id|**nvarchar(32)**|Идентификатор сеанса, в котором произошло состояния ожидания.|См. в разделе session_id в [sys.dm_pdw_exec_sessions &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-sessions-transact-sql.md).|  
|type|**nvarchar(255)**|Тип ожидания, которые представляет эта запись.|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|  
|object_type|**nvarchar(255)**|Тип объекта, который зависит от ожидания.|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|  
|object_name|**nvarchar(386)**|Имя или идентификатор GUID для указанного объекта, который был подвергнут ожидания.||  
|request_id|**nvarchar(32)**|Идентификатор запроса, в котором произошло состояния ожидания.|См. в разделе request_id в [sys.dm_pdw_exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md).|  
|request_time|**datetime**|Время, с которого была запрошена состояния ожидания.||  
|acquire_time|**datetime**|Время, с которого была получена блокировка или ресурса.||  
|state|**nvarchar(50)**|Состояние из состояния ожидания.|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|  
|priority|**int**|Приоритет элемента ожидания.|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|  
  
## <a name="see-also"></a>См. также  
 [Хранилище данных SQL и параллельные хранилища данных динамические административные представления &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)   
 [sys.dm_pdw_wait_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-wait-stats-transact-sql.md)  
  
  
