---
title: sys. dm_db_task_space_usage (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
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
author: CarlRabeler
ms.author: carlrab
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 30eed5a2832f586cc25224c7fbd2e9fdc7df3777
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85738687"
---
# <a name="sysdm_db_task_space_usage-transact-sql"></a>sys.dm_db_task_space_usage (Transact-SQL)
[!INCLUDE [sql-asdb-asdbmi-asdw-pdw](../../includes/applies-to-version/sql-asdb-asdbmi-asdw-pdw.md)]

  Возвращает действия по размещению и удалению из памяти страниц для задачи в базе данных.  
  
> [!NOTE]  
>  Это представление применимо только к [базе данных tempdb](../../relational-databases/databases/tempdb-database.md).  
  
> [!NOTE]  
>  Чтобы вызвать эту функцию из [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] или [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] , используйте имя **sys. dm_pdw_nodes_db_task_space_usage**.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**session_id**|**smallint**|Идентификатор сеанса.|  
|**request_id**|**int**|Идентификатор запроса внутри сеанса.<br /><br /> Запрос также называется пакетом и может состоять из одного или более запросов. Сеанс может иметь несколько запросов, активных в одно и то же время. Каждый запрос в пакете может запустить несколько потоков (задач), если используется параллельный план выполнения.|  
|**exec_context_id**|**int**|Идентификатор контекста выполнения задачи. Дополнительные сведения см. в разделе [sys. dm_os_tasks &#40;&#41;Transact-SQL ](../../relational-databases/system-dynamic-management-views/sys-dm-os-tasks-transact-sql.md).|  
|**database_id**|**smallint**|Идентификатор базы данных.|  
|**user_objects_alloc_page_count**|**bigint**|Количество страниц памяти, зарезервированных или выделенных для пользовательских объектов в данной задаче.|  
|**user_objects_dealloc_page_count**|**bigint**|Количество страниц памяти, освобожденных и более не резервируемых для пользовательских объектов в данной задаче.|  
|**internal_objects_alloc_page_count**|**bigint**|Количество страниц памяти, зарезервированных или выделенных для внутренних объектов в данной задаче.|  
|**internal_objects_dealloc_page_count**|**bigint**|Количество страниц памяти, освобожденных и более не резервируемых для внутренних объектов в данной задаче.|  
|**pdw_node_id**|**int**|**Применимо к**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] ,[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Идентификатор узла, на котором находится данное распределение.|  
  
## <a name="permissions"></a>Разрешения

В [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] необходимо `VIEW SERVER STATE` разрешение.   
На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] уровнях Premium требуется `VIEW DATABASE STATE` разрешение в базе данных. На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] уровнях Standard и Basic требуется **Администратор сервера** или учетная запись **администратора Azure Active Directory** .   

## <a name="remarks"></a>Примечания  
 IAM-страницы не включены ни в один из счетчиков страниц, сведения о котором приводятся в данном представлении.  
  
 Счетчики страниц сбрасываются в ноль (0) в начале запроса. Их значения суммируются на уровне сеанса при завершении запроса. Дополнительные сведения см. в разделе [sys.dm_db_session_space_usage (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-db-session-space-usage-transact-sql.md).  
  
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
 Внутренние объекты доступны только в **базе данных tempdb**. Следующие объекты включаются в счетчики страниц внутренних объектов:  
  
-   рабочие таблицы для выполнения операций с курсорами и буферами, а также для хранения временных больших объектов (LOB);  
  
-   рабочие файлы для таких операций, как хэш-соединение  
  
-   Сортировки  
  
## <a name="physical-joins"></a>Физические соединения  
 ![Физические соединения для sys.dm_db_session_task_usage](../../relational-databases/system-dynamic-management-views/media/join-dm-db-task-space-usage-1.gif "Физические соединения для sys.dm_db_session_task_usage")  
  
## <a name="relationship-cardinalities"></a>Количество элементов связей  
  
|Исходный тип|Кому|Связь|  
|----------|--------|------------------|  
|dm_db_task_space_usage.request_id|dm_exec_requests.request_id|Один к одному|  
|dm_db_task_space_usage.session_id|dm_exec_requests.session_id|Один к одному|  
  
## <a name="see-also"></a>См. также  
 [Динамические административные представления и функции &#40;&#41;Transact-SQL](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Динамические административные представления, связанные с базами данных &#40;&#41;Transact-SQL](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)   
 [sys. dm_exec_sessions &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql.md)   
 [sys. dm_exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)   
 [sys. dm_os_tasks &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-tasks-transact-sql.md)   
 [sys. dm_db_session_space_usage &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-session-space-usage-transact-sql.md)   
 [sys.dm_db_file_space_usage (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-db-file-space-usage-transact-sql.md)  
  
  


