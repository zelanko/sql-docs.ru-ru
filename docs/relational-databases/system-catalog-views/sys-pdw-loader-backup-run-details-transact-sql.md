---
description: sys. pdw_loader_backup_run_details (Transact-SQL)
title: sys. pdw_loader_backup_run_details (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 04fc004f-ee15-4d7a-be08-78357aa99b55
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: d42094beb9b29cc620007bb1d590a6fa8dc33987
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88400530"
---
# <a name="syspdw_loader_backup_run_details-transact-sql"></a>sys. pdw_loader_backup_run_details (Transact-SQL)
[!INCLUDE[applies-to-version/asa-pdw](../../includes/applies-to-version/asa-pdw.md)]

  Содержит более подробные сведения, помимо сведений в [sys. pdw_loader_backup_runs &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-loader-backup-runs-transact-sql.md), о текущих и завершенных операциях резервного копирования и восстановления в, а также [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] о текущих и завершенных операциях резервного копирования, восстановления и загрузки в [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] . Эта информация сохраняется и после перезапуска системы.  
  
|Имя столбца|Тип данных|Description|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|run_id|**int**|Уникальный идентификатор для конкретного выполнения резервного копирования или восстановления.<br /><br /> run_id и pdw_node_id формируют ключ для этого представления.||  
|pdw_node_id|**int**|Уникальный идентификатор узла устройства, для которого эта запись содержит сведения.<br /><br /> run_id и pdw_node_id формируют ключ для этого представления.|См. раздел node_id в [sys. dm_pdw_nodes &#40;&#41;Transact-SQL ](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-transact-sql.md).|  
|status|**nvarchar (16)**|Текущее состояние запуска.|"ОТМЕНЕНО", "ЗАВЕРШЕНО", "СБОЙ", "В ОЧЕРЕДИ", "ВЫПОЛНЯЕТСЯ"|  
|start_time|**datetime**|Время начала операции на этом конкретном узле.||  
|end_time|**datetime**|Время завершения операции на данном конкретном узле (при наличии).||  
|total_elapsed_time|**int**|Общее время выполнения операции на этом конкретном узле.|Если total_elapsed_time превышает максимальное значение для целого числа (24,8 дней в миллисекундах), это приведет к сбою материализации из-за переполнения.<br /><br /> Максимальное значение в миллисекундах эквивалентно 24,8 дням.|  
|progress|**int**|Ход выполнения операции, выраженный в процентах.|0–100|  
  
## <a name="see-also"></a>См. также:  
 [SQL Data Warehouse and Parallel Data Warehouse Catalog Views](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md) (Представления каталога в службе "Хранилище данных SQL" и Parallel Data Warehouse)  
  
  
