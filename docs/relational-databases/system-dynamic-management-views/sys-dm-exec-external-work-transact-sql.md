---
title: sys. DM _exec_external_work (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2019
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
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
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 5afdfd4f9a5f66845ae6d3798910fc2c4bf5ab8a
ms.sourcegitcommit: 830149bdd6419b2299aec3f60d59e80ce4f3eb80
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/04/2019
ms.locfileid: "73532951"
---
# <a name="sysdm_exec_external_work-transact-sql"></a>sys. DM _exec_external_work (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-pdw-md.md)]

  Возвращает сведения о рабочей нагрузке для каждого рабочего узла на каждом из вычислений.  
  
 Запросите представление sys. DM _exec_external_work, чтобы обозначить работу для взаимодействия с внешним источником данных (например, Hadoop или External SQL Server).  
  
|Имя столбца|Тип данных|Описание|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|execution_id|`nvarchar(32)`|Уникальный идентификатор связанного запроса Polybase.|См. раздел *request_ID* в [sys. &#40;DM _exec_requests Transact&#41;-SQL](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md).|  
|step_index|`int`|Запрос, выполняемый этим исполнителем.|См. раздел *step_index* в [sys. &#40;DM _exec_requests Transact&#41;-SQL](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md).|  
|dms_step_index|`int`|Шаг в плане DMS, который выполняется этим исполнителем.|См. раздел [sys. &#40;DM _EXEC_DMS_WORKERS Transact&#41;-SQL](../../relational-databases/system-dynamic-management-views/sys-dm-exec-dms-workers-transact-sql.md).|  
|compute_node_id|`int`|Узел, на котором запущена Рабочая роль.|См. раздел [sys. &#40;DM _EXEC_COMPUTE_NODES Transact&#41;-SQL](../../relational-databases/system-dynamic-management-views/sys-dm-exec-compute-nodes-transact-sql.md).|  
|type|`nvarchar(60)`|Тип внешней работы.|"Разделение файлов"|  
|work_id|`int`|Идентификатор фактического разбиения.|Больше или равно 0.|  
|input_name|`nvarchar(4000)`|Имя входных данных для чтения|Имя файла при использовании Hadoop.|  
|read_location|`bigint`|Смещение или расположение чтения.|Смещение файла для чтения.|  
|bytes_processed|`bigint`|Общее число байтов, обработанных этим исполнителем.|Больше или равно 0.|  
|length|`bigint`|Длина блока Split или HDFS в случае Hadoop|Определяемый пользователем. Значение по умолчанию — 64M|  
|status|`nvarchar(32)`|Состояние рабочей роли|Ожидание, обработка, завершение, сбой, прервано|  
|start_time|`datetime`|Начало работы||  
|end_time|`datetime`|Окончание работы||  
|total_elapsed_time|`int`|Общее время в миллисекундах||
|compute_pool_id|`int`|Уникальный идентификатор пула.|

## <a name="see-also"></a>См. также раздел  
 [Устранение неполадок в polybase с помощью динамических административных представлений](https://msdn.microsoft.com/library/ce9078b7-a750-4f47-b23e-90b83b783d80)   
 [Динамические административные представления и функции (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Динамические административные представления &#40;, связанные с базами данных TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)  
  
  
