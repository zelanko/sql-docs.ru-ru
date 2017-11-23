---
title: "sys.pdw_loader_backup_run_details (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: 
ms.prod_service: sql-data-warehouse, pdw
ms.service: sql-data-warehouse
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
ms.assetid: 04fc004f-ee15-4d7a-be08-78357aa99b55
caps.latest.revision: "9"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 79e69b2a74841e790eb178aa2f8d1b693cfe7c5a
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="syspdwloaderbackuprundetails-transact-sql"></a>sys.pdw_loader_backup_run_details (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Содержит подробные сведения, помимо сведения в дополнительную [sys.pdw_loader_backup_runs &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-pdw-loader-backup-runs-transact-sql.md), о выполняющихся и завершенных операциях backup и restore в [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] , а также о выполняющихся и завершенных резервного копирования, восстановления и операций загрузки в [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]. Сведения, сохраняются после перезагрузки системы.  
  
|Имя столбца|Тип данных|Description|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|run_id|**int**|Уникальный идентификатор для конкретного резервного копирования или восстановления запуска.<br /><br /> run_id и pdw_node_id формируют ключ для этого представления.||  
|pdw_node_id|**int**|Уникальный идентификатор устройства узла, для которого эта запись содержит подробные сведения.<br /><br /> run_id и pdw_node_id формируют ключ для этого представления.|В разделе node_id в [sys.dm_pdw_nodes &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-transact-sql.md).|  
|status|**nvarchar(16) в формате**|Текущее состояние выполнения.|«ОТМЕНЕН», «ЗАВЕРШЕНО», «ОШИБКА», «QUEUED», «РАБОТАЕТ»|  
|start_time|**datetime**|Время начала операции на данный узел.||  
|end_time|**datetime**|Время операции окончания на данный узел, если таковые имеются.||  
|total_elapsed_time|**int**|Общее время выполнения операции на данный узел.|Если total_elapsed_time превышает максимальное значение для целого числа (24.8 дней в миллисекундах), это приведет к переполнению материализации сбой из-за.<br /><br /> Максимальное значение в миллисекундах соответствует 24.8 дней.|  
|Ход выполнения|**int**|Ход выполнения операции, выраженное в процентах.|от 0 до 100|  
  
## <a name="see-also"></a>См. также:  
 [Хранилище данных SQL и представления каталога хранилища параллельных данных](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
