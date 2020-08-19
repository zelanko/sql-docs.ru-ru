---
description: sys. dm_exec_compute_node_status (Transact-SQL)
title: sys. dm_exec_compute_node_status (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2019
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- DM_EXEC_COMPUTE_NODE_STATUS_TSQL
- DM_EXEC_COMPUTE_NODE_STATUS
dev_langs:
- TSQL
helpviewer_keywords:
- PolyBase,views
- PolyBase
- dm_exec_compute_node_status
- sys.dm_exec_compute_node_status management view
ms.assetid: b606f91f-3a08-4a4f-bb57-32ae155b3738
author: CarlRabeler
ms.author: carlrab
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 182a6fff7ff2cf0af1b009a3c5acc79e00c8365a
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88447635"
---
# <a name="sysdm_exec_compute_node_status-transact-sql"></a>sys. dm_exec_compute_node_status (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-pdw-md.md)]

  Содержит дополнительные сведения о производительности и состоянии всех узлов Polybase. Содержит по одной строке на каждый узел.  
  
|Имя столбца|Тип данных|Description|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|compute_node_id|`int`|Уникальный числовой идентификатор, связанный с узлом.|Уникален в масштабном кластере независимо от типа.|  
|process_id|`int`|||  
|process_name|`nvarchar(255)`|Логическое имя узла.|Любая строка соответствующей длины.|  
|allocated_memory|`bigint`|Общая выделенная память на этом узле.||  
|available_memory|`bigint`|Общая объем доступной памяти на этом узле.||  
|process_cpu_usage|`bigint`|Общее использование ЦП процесса в тактах.||  
|total_cpu_usage|`bigint`|Общее использование ЦП в тактах.||  
|thread_count|`bigint`|Общее число потоков, используемых на этом узле.||  
|handle_count|`bigint`|Общее число используемых дескрипторов на этом узле.||  
|total_elapsed_time|`bigint`|Общее время, прошедшее с момента запуска или перезапуска системы.|Общее время, прошедшее с момента запуска или перезапуска системы. Если total_elapsed_time превышает максимальное значение для целого числа (24,8 дней в миллисекундах), это приведет к сбою материализации из-за переполнения. Максимальное значение в миллисекундах эквивалентно 24,8 дням.|  
|is_available|`bit`|Флаг, указывающий, доступен ли этот узел.||  
|sent_time|`datetime`|Время последней отправки сетевого пакета этим||  
|received_time|`datetime`|Время последней отправки сетевого пакета этим узлом.||  
|error_id|`nvarchar(36)`|Уникальный идентификатор последней ошибки, произошедшей на этом узле.||
|compute_pool_id|`int`|Уникальный идентификатор пула.|

## <a name="see-also"></a>См. также  
 [Устранение неполадок в Polybase с помощью динамических административных представлений](https://msdn.microsoft.com/library/ce9078b7-a750-4f47-b23e-90b83b783d80)   
 [Динамические административные представления и функции (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Динамические административные представления, связанные с базами данных &#40;&#41;Transact-SQL ](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)  
  
  
