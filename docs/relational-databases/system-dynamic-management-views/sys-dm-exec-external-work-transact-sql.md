---
title: sys.dm_exec_external_work (Transact-SQL) | Документация Майкрософт
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
- DM_EXEC_EXTERNAL_WORK
- DM_EXEC_EXTERNAL_WORK_TSQL
- SYS.DM_EXEC_EXTERNAL_WORK_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_external_work management view
- dm_exec_external_work management view
- PolyBase,views
- PolyBase
ms.assetid: 7597d97b-1fde-4135-ac35-4af12968f300
caps.latest.revision: 8
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: bb8054d49ecbcd3f4140c63e2adf460e4330b9e6
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/06/2018
ms.locfileid: "39538474"
---
# <a name="sysdmexecexternalwork-transact-sql"></a>sys.dm_exec_external_work (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-pdw-md.md)]

  Возвращает сведения о каждой рабочей роли, рабочей нагрузки на каждом вычислительном узле.  
  
 Sys.dm_exec_external_work запроса для определения работы зацикливается для взаимодействия с внешним источником данных (например, Hadoop или внешних SQL Server).  
  
|Имя столбца|Тип данных|Описание|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|execution_id|**nvarchar(32)**|Уникальный идентификатор для связанного запроса PolyBase.|См. в разделе *request_ID* в [sys.dm_exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md).|  
|step_index|**int**|Запрос выполняет этим исполнителем.|См. в разделе *step_index* в [sys.dm_exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md).|  
|dms_step_index|**int**|Шаг в плане DMS, который выполняется этим исполнителем.|См. в разделе [sys.dm_exec_dms_workers &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-dms-workers-transact-sql.md).|  
|compute_node_id|**int**|На узле рабочей роли выполняется.|См. в разделе [sys.dm_exec_compute_nodes &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-compute-nodes-transact-sql.md).|  
|Тип|**nvarchar(60)**|Тип внешней работы.|«Файл разбиение»|  
|work_id|**int**|Идентификатор фактического разбиения.|Больше или равно 0.|  
|input_name|**nvarchar(4000)**|Имя входных данных для чтения|Имя файла, при использовании Hadoop.|  
|read_location|**bigint**|Смещение или чтения расположение.|Смещение файла для чтения.|  
|bytes_processed|**bigint**|Общее число байтов, обработанных этим исполнителем.|Больше или равно 0.|  
|length|**bigint**|Длина разбиения или блока HDFS в случае Hadoop|Определяемые пользователем. Значение по умолчанию — 64 МБ|  
|status|**nvarchar(32)**|Состояние рабочего процесса|Ожидающие обработки, сделать, не удалось, прервана|  
|start_time|**datetime**|Начало работы||  
|end_time|**datetime**|Конец работы||  
|total_elapsed_time|**int**|Общее время в миллисекундах||  
  
## <a name="see-also"></a>См. также  
 [PolyBase, устранение неполадок с помощью динамических административных представлений](http://msdn.microsoft.com/library/ce9078b7-a750-4f47-b23e-90b83b783d80)   
 [Динамические административные представления и функции (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Динамические административные представления, относящиеся к базе данных &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)  
  
  
