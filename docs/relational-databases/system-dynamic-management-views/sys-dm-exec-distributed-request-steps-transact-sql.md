---
title: sys. dm_exec_distributed_request_steps (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- SYS.DM_EXEC_DISTRIBUTED_REQUEST_STEPS_TSQL
- DM_EXEC_DISTRIBUTED_REQUEST_STEPS_TSQL
- DM_EXEC_DISTRIBUTED_REQUEST_STEPS
dev_langs:
- TSQL
helpviewer_keywords:
- PolyBase,views
- PolyBase
- dm_exec_distributed_request_steps
- sys.dm_exec_distributed_request_steps management view
ms.assetid: 1954541d-b716-4e03-8fcc-7022f428e01d
author: CarlRabeler
ms.author: carlrab
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 2e5b2dcf0cf62d9fe6157284409d96bec8f105b4
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82833777"
---
# <a name="sysdm_exec_distributed_request_steps-transact-sql"></a>sys. dm_exec_distributed_request_steps (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-pdw-md.md)]

  Содержит сведения обо всех шагах, составляющих данный запрос или запрос Polybase. В нем отображается одна строка для каждого шага запроса.  
  
|Имя столбца|Тип данных|Описание|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|execution_id|**int**|execution_id и step_index сделать ключ для этого представления. Уникальный числовой идентификатор, связанный с запросом.|См. раздел ID в [представлении sys. dm_exec_requests &#40;&#41;Transact-SQL ](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md).|  
|step_index|**int**|Расположение этого шага в последовательности шагов, составляющих запрос.|от 0 до (n – 1) для запроса с n шагами.|  
|operation_type|**nvarchar(128)**|Тип операции, представленной этим шагом.|"MoveOperation", "OnOperation", "Рандомидоператион", "RemoteOperation", "ReturnOperation", "ShuffleMoveOperation", "Темптаблепропертиесоператион", "Дропдиагностикснотифйоператион", "HadoopShuffleOperation", "HadoopBroadCastOperation", "HadoopRoundRobinOperation"|  
|distribution_type|**nvarchar(32)**|Место исполнения шага.|"Аллкомпутенодес", "Аллдистрибутионс", "ComputeNode", "Distribution", "AllNodes", "Субсетнодес", "Distribution", "unspecifieded".|  
|location_type|**nvarchar(32)**|Место исполнения шага.|"COMPUTE", "Head" или "DMS". Все шаги перемещения данных показывают "DMS".|  
|status|**nvarchar(32)**|Состояние этого шага|"Pending", "работает", "Complete", "Failed", "Ундофаилед", "Пендингканцел", "recommit", "Undone", "Abortd"|  
|error_id|**nvarchar (36)**|Уникальный идентификатор ошибки, связанной с этим шагом, если таковой имеется|Ознакомьтесь с идентификатором [sys. dm_exec_compute_node_errors &#40;&#41;Transact-SQL ](../../relational-databases/system-dynamic-management-views/sys-dm-exec-compute-node-errors-transact-sql.md), значение null, если ошибка не возникла.|  
|start_time|**datetime**|Время начала выполнения этапа|Меньше или равно текущему времени и больше или равно end_compile_time запроса, к которому относится этот шаг.|  
|end_time|**datetime**|Время, когда выполнение этого шага было завершено, было отменено или завершилось сбоем.|Меньшее или равное текущему времени и больше или равно start_time, установите значение NULL для шагов, выполняемых в данный момент или в очереди.|  
|total_elapsed_time|**int**|Общее количество времени выполнения шага запроса (в миллисекундах)|Между 0 и разностью между end_time и start_time. 0 для шагов в очереди.|  
|row_count|**bigint**|Общее число строк, измененных или возвращенных этим запросом|0 для шагов, которые не изменяют или возвращают данные, количество затронутых строк в противном случае. Задайте значение-1 для шагов DMS.|  
|.|nvarchar(4000)|Содержит полный текст команды этого шага.|Любая допустимая строка запроса для шага. Усекается, если длиннее 4000 символов.|  
  
## <a name="see-also"></a>См. также  
 [Устранение неполадок в Polybase с помощью динамических административных представлений](https://msdn.microsoft.com/library/ce9078b7-a750-4f47-b23e-90b83b783d80)   
 [Динамические административные представления и функции &#40;&#41;Transact-SQL](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Динамические административные представления, связанные с базами данных &#40;&#41;Transact-SQL](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)  
  
  
