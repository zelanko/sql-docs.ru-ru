---
title: sys. dm_db_session_space_usage (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 11/16/2015
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_db_session_space_usage_TSQL
- dm_db_session_space_usage
- sys.dm_db_session_space_usage
- sys.dm_db_session_space_usage_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_session_space_usage dynamic management view
ms.assetid: a67a6045-8e14-460a-9fe3-912b846c08c1
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 5e4febf0882f57f7d1545f86cbe4c65e322226dc
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68263972"
---
# <a name="sysdm_db_session_space_usage-transact-sql"></a>sys.dm_db_session_space_usage (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает число страниц, выделенных и освобожденных для каждого сеанса базы данных.  
  
> [!NOTE]  
>  Это представление применимо только к [базе данных tempdb](../../relational-databases/databases/tempdb-database.md).  
  
> [!NOTE]  
>  Чтобы вызвать эту функцию [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] из [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]или, используйте имя **sys. dm_pdw_nodes_db_session_space_usage**.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**session_id**|**smallint**|Идентификатор сеанса.<br /><br /> **session_id** сопоставляется с **session_id** в [sys. dm_exec_sessions](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql.md).|  
|**database_id**|**smallint**|Идентификатор базы данных.|  
|**user_objects_alloc_page_count**|**bigint**|Число страниц, зарезервированных или выделенных для пользовательских объектов в данном сеансе.|  
|**user_objects_dealloc_page_count**|**bigint**|Число страниц, освобожденных пользовательскими объектами или более не зарезервированных для них в данном сеансе.|  
|**internal_objects_alloc_page_count**|**bigint**|Число страниц, зарезервированных или выделенных для внутренних объектов в данном сеансе.|  
|**internal_objects_dealloc_page_count**|**bigint**|Число страниц, освобожденных внутренними объектами или более не зарезервированных для них в данном сеансе.|  
|**user_objects_deferred_dealloc_page_count**|**bigint**|Количество страниц, помеченных для отложенного освобождения.<br /><br /> **Примечание.** Представлено в пакетах [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] обновления [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]для и.|  
|**pdw_node_id**|**int**|**Применимо к**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)],[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Идентификатор узла, на котором находится данное распределение.|  
  
## <a name="permissions"></a>Разрешения  

В [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]необходимо `VIEW SERVER STATE` разрешение.   
На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] уровнях Premium требуется `VIEW DATABASE STATE` разрешение в базе данных. На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] уровнях Standard и Basic требуется **Администратор сервера** или учетная запись **администратора Azure Active Directory** .   

## <a name="remarks"></a>Remarks  
 В этом представлении при подсчете выделенных и освобожденных страниц IAM-страницы не учитываются.  
  
 В начале сеанса счетчики страниц устанавливаются в ноль (0). Счетчики отслеживают общее число страниц, выделенных и освобожденных для уже завершенных в этом сеансе задач. Счетчики обновляются только при завершении задачи; они не отражают состояние выполняющихся задач.  
  
 В каждый момент времени у сеанса может быть несколько запросов. Запрос может создавать несколько потоков и задач, если это параллельный запрос к базе данных.  
  
 Дополнительные сведения о сеансах, запросах и задачах см. в разделе [sys. dm_exec_sessions &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql.md), [sys. dm_exec_requests &#40;transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)и [sys. dm_os_tasks &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-tasks-transact-sql.md).  
  
## <a name="user-objects"></a>Пользовательские объекты  
 Следующие объекты включаются в счетчики страниц пользовательских объектов.  
  
-   Пользовательские таблицы и индексы  
  
-   Системные таблицы и индексы  
  
-   Глобальные временные таблицы и индексы  
  
-   Локальные временные таблицы и индексы  
  
-   Переменные таблицы  
  
-   Таблицы, возвращаемые в функциях с табличным значением  
  
## <a name="internal-objects"></a>Внутренние объекты  
 Внутренние объекты доступны только в **базе данных tempdb**. Следующие объекты включаются в счетчики страниц внутренних объектов:  
  
-   рабочие таблицы для выполнения операций с курсорами и буферами, а также для хранения временных больших объектов (LOB);  
  
-   рабочие файлы для таких операций, как хэш-соединение  
  
-   Сортировки  
  
## <a name="physical-joins"></a>Физические соединения  
 ![Физические соединения для sys.dm_db_session_space_usage](../../relational-databases/system-dynamic-management-views/media/join-dm-db-session-space-usage-1.gif "Физические соединения для sys.dm_db_session_space_usage")  
  
## <a name="relationship-cardinalities"></a>Количество элементов связей  
  
|С|Кому|Связь|  
|----------|--------|------------------|  
|dm_db_session_space_usage.session_id|dm_exec_sessions.session_id|Один к одному|  
  
## <a name="see-also"></a>См. также:  
 [Динамические административные представления и функции (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Динамические административные представления, связанные с базами данных &#40;&#41;Transact-SQL](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)   
 [sys. dm_exec_sessions &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql.md)   
 [sys. dm_exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)   
 [sys. dm_os_tasks &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-tasks-transact-sql.md)   
 [sys. dm_db_task_space_usage &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-task-space-usage-transact-sql.md)   
 [sys. dm_db_file_space_usage &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-file-space-usage-transact-sql.md)  
  
  



