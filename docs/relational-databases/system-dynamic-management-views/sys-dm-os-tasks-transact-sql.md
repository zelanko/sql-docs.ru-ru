---
title: sys.dm_os_tasks (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/13/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_os_tasks
- sys.dm_os_tasks_TSQL
- dm_os_tasks_TSQL
- dm_os_tasks
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_tasks dynamic management view
ms.assetid: 180a3c41-e71b-4670-819d-85ea7ef98bac
caps.latest.revision: 34
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 5cd963f2655fa86c906624fa81eed681dbe4c999
ms.sourcegitcommit: d2573a8dec2d4102ce8882ee232cdba080d39628
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/07/2018
---
# <a name="sysdmostasks-transact-sql"></a>sys.dm_os_tasks (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает одну строку для каждой активной задачи в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  Вызов его из [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] или [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], используйте имя **sys.dm_pdw_nodes_os_tasks**.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**task_address**|**varbinary(8)**|Адрес объекта в памяти.|  
|**task_state**|**nvarchar(60)**|Состояние задачи. Может иметь одно из следующих значений.<br /><br /> Ожидание: Ожидание рабочего потока.<br /><br /> Готово к ЗАПУСКУ: Готов к запуску, но ожидает получения такта.<br /><br /> ВЫПОЛНЕНИЯ: В настоящее время выполняется в планировщике.<br /><br /> ПРИОСТАНОВЛЕНО: У задачи есть исполнитель, но ожидает события.<br /><br /> ВЫПОЛНЕНО: завершено.<br /><br /> SPINLOOP: Заблокирована с ожиданием из.|  
|**context_switches_count**|**int**|Число переключений контекста планировщика, которые задача уже выполнила.|  
|**pending_io_count**|**int**|Количество физических операций ввода-вывода, выполняемых этой задачей.|  
|**pending_io_byte_count**|**bigint**|Суммарное количество байт, обработанных в операциях ввода-вывода, выполняемых этой задачей.|  
|**pending_io_byte_average**|**int**|Среднее количество байт, обработанных в операциях ввода-вывода, выполняемых этой задачей.|  
|**scheduler_id**|**int**|Идентификатор родительского планировщика. Это дескриптор сведений планировщика для этой задачи. Дополнительные сведения см. в разделе [sys.dm_os_schedulers &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-schedulers-transact-sql.md).|  
|**session_id**|**smallint**|Идентификатор сеанса, связанного с задачей.|  
|**exec_context_id**|**int**|Идентификатор контекста выполнения, связанного с задачей.|  
|**request_id**|**int**|Идентификатор запроса задачи. Дополнительные сведения см. в разделе [sys.dm_exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md).|  
|**worker_address**|**varbinary(8)**|Адрес в памяти для исполнителя, выполняющего задачу.<br /><br /> NULL = задача либо ожидает готовности исполнителя, либо выполнение задачи только что завершилось.<br /><br /> Дополнительные сведения см. в разделе [sys.dm_os_workers &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-workers-transact-sql.md).|  
|**host_address**|**varbinary(8)**|Адрес сервера в памяти.<br /><br /> 0 = задача создавалась без помощи сервера. Помогает идентифицировать сервер, использованный для создания этой задачи.<br /><br /> Дополнительные сведения см. в разделе [sys.dm_os_hosts &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-hosts-transact-sql.md).|  
|**parent_task_address**|**varbinary(8)**|Адрес в памяти задачи, являющейся родительской задачей объекта.|  
|**pdw_node_id**|**int**|**Применяется к**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Идентификатор для узла, это распределение.|  
  
## <a name="permissions"></a>Разрешения

На [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], требуется `VIEW SERVER STATE` разрешение.   
На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], требуется `VIEW DATABASE STATE` разрешение в базе данных.   

## <a name="examples"></a>Примеры  
  
### <a name="a-monitoring-parallel-requests"></a>A. Наблюдение за параллельными запросами  
 Для запросов, которые выполняются параллельно, будет отображено несколько строк для того же сочетания (\<**session_id**>, \< **request_id**>). Используйте следующий запрос для поиска [Настройка параметра max degree of parallelism Server Configuration Option](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md) для всех активных запросов.  
  
> [!NOTE]  
>  Объект **request_id** уникален в пределах одного сеанса.  
  
```  
SELECT  
    task_address,  
    task_state,  
    context_switches_count,  
    pending_io_count,  
    pending_io_byte_count,  
    pending_io_byte_average,  
    scheduler_id,  
    session_id,  
    exec_context_id,  
    request_id,  
    worker_address,  
    host_address  
  FROM sys.dm_os_tasks  
  ORDER BY session_id, request_id;  
```  
  
### <a name="b-associating-session-ids-with-windows-threads"></a>Б. Сопоставление идентификатора сеанса с потоками Windows  
 Можно использовать следующий запрос для сопоставления значения идентификатора сеанса со значением идентификатора потока Windows. Затем можно наблюдать за производительностью потока в системном мониторе Windows. Следующий запрос не возвращает сведений для сеансов, находящихся в ждущем режиме.  
  
```  
SELECT STasks.session_id, SThreads.os_thread_id  
  FROM sys.dm_os_tasks AS STasks  
  INNER JOIN sys.dm_os_threads AS SThreads  
    ON STasks.worker_address = SThreads.worker_address  
  WHERE STasks.session_id IS NOT NULL  
  ORDER BY STasks.session_id;  
GO  
```  
  
## <a name="see-also"></a>См. также  
  [Динамические административные представления, относящиеся к операционной системе SQL Server &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  


