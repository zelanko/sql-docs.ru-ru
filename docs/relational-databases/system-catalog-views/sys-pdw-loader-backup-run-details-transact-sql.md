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
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 04fc004f-ee15-4d7a-be08-78357aa99b55
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 02b934db7152723e66aab5818751cb748d2e2a87
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/03/2018
---
# <a name="syspdwloaderbackuprundetails-transact-sql"></a>sys.pdw_loader_backup_run_details (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Содержит подробные сведения, помимо сведения в дополнительную [sys.pdw_loader_backup_runs &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-pdw-loader-backup-runs-transact-sql.md), о выполняющихся и завершенных операциях backup и restore в [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] , а также о выполняющихся и завершенных резервного копирования, восстановления и операций загрузки в [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]. Сведения, сохраняются после перезагрузки системы.  
  
|Имя столбца|Тип данных|Описание|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|run_id|**int**|Уникальный идентификатор для конкретного резервного копирования или восстановления запуска.<br /><br /> run_id и pdw_node_id формируют ключ для этого представления.||  
|pdw_node_id|**int**|Уникальный идентификатор устройства узла, для которого эта запись содержит подробные сведения.<br /><br /> run_id и pdw_node_id формируют ключ для этого представления.|В разделе node_id в [sys.dm_pdw_nodes &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-transact-sql.md).|  
|status|**nvarchar(16)**|Текущее состояние выполнения.|«ОТМЕНЕН», «ЗАВЕРШЕНО», «ОШИБКА», «QUEUED», «РАБОТАЕТ»|  
|start_time|**datetime**|Время начала операции на данный узел.||  
|end_time|**datetime**|Время операции окончания на данный узел, если таковые имеются.||  
|total_elapsed_time|**int**|Общее время выполнения операции на данный узел.|Если total_elapsed_time превышает максимальное значение для целого числа (24.8 дней в миллисекундах), это приведет к переполнению материализации сбой из-за.<br /><br /> Максимальное значение в миллисекундах соответствует 24.8 дней.|  
|Ход выполнения|**int**|Ход выполнения операции, выраженное в процентах.|от 0 до 100|  
  
## <a name="see-also"></a>См. также  
 [Хранилище данных SQL и представления каталога хранилища параллельных данных](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
