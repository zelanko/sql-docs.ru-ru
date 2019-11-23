---
title: sys. dm_os_waiting_tasks (Transact-SQL) | Документация Майкрософт
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
ms.openlocfilehash: c0a89a48fa960812ee955cd3b7ecb30069161f61
ms.sourcegitcommit: aece9f7db367098fcc0c508209ba243e05547fe1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/11/2019
ms.locfileid: "72260377"
---
# <a name="sysdm_os_waiting_tasks-transact-sql"></a>sys.dm_os_waiting_tasks (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает сведения об очереди задач, ожидающих освобождения определенного ресурса. Дополнительные сведения о задачах см. в разделе [руководств по архитектуре потоков и задач](../../relational-databases/thread-and-task-architecture-guide.md).
   
> [!NOTE]  
>  Чтобы вызвать это из [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] или [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], используйте имя **sys. dm_pdw_nodes_os_waiting_tasks**.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**waiting_task_address**|**varbinary (8)**|Адрес ожидающей задачи.|  
|**session_id**|**smallint**|Идентификатор сеанса, связанного с этой задачей.|  
|**exec_context_id**|**int**|Идентификатор контекста выполнения, связанного с этой задачей.|  
|**wait_duration_ms**|**bigint**|Общее время ожидания для этого типа ожиданий в миллисекундах. Это время является инклюзивным **signal_wait_time**.|  
|**wait_type**|**nvarchar(60)**|Имя типа ожидания.|  
|**resource_address**|**varbinary (8)**|Адрес ресурса, освобождения которого ожидает задача.|  
|**blocking_task_address**|**varbinary (8)**|Задача, которая в настоящий момент блокирует этот ресурс.|  
|**blocking_session_id**|**smallint**|Идентификатор сеанса, блокирующего данный запрос. Если этот столбец содержит значение NULL, то запрос не блокирован или сведения о сеансе блокировки недоступны (или не могут быть идентифицированы).<br /><br /> -2 = Блокирующий ресурс принадлежит потерянной распределенной транзакции.<br /><br /> -3 = Блокирующий ресурс принадлежит отложенной транзакции восстановления.<br /><br /> -4 = Идентификатор сеанса владельца кратковременной блокировки не может быть определен из-за внутренних переходов состояния кратковременной блокировки.|  
|**blocking_exec_context_id**|**int**|Идентификатор контекста выполнения блокирующей задачи.|  
|**resource_description**|**nvarchar (3072)**|Описание используемого ресурса. Дополнительные сведения см. в приведенном ниже списке.|  
|**pdw_node_id**|**int**|**Применимо к**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Идентификатор узла, на котором находится данное распределение.|  
  
## <a name="resource_description-column"></a>Столбец resource_description  
 Столбец resource_description имеет следующие возможные значения.  
  
 **Владелец ресурса пула потоков:**  
  
-   threadpool id=scheduler\<hex-address>  
  
 **Владелец ресурса параллельных запросов:**  
  
-   Ексчанжеевент ID = {порт | Pipe}\<шестнадцатеричный адрес > столбцы waittype =\<Exchange-Wait-Type > nodeId =\<сервер Exchange-node-ID >  
  
 **Тип ожидания Exchange:**  
  
-   e_waitNone  
  
-   e_waitPipeNewRow  
  
-   e_waitPipeGetRow  
  
-   e_waitSynchronizeConsumerOpen  
  
-   e_waitPortOpen  
  
-   e_waitPortClose  
  
-   e_waitRange  
  
 **Владелец ресурса блокировки:**  
  
-   \<тип-описание > ID = блокировка\<Lock-Hex-address > Mode =\<Mode > АссоЦиатедобжектид =\<связанный-obj-ID >  
  
     **\<> описания типа могут иметь следующие особенности:**  
  
    -   Для базы данных: databaselock подресурс =\<databaselock-Resource > DBID =\<DB-ID >  
  
    -   Для файла: FileLock ИД =\<файл-ID > подресурсе =\<FileLock-Resource > DBID =\<DB-ID >  
  
    -   Для объекта: objectlock Локкпартитион =\<Lock-Partition-ID > ObjId =\<obj-ID > подресурсе =\<objectlock-Resource > DBID =\<DB-ID >  
  
    -   Для страницы: пажелокк ИД файла =\<файл-ID > идентификатор страницы =\<Page-ID > DBID =\<DB-ID > подресурсе =\<пажелокк-Resource >  
  
    -   Для ключа: кэйлокк хобтид =\<HoBT-ID > DBID =\<DB-ID >  
  
    -   Для ЭКСТЕНТа: екстентлокк ИД =\<файл с идентификатором > идентификатор страницы =\<Page-ID > DBID =\<DB-ID >  
  
    -   Для RID: ридлокк ИД файла =\<файл-ID > идентификатор страницы =\<Page-ID > DBID =\<DB-ID >  
  
    -   Для приложения: аппликатионлокк hash =\<хэш > ДатабасепринЦипалид =\<Role-ID > DBID =\<DB-ID >  
  
    -   Для МЕТАДАННЫХ: metadatalock подресурс =\<метаданные — подресурс > ClassID =\<metadatalock-Description > DBID =\<DB-ID >  
  
    -   Для HOBT: хобтлокк хобтид =\<HoBT-ID > подресурсе =\<HoBT-Resource > DBID =\<DB-ID >  
  
    -   Для ALLOCATION_UNIT: аллокунитлокк хобтид =\<HoBT-ID > подресурс =\<Alloc-Unit-a > DBID =\<DB-ID >  
  
     **\<режим > может быть следующим:**  
  
     Sch-S, Sch-M, S, U, X, IS, IU, IX, SIU, SIX, UIX, BU, RangeS-S, RangeS-U, RangeI-N, RangeI-S, RangeI-U, RangeI-X, RangeX-, RangeX-U, RangeX-X  
  
 **Владелец внешнего ресурса:**  
  
-   External Екстерналресаурце =\<тип ожидания >  
  
 **Универсальный владелец ресурса:**  
  
-   Трансактионмутекс Трансактионинфо Workspace =\<Рабочая область — идентификатор >  
  
-   Mutex  
  
-   CLRTaskJoin  
  
-   CLRMonitorEvent  
  
-   CLRRWLockEvent  
  
-   resourceWait  
  
 **Владелец ресурса кратковременной блокировки:**  
  
-   \<DB-ID >:\<файл идентификатор >:\<страница в файле >  
  
-   \<GUID >  
  
-   \<> класса кратковременных блокировок (\<кратковременной блокировки адреса >)  
  
## <a name="permissions"></a>Разрешения

На [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]требуется `VIEW SERVER STATE` разрешение.   
На уровнях [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] Premium требуется разрешение `VIEW DATABASE STATE` в базе данных. На уровнях [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] Standard и Basic требуется **Администратор сервера** или учетная запись **администратора Azure Active Directory** .   
 
## <a name="example"></a>Пример
В этом примере будут определены заблокированные сеансы. Выполните запрос [!INCLUDE[tsql](../../includes/tsql-md.md)] в [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].

```sql
SELECT * FROM sys.dm_os_waiting_tasks 
WHERE blocking_session_id IS NOT NULL; 
``` 
  
## <a name="see-also"></a>См. также статью  
[SQL Server динамическое представление &#40;управления, связанное с операционной&#41; системой,     Transact-SQL](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
[Руководство по архитектуре потоков и задач](../../relational-databases/thread-and-task-architecture-guide.md)     
   
 
