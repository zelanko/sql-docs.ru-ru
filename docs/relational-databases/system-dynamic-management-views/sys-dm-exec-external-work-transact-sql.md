---
description: sys. dm_exec_external_work (Transact-SQL)
title: sys. dm_exec_external_work (Transact-SQL) | Документация Майкрософт
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
author: CarlRabeler
ms.author: carlrab
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 4476f9a3beaf7906d69763462f5b7558989241eb
ms.sourcegitcommit: 5da46e16b2c9710414fe36af9670461fb07555dc
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/01/2020
ms.locfileid: "89283645"
---
# <a name="sysdm_exec_external_work-transact-sql"></a>sys. dm_exec_external_work (Transact-SQL)
[!INCLUDE [sqlserver2016-asa-pdw](../../includes/applies-to-version/sqlserver2016-asa-pdw.md)]

  Возвращает сведения о рабочей нагрузке для каждого рабочего узла на каждом из вычислений.  
  
 Запросите представление sys. dm_exec_external_work, чтобы обозначить работу для взаимодействия с внешним источником данных (например, Hadoop или External SQL Server).  
  
|Имя столбца|Тип данных|Description|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|execution_id|`nvarchar(32)`|Уникальный идентификатор связанного запроса Polybase.|См. раздел *request_ID* в [sys. Dm_exec_requests &#40;&#41;Transact-SQL ](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md).|  
|step_index|`int`|Запрос, выполняемый этим исполнителем.|См. раздел *step_index* в  [sys. Dm_exec_requests &#40;&#41;Transact-SQL ](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md).|  
|dms_step_index|`int`|Шаг в плане DMS, который выполняется этим исполнителем.|См. раздел [sys. dm_exec_dms_workers &#40;&#41;Transact-SQL ](../../relational-databases/system-dynamic-management-views/sys-dm-exec-dms-workers-transact-sql.md).|  
|compute_node_id|`int`|Узел, на котором запущена Рабочая роль.|См. раздел [sys. dm_exec_compute_nodes &#40;&#41;Transact-SQL ](../../relational-databases/system-dynamic-management-views/sys-dm-exec-compute-nodes-transact-sql.md).|  
|type|`nvarchar(60)`|Тип внешней работы.|"Разделение файлов"|  
|work_id|`int`|Идентификатор фактического разбиения.|Больше или равно 0.|  
|input_name|`nvarchar(4000)`|Имя входных данных для чтения|Имя файла при использовании Hadoop.|  
|read_location|`bigint`|Смещение или расположение чтения.|Смещение файла для чтения.|  
|bytes_processed|`bigint`|Всего байт, выделенных для обработки данных этим исполнителем. Это может не обязательно представлять итоговые данные, возвращаемые запросом |Больше или равно 0.|  
|length|`bigint`|Длина блока Split или HDFS в случае Hadoop|Определяемый пользователем. Значение по умолчанию — 64M|  
|status|`nvarchar(32)`|Состояние рабочей роли|Ожидание, обработка, завершение, сбой, прервано|  
|start_time|`datetime`|Начало работы||  
|end_time|`datetime`|Окончание работы||  
|total_elapsed_time|`int`|Общее время в миллисекундах||
|compute_pool_id|`int`|Уникальный идентификатор пула.|

## <a name="see-also"></a>См. также:  
 [Устранение неполадок в Polybase с помощью динамических административных представлений](https://msdn.microsoft.com/library/ce9078b7-a750-4f47-b23e-90b83b783d80)   
 [Динамические административные представления и функции (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Динамические административные представления, связанные с базами данных &#40;&#41;Transact-SQL ](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)  
  
  
