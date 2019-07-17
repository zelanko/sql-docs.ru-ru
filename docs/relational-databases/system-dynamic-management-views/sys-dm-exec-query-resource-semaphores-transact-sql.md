---
title: sys.dm_exec_query_resource_semaphores (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_exec_query_resource_semaphores_TSQL
- dm_exec_query_resource_semaphores_TSQL
- sys.dm_exec_query_resource_semaphores
- dm_exec_query_resource_semaphores
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_query_resource_semaphores dynamic management view
ms.assetid: e43a2aa9-dd52-4c89-911e-1a7d05f7ffbb
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 026c13a461d6b4efe7244a08a9f3cdbe117deee9
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/16/2019
ms.locfileid: "68255286"
---
# <a name="sysdmexecqueryresourcesemaphores-transact-sql"></a>sys.dm_exec_query_resource_semaphores (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает сведения о текущем состоянии семафора запроса-ресурса в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. **sys.dm_exec_query_resource_semaphores** содержит состояние памяти выполнения общего запроса и позволяет определить ли доступ к системе недостаточно памяти. Данное представление дополняет сведения о памяти, полученные из [sys.dm_os_memory_clerks](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-clerks-transact-sql.md) для получения полной картины состояния памяти сервера. **sys.dm_exec_query_resource_semaphores** возвращает одну строку для обычного семафора ресурса, а другой для семафора ресурса малого запроса. Существует два требования для семафора малого запроса.  
  
-   Запрошенный объема выделенной памяти должно быть меньше 5 МБ  
  
-   Стоимость запроса должно быть меньше, чем 3 стоимость единицы  
  
> [!NOTE]  
>  Вызывать его из [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] или [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], используйте имя **sys.dm_pdw_nodes_exec_query_resource_semaphores**.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**resource_semaphore_id**|**smallint**|Неуникальный идентификатор семафора ресурса. 0 для обычного семафора ресурса и 1 для семафора ресурса малого запроса.|  
|**target_memory_kb**|**bigint**|Предоставляет использование назначения в килобайтах.|  
|**max_target_memory_kb**|**bigint**|Максимально возможное назначение в килобайтах. Значение NULL для семафора ресурса малого запроса.|  
|**total_memory_kb**|**bigint**|Объем памяти, занимаемый семафором ресурса в килобайтах. Если система испытывает недостаток памяти или принудительный минимальный объем памяти выделяется часто, это значение может быть больше, чем **target_memory_kb** или **max_target_memory_kb** значения. Общий объем памяти — это сумма объемов доступной и выделенной памяти.|  
|**available_memory_kb**|**bigint**|Объем памяти, доступный для нового выделения в килобайтах.|  
|**granted_memory_kb**|**bigint**|Общий объем выделенной памяти.|  
|**used_memory_kb**|**bigint**|Физически используемая часть объема выделенной памяти в килобайтах.|  
|**grantee_count**|**int**|Количество активных запросов, необходимых для выделения.|  
|**waiter_count**|**int**|Количество запросов, ожидающих предоставлений, которые будут удовлетворены.|  
|**timeout_error_count**|**bigint**|Общее количество ошибок времени ожидания с момента запуска сервера. Значение NULL для семафора ресурса малого запроса.|  
|**forced_grant_count**|**bigint**|Общее количество минимальных принудительных предоставлений памяти с момента запуска сервера. Значение NULL для семафора ресурса малого запроса.|  
|**pool_id**|**int**|Идентификатор пула ресурсов, к которому принадлежит данный семафор ресурса.|  
|**pdw_node_id**|**int**|**Применяется к**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Идентификатор для узла, это распределение является на.|  
  
## <a name="permissions"></a>Разрешения  

На [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], требуется `VIEW SERVER STATE` разрешение.   
На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] уровней Premium необходимо `VIEW DATABASE STATE` разрешение в базе данных. На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] уровней Standard и Basic, требует **администратора сервера** или **администратор Azure Active Directory** учетной записи.   
  
## <a name="remarks"></a>Примечания  
 Запросы, использующие динамические административные представления, которые содержат предложение ORDER BY или статистические функции, могут увеличить потребление памяти и таким образом устранить неполадки.  
  
 Используйте **sys.dm_exec_query_resource_semaphores** для устранения неполадок, но не включайте его в приложениях, которые будут использоваться в будущих версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Регулятор ресурсов позволяет администратору базы данных распределять ресурсы сервера между пулами ресурсов, используя до 64 пулов. В [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] и более поздних версиях каждый пул ведет себя как небольшой независимый экземпляр сервера и требует двух семафоров.  
  
## <a name="see-also"></a>См. также  
 [Динамические административные представления и функции, связанные с выполнением &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)   
 [sys.dm_exec_query_memory_grants (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-memory-grants-transact-sql.md)  
  
  


