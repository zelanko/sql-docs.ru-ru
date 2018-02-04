---
title: "sys.dm_db_task_space_usage (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dm_db_task_space_usage_TSQL
- sys.dm_db_task_space_usage_TSQL
- dm_db_task_space_usage
- sys.dm_db_task_space_usage
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_task_space_usage dynamic management view
ms.assetid: fb0c87e5-43b9-466a-a8df-11b3851dc6d0
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2a10c12a2510baaace72219803e9f3cc26bebf20
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/03/2018
---
# <a name="sysdmdbtaskspaceusage-transact-sql"></a>sys.dm_db_task_space_usage (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает действия по размещению и удалению из памяти страниц для задачи в базе данных.  
  
> [!NOTE]  
>  Это представление применимо только к [базы данных tempdb](../../relational-databases/databases/tempdb-database.md).  
  
> [!NOTE]  
>  Вызов его из [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] или [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], используйте имя **sys.dm_pdw_nodes_db_task_space_usage**.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**session_id**|**smallint**|Идентификатор сеанса.|  
|**request_id**|**int**|Идентификатор запроса внутри сеанса.<br /><br /> Запрос также называется пакетом и может состоять из одного или более запросов. Сеанс может иметь несколько запросов, активных в одно и то же время. Каждый запрос в пакете может запустить несколько потоков (задач), если используется параллельный план выполнения.|  
|**exec_context_id**|**int**|Идентификатор контекста выполнения задачи. Дополнительные сведения см. в разделе [sys.dm_os_tasks &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-os-tasks-transact-sql.md).|  
|**database_id**|**smallint**|Идентификатор базы данных.|  
|**user_objects_alloc_page_count**|**bigint**|Количество страниц памяти, зарезервированных или выделенных для пользовательских объектов в данной задаче.|  
|**user_objects_dealloc_page_count**|**bigint**|Количество страниц памяти, освобожденных и более не резервируемых для пользовательских объектов в данной задаче.|  
|**internal_objects_alloc_page_count**|**bigint**|Количество страниц памяти, зарезервированных или выделенных для внутренних объектов в данной задаче.|  
|**internal_objects_dealloc_page_count**|**bigint**|Количество страниц памяти, освобожденных и более не резервируемых для внутренних объектов в данной задаче.|  
|**pdw_node_id**|**int**|**Применяется к**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Идентификатор для узла, это распределение.|  
  
## <a name="permissions"></a>Разрешения  
 На [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] необходимо разрешение VIEW SERVER STATE на сервере.  
  
 На [!INCLUDE[ssSDS](../../includes/sssds-md.md)] уровней Premium необходимо разрешение VIEW DATABASE STATE в базе данных. На [!INCLUDE[ssSDS](../../includes/sssds-md.md)] уровней Standard и Basic требуется [!INCLUDE[ssSDS](../../includes/sssds-md.md)] учетная запись администратора.  
  
## <a name="remarks"></a>Remarks  
 IAM-страницы не включены ни в один из счетчиков страниц, сведения о котором приводятся в данном представлении.  
  
 Счетчики страниц сбрасываются в ноль (0) в начале запроса. Их значения суммируются на уровне сеанса при завершении запроса. Дополнительные сведения см. в разделе [sys.dm_db_session_space_usage &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-db-session-space-usage-transact-sql.md).  
  
 Кэширование рабочей таблицы, временной таблицы и операции отложенного обновления влияет на количество страниц, выделенных и освобожденных для указанной задачи.  
  
## <a name="user-objects"></a>Пользовательские объекты  
 Следующие объекты включаются в счетчики страниц пользовательских объектов.  
  
-   Пользовательские таблицы и индексы  
  
-   Системные таблицы и индексы  
  
-   Глобальные временные таблицы и индексы  
  
-   Локальные временные таблицы и индексы  
  
-   Табличные переменные  
  
-   Таблицы, возвращаемые в функциях с табличным значением  
  
## <a name="internal-objects"></a>Внутренние объекты  
 Внутренние объекты имеются только в **tempdb**. Следующие объекты включаются в счетчики страниц внутренних объектов:  
  
-   рабочие таблицы для выполнения операций с курсорами и буферами, а также для хранения временных больших объектов (LOB);  
  
-   рабочие файлы для таких операций, как хэш-соединение  
  
-   Сортировки  
  
## <a name="physical-joins"></a>Физические соединения  
 ![Физические соединения для sys.dm_db_session_task_usage](../../relational-databases/system-dynamic-management-views/media/join-dm-db-task-space-usage-1.gif "физического соединения для sys.dm_db_session_task_usage")  
  
## <a name="relationship-cardinalities"></a>Количество элементов связей  
  
|От|Чтобы|Связь|  
|----------|--------|------------------|  
|dm_db_task_space_usage.request_id|dm_exec_requests.request_id|Один к одному|  
|dm_db_task_space_usage.session_id|dm_exec_requests.session_id|Один к одному|  
  
## <a name="see-also"></a>См. также  
 [Динамические административные представления и функции (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Динамические административные представления &#40; относящиеся к базе данных Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)   
 [sys.dm_exec_sessions &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql.md)   
 [sys.dm_exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)   
 [sys.dm_os_tasks &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-tasks-transact-sql.md)   
 [sys.dm_db_session_space_usage &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-session-space-usage-transact-sql.md)   
 [sys.dm_db_file_space_usage (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-db-file-space-usage-transact-sql.md)  
  
  


