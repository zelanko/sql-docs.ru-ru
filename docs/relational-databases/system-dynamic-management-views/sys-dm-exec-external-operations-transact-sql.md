---
title: sys.dm_exec_external_operations (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.service: ''
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- DM_EXEC_EXTERNAL_OPERATIONS_TSQL
- DM_EXEC_EXTERNAL_OPERATIONS
- SYS.DM_EXEC_EXTERNAL_OPERATIONS_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- PolyBase,views
- PolyBase
- sys.dm_exec_external_operations management view
- dm_exec_external_operations management view
ms.assetid: d268217a-85b8-4b7f-9cd1-87865eba2be1
caps.latest.revision: 8
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 34c2793e964cf48bb497af6700a805a0d479e43f
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sysdmexecexternaloperations-transact-sql"></a>sys.dm_exec_external_operations (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-pdw-md.md)]

  Сбор сведений о внешних операциях PolyBase.  
  
|Имя столбца|Тип данных|Описание|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|execution_id|**nvarchar(32)**|Уникальный идентификатор запроса связанных с запросом PolyBase|КОД в разделе [sys.dm_exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)|  
|step_index|**int**|Индекс действия запроса|В разделе step_index в [sys.dm_exec_distributed_request_steps &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-distributed-request-steps-transact-sql.md)|  
|Тип ошибка_|**nvarchar(128)**|Описывает операцию Hadoop или другие внешние операции|«Операция внешних Hadoop»|  
|Имя ошибка_|**nvarchar(4000)**|Указывает, как состояние задания в процентах (занятого потребляет входных данных)|0-1 – умножается на коэффициент 100 («завершено»)|  
|Ход выполнения map_|**float**|Указывает, как состояние reduce задания в процентах, при наличии|0-1 – умножается на коэффициент 100 («завершено»)|  
  
## <a name="see-also"></a>См. также  
 [PolyBase, устранение неполадок с помощью динамических административных представлений](http://msdn.microsoft.com/library/ce9078b7-a750-4f47-b23e-90b83b783d80)   
 [Динамические административные представления и функции (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Динамические административные представления, относящиеся к базе данных &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)  
  
  
