---
title: sys. dm_db_xtp_transactions (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 08/29/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_db_xtp_transactions
- sys.dm_db_xtp_transactions_TSQL
- dm_db_xtp_transactions
- dm_db_xtp_transactions_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_xtp_transactions dynamic management view
ms.assetid: 5c1a0a7a-e851-4b6f-8dfd-c9655fbf5a51
author: stevestein
ms.author: sstein
monikerRange: =azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: cc5f12e50c1e7a7d639acdbf9a244406ce9366c6
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68097928"
---
# <a name="sysdm_db_xtp_transactions-transact-sql"></a>sys.dm_db_xtp_transactions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2014-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-asdb-xxxx-xxx-md.md)]

  Сообщает об активных транзакциях в компоненте In-Memory OLTP.  
  
 Дополнительные сведения см. в разделе [In-Memory OLTP (оптимизация в памяти)](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md).  
    
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|xtp_transaction_id|**bigint**|Внутренний идентификатор для этой транзакции в диспетчере транзакций XTP.|  
|transaction_id|**bigint**|Идентификатор транзакции. Соединения с идентификатором транзакции в других, связанных с ней динамических административных представлениях, например sys.dm_tran_active_transactions.<br /><br /> Значение 0 для транзакций XTP, таких как транзакции, запущенные скомпилированными в собственном коде хранимыми процедурами.|  
|session_id|**smallint**|Идентификатор сеанса, в котором выполняется данная транзакция. Соединения с sys.dm_exec_sessions.|  
|begin_tsn|**bigint**|Начальный серийный номер транзакции.|  
|end_tsn|**bigint**|Конечный серийный номер транзакции.|  
|state|**int**|Состояние транзакции:<br /><br /> 0=ACTIVE<br /><br /> 1=COMMITTED<br /><br /> 2=ABORTED<br /><br /> 3=VALIDATING|  
|state_desc|**nvarchar**|Описание состояния транзакции.|  
|набор по|**int**|Результат транзакции. Допустимы следующие значения:<br /><br /> 0 — ВЫПОЛНЯЕТСЯ<br /><br /> 1 — УСПЕШНОЕ ЗАВЕРШЕНИЕ<br /><br /> 2 — ОШИБКА<br /><br /> 3 — ЗАВИСИМОСТЬ ФИКСАЦИИ<br /><br /> 4 — ПРОВЕРКА ЗАВЕРШЕНА С ОШИБКОЙ (RR)<br /><br /> 5 — ПРОВЕРКА НЕ ПРОЙДЕНА (SR)<br /><br /> 6 — ОТКАТ|  
|result_desc|**nvarchar**|Результат транзакции. Допустимы следующие значения:<br /><br /> ВЫПОЛНЯЕТСЯ<br /><br /> УСПЕШНОЕ ЗАВЕРШЕНИЕ<br /><br /> ошибка<br /><br /> ЗАВИСИМОСТЬ ФИКСАЦИИ<br /><br /> ПРОВЕРКА НЕ ПРОЙДЕНА (RR)<br /><br /> ПРОВЕРКА НЕ ПРОЙДЕНА (SR)<br /><br /> ROLLBACK|  
|last_error|**int**|Только для внутреннего применения|  
|is_speculative|**bit**|Только для внутреннего применения|  
|is_prepared|**bit**|Только для внутреннего применения|  
|is_delayed_durability|**bit**|Только для внутреннего применения|  
|memory_address|**varbinary**|Только для внутреннего применения|  
|database_address|**varbinary**|Только для внутреннего применения|  
|thread_id|**int**|Только для внутреннего применения|  
|read_set_row_count|**int**|Только для внутреннего применения|  
|write_set_row_count|**int**|Только для внутреннего применения|  
|scan_set_count|**int**|Только для внутреннего применения|  
|savepoint_garbage_count|**int**|Только для внутреннего применения|  
|log_bytes_required|**bigint**|Только для внутреннего применения|  
|count_of_allocations|**int**|Только для внутреннего применения|  
|allocated_bytes|**int**|Только для внутреннего применения|  
|reserved_bytes|**int**|Только для внутреннего применения|  
|commit_dependency_count|**int**|Только для внутреннего применения|  
|commit_dependency_total_attempt_count|**int**|Только для внутреннего применения|  
|scan_area|**int**|Только для внутреннего применения|  
|scan_area_desc|**nvarchar**|Только для внутреннего применения|  
|scan_location|**int**|Только для внутреннего применения.|  
|dependent_1_address|**varbinary(8)**|Только для внутреннего применения|  
|dependent_2_address|**varbinary(8)**|Только для внутреннего применения|  
|dependent_3_address|**varbinary(8)**|Только для внутреннего применения|  
|dependent_4_address|**varbinary(8)**|Только для внутреннего применения|  
|dependent_5_address|**varbinary(8)**|Только для внутреннего применения|  
|dependent_6_address|**varbinary(8)**|Только для внутреннего применения|  
|dependent_7_address|**varbinary(8)**|Только для внутреннего применения|  
|dependent_8_address|**varbinary(8)**|Только для внутреннего применения|  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение VIEW DATABASE STATE на сервере.  
  
## <a name="see-also"></a>См. также:  
 [Оптимизированные для памяти динамические административные представления таблиц &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/memory-optimized-table-dynamic-management-views-transact-sql.md)  
  
  
