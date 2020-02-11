---
title: sys. dm_xtp_transaction_stats (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_xtp_transaction_stats_TSQL
- dm_xtp_transaction_stats
- sys.dm_xtp_transaction_stats_TSQL
- sys.dm_xtp_transaction_stats
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_xtp_transaction_stats dynamic management view
ms.assetid: 9389f48d-0de5-47bd-9821-4db8f04504e4
author: stevestein
ms.author: sstein
ms.openlocfilehash: 755b5f836b833512a122ad92e5cedbd7e938a4e8
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68090075"
---
# <a name="sysdm_xtp_transaction_stats-transact-sql"></a>sys.dm_xtp_transaction_stats (Transact-SQL)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

  Предоставляет статистические данные о транзакциях, выполненных с момента запуска сервера.  
  
 Дополнительные сведения см. в разделе [In-Memory OLTP (оптимизация в памяти)](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md).  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|total_count|**bigint**|Общее число транзакций, которые были запущены в компоненте In-Memory OLTP.|  
|read_only_count|**bigint**|Число транзакций в режиме только для чтения.|  
|total_aborts|**bigint**|Общее число транзакций, которые были прерваны пользователем или системой.|  
|user_aborts|**bigint**|Количество прерываний, инициированных системой. Эти прерывания могут быть вызваны конфликтами операции записи, ошибками проверки и зависимости.|  
|validation_failures|**bigint**|Количество раз, когда транзакция была прервана вследствие ошибки проверки.|  
|dependencies_taken|**bigint**|Только для внутреннего применения.|  
|dependencies_failed|**bigint**|Количество раз, когда транзакция была прервана, поскольку транзакция, от которой она зависела, была прервана.|  
|savepoint_create|**bigint**|Количество созданных точек сохранения. Новая точка сохранения создается для каждого атомарного блока.|  
|savepoint_rollbacks|**bigint**|Количество откатов к предыдущей точке сохранения.|  
|savepoint_refreshes|**bigint**|Только для внутреннего применения.|  
|log_bytes_written|**bigint**|Общее число байтов, записанных в записи журнала компонента In-Memory OLTP.|  
|log_IO_count|**bigint**|Общее число транзакций, для которых требуется ввести журнал операций ввода-вывода. Учитываются только транзакции в долговечных таблицах.|  
|phantom_scans_started|**bigint**|Только для внутреннего применения.|  
|phatom_scans_retries|**bigint**|Только для внутреннего применения.|  
|phantom_rows_touched|**bigint**|Только для внутреннего применения.|  
|phantom_rows_expiring|**bigint**|Только для внутреннего применения.|  
|phantom_rows_expired|**bigint**|Только для внутреннего применения.|  
|phantom_rows_expired_removed|**bigint**|Только для внутреннего применения.|  
|scans_started|**bigint**|Только для внутреннего применения.|  
|scans_retried|**bigint**|Только для внутреннего применения.|  
|rows_returned|**bigint**|Только для внутреннего применения.|  
|rows_touched|**bigint**|Только для внутреннего применения.|  
|rows_expiring|**bigint**|Только для внутреннего применения.|  
|rows_expired|**bigint**|Только для внутреннего применения.|  
|rows_expired_removed|**bigint**|Только для внутреннего применения.|  
|rows_inserted|**bigint**|Только для внутреннего применения.|  
|rows_updated|**bigint**|Только для внутреннего применения.|  
|rows_deleted|**bigint**|Только для внутреннего применения.|  
|write_conflicts|**bigint**|Только для внутреннего применения.|  
|unique_constraint_violations|**bigint**|Общее число нарушений ограничений уникальности.|  
  
## <a name="permissions"></a>Разрешения  
 необходимо разрешение VIEW SERVER STATE на сервере.  
  
## <a name="see-also"></a>См. также:  
 [Динамические административные представления оптимизированной для памяти таблицы &#40;языке Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/memory-optimized-table-dynamic-management-views-transact-sql.md)  
  
  
