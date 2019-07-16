---
title: sys.dm_os_waiting_tasks (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/13/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_os_waiting_tasks
- sys.dm_os_waiting_tasks_TSQL
- dm_os_waiting_tasks_TSQL
- sys.dm_os_waiting_tasks
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_waiting_tasks dynamic management view
ms.assetid: ca5e6844-368c-42e2-b187-6e5f5afc8df3
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: f6ce0fa8270a05d8c3385cbc7b5c25edeaa84bc5
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67899637"
---
# <a name="sysdmoswaitingtasks-transact-sql"></a>sys.dm_os_waiting_tasks (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает сведения об очереди задач, ожидающих освобождения определенного ресурса.  
  
> [!NOTE]  
>  Вызывать его из [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] или [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], используйте имя **sys.dm_pdw_nodes_os_waiting_tasks**.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**waiting_task_address**|**varbinary(8)**|Адрес ожидающей задачи.|  
|**session_id**|**smallint**|Идентификатор сеанса, связанного с этой задачей.|  
|**exec_context_id**|**int**|Идентификатор контекста выполнения, связанного с этой задачей.|  
|**wait_duration_ms**|**bigint**|Общее время ожидания для этого типа ожиданий в миллисекундах. Это время **signal_wait_time**.|  
|**wait_type**|**nvarchar(60)**|Имя типа ожидания.|  
|**resource_address**|**varbinary(8)**|Адрес ресурса, освобождения которого ожидает задача.|  
|**blocking_task_address**|**varbinary(8)**|Задача, которая в настоящий момент блокирует этот ресурс.|  
|**blocking_session_id**|**smallint**|Идентификатор сеанса, блокирующего данный запрос. Если этот столбец содержит значение NULL, то запрос не блокирован или сведения о сеансе блокировки недоступны (или не могут быть идентифицированы).<br /><br /> -2 = Блокирующий ресурс принадлежит потерянной распределенной транзакции.<br /><br /> -3 = Блокирующий ресурс принадлежит отложенной транзакции восстановления.<br /><br /> -4 = Идентификатор сеанса владельца кратковременной блокировки не может быть определен из-за внутренних переходов состояния кратковременной блокировки.|  
|**blocking_exec_context_id**|**int**|Идентификатор контекста выполнения блокирующей задачи.|  
|**resource_description**|**nvarchar(3072)**|Описание используемого ресурса. Дополнительные сведения см. в приведенном ниже списке.|  
|**pdw_node_id**|**int**|**Применяется к**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Идентификатор для узла, это распределение является на.|  
  
## <a name="resourcedescription-column"></a>Столбец resource_description  
 Столбец resource_description имеет следующие возможные значения.  
  
 **Владелец ресурса пула потоков:**  
  
-   threadpool id=scheduler\<hex-address>  
  
 **Владелец ресурса параллельного запроса:**  
  
-   exchangeEvent id = {порта | Канал}\<hex-address > WaitType =\<exchange-wait-type > nodeId =\<exchange узел id >  
  
 **Exchange-wait-type:**  
  
-   e_waitNone  
  
-   e_waitPipeNewRow  
  
-   e_waitPipeGetRow  
  
-   e_waitSynchronizeConsumerOpen  
  
-   e_waitPortOpen  
  
-   e_waitPortClose  
  
-   e_waitRange  
  
 **Владелец ресурса блокировки:**  
  
-   \<Тип specific-description > id = блокировка\<блокировки hex-address > режим =\<режим > associatedObjectId =\<связанные obj-id >  
  
     **\<Тип specific-description > может быть:**  
  
    -   Для DATABASE: Databaselock subresource =\<databaselock-subresource > dbid =\<db-id >  
  
    -   Для FILE: Filelock fileid =\<файл id > subresource =\<filelock-subresource > dbid =\<db-id >  
  
    -   Для OBJECT: Objectlock lockPartition =\<lock-partition-id > objid =\<obj-id > subresource =\<objectlock-subresource > dbid =\<db-id >  
  
    -   Для PAGE: Pagelock fileid =\<файл id > pageid =\<страницы id > dbid =\<db-id > subresource =\<pagelock-subresource >  
  
    -   Для ключа: Keylock hobtid =\<hobt-id > dbid =\<db-id >  
  
    -   Для EXTENT: Extentlock fileid =\<файл id > pageid =\<страницы id > dbid =\<db-id >  
  
    -   Для RID: Ridlock fileid =\<файл id > pageid =\<страницы id > dbid =\<db-id >  
  
    -   Для APPLICATION: Applicationlock hash =\<hash > databasePrincipalId =\<роли id > dbid =\<db-id >  
  
    -   Для METADATA: Metadatalock subresource =\<метаданных subresource > classid =\<metadatalock-description > dbid =\<db-id >  
  
    -   Для HOBT: Hobtlock hobtid =\<hobt-id > subresource =\<hobt-subresource > dbid =\<db-id >  
  
    -   Для ALLOCATION_UNIT: Allocunitlock hobtid =\<hobt-id > subresource =\<alloc-unit-subresource > dbid =\<db-id >  
  
     **\<Режим > может быть:**  
  
     Sch-S, Sch-M, S, U, X, IS, IU, IX, SIU, SIX, UIX, BU, RangeS-S, RangeS-U, RangeI-N, RangeI-S, RangeI-U, RangeI-X, RangeX-, RangeX-U, RangeX-X  
  
 **Владелец внешнего ресурса:**  
  
-   Внешние ExternalResource =\<тип ожидания >  
  
 **Владелец универсального ресурса:**  
  
-   Рабочая область TransactionInfo TransactionMutex =\<идентификатор рабочей области >  
  
-   Mutex  
  
-   CLRTaskJoin  
  
-   CLRMonitorEvent  
  
-   CLRRWLockEvent  
  
-   resourceWait  
  
 **Владелец ресурса кратковременной блокировки:**  
  
-   \<DB-id >:\<файл id >:\<в файл подкачки >  
  
-   \<ИДЕНТИФИКАТОР GUID >  
  
-   \<Класс кратковременных блокировок > (\<кратковременной блокировки address >)  
  
## <a name="permissions"></a>Разрешения

На [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], требуется `VIEW SERVER STATE` разрешение.   
В [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] необходимо разрешение `VIEW DATABASE STATE` для базы данных.   
 
## <a name="example"></a>Пример
В этом примере будет идентифицировать заблокированных сеансов.  Выполнение [!INCLUDE[tsql](../../includes/tsql-md.md)] запроса в [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].
```sql
SELECT * FROM sys.dm_os_waiting_tasks 
WHERE blocking_session_id IS NOT NULL; 
``` 
  
## <a name="see-also"></a>См. также  
  [Динамические административные представления, относящиеся к операционной системе SQL Server &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  


