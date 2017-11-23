---
title: "sys.dm_exec_external_work (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DM_EXEC_EXTERNAL_WORK
- DM_EXEC_EXTERNAL_WORK_TSQL
- SYS.DM_EXEC_EXTERNAL_WORK_TSQL
dev_langs: TSQL
helpviewer_keywords:
- sys.dm_exec_external_work management view
- dm_exec_external_work management view
- PolyBase,views
- PolyBase
ms.assetid: 7597d97b-1fde-4135-ac35-4af12968f300
caps.latest.revision: "8"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b3287e4ae13d7ea06ab00197067ba856e601b9c7
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmexecexternalwork-transact-sql"></a>sys.dm_exec_external_work (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-pdw-md.md)]

  Возвращает сведения о рабочей нагрузки на рабочий, на каждом вычислительном узле.  
  
 Sys.dm_exec_external_work запроса для определения работы зацикливается для взаимодействия с внешнего источника данных (например, Hadoop или внешние SQL Server).  
  
|Имя столбца|Тип данных|Description|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|execution_id|**nvarchar(32)**|Уникальный идентификатор связанного запроса PolyBase.|В разделе *request_ID* в [sys.dm_exec_requests &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md).|  
|step_index|**int**|Запрос выполняет этот рабочий процесс.|В разделе *step_index* в [sys.dm_exec_requests &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md).|  
|dms_step_index|**int**|Шаг в плане DMS, выполняемый этим исполнителем.|В разделе [sys.dm_exec_dms_workers &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-exec-dms-workers-transact-sql.md).|  
|compute_node_id|**int**|На узле рабочий процесс выполняется.|В разделе [sys.dm_exec_compute_nodes &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-exec-compute-nodes-transact-sql.md).|  
|Тип|**nvarchar(60)**|Тип внешней работы.|«Файл разбиение»|  
|work_id|**int**|Идентификатор фактического разбиения.|Больше или равно 0.|  
|input_name|**nvarchar(4000)**|Имя входа для чтения|Имя файла, при использовании Hadoop.|  
|read_location|**bigint**|Смещение или чтения расположение.|Смещение файла для чтения.|  
|bytes_processed|**bigint**|Общее количество байт, обработанных этим исполнителем.|Больше или равно 0.|  
|length|**bigint**|Длина разбиение или блоке HDFS в случае Hadoop|Определяемые пользователем. Значение по умолчанию — 64 МБ|  
|status|**nvarchar(32)**|Состояние рабочего процесса.|Ожидающие обработки, выполнить, не удалось, прервана|  
|start_time|**datetime**|Начало работы||  
|end_time|**datetime**|Завершения работы||  
|total_elapsed_time|**int**|Общее время в миллисекундах||  
  
## <a name="see-also"></a>См. также:  
 [PolyBase, устранение неполадок с помощью динамических административных представлений](http://msdn.microsoft.com/library/ce9078b7-a750-4f47-b23e-90b83b783d80)   
 [Динамические административные представления и функции (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Динамические административные представления &#40; относящиеся к базе данных Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)  
  
  
