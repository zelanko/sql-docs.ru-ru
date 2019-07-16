---
title: sys.dm_geo_replication_link_status (база данных SQL Azure) | Документация Майкрософт
ms.custom: ''
ms.date: 01/28/2019
ms.service: sql-database
ms.reviewer: ''
ms.topic: conceptual
f1_keywords:
- dm_geo_replication_link_status
- dm_geo_replication_link_status_TSQL
- sys.dm_geo_replication_link_status
- sys.dm_geo_replication_link_status_TSQL
helpviewer_keywords:
- dm_geo_replication_link_status dynamic management view
- sys.dm_geo_replication_link_status dynamic management view
ms.assetid: d763d679-470a-4c21-86ab-dfe98d37e9fd
author: mashamsft
ms.author: mathoma
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 8302de76b45ca09e86c87c29ab99c30898168de5
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67900888"
---
# <a name="sysdmgeoreplicationlinkstatus-azure-sql-database"></a>sys.dm_geo_replication_link_status (база данных SQL Azure)

[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Содержит по строке на каждый канал репликации между первичной и вторичной базы данных в партнерстве георепликации. Это касается первичных и вторичных баз данных. Если для заданной базы данных-источника существует более одной связи непрерывной репликации, эта таблица содержит по одной строке для каждого из отношений. Во всех базах данных, включая логической базе данных master создается представление. Однако запрос этого представления для логической базы данных master возвращает пустой набор.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|link_guid|**uniqueidentifier**|Уникальный идентификатор канала репликации.|  
|partner_server|**sysname**|Имя сервера базы данных SQL, содержащего связанной базы данных.|  
|partner_database|**sysname**|Имя связанной базы данных на связанном сервере базы данных SQL.|  
|last_replication|**datetimeoffset**|Отметка времени последней транзакции подтверждения вторичным в формате базы данных-источника. Это значение доступно только основной базы данных.|  
|replication_lag_sec|**int**|Разница во времени в секундах между last_replication и меткой времени фиксации этой транзакции на сервере-источнике, в формате базы данных-источника.  Это значение доступно только основной базы данных.|  
|replication_state|**tinyint**|Состояние географической репликации для этой базы данных, один из:.<br /><br /> 1 = заполнение. Георепликация целевой объект заполняется, но еще не синхронизированы две базы данных. До завершения первоначального заполнения, не удается подключиться к базе данных-получателе. Удаление базы данных-получателя из основного отменит операции заполнения.<br /><br /> 2 = захват. База данных-получатель находится в состоянии транзакционной согласованности и постоянно синхронизируются с базы данных-источника.<br /><br /> 4 = Suspended. Это неактивная связь непрерывного копирования. Это состояние обычно означает, что доступной для Interlink полосы пропускания недостаточно для уровня активности транзакций в базе данных-источнике. Однако связь непрерывного копирования не повреждена.|  
|replication_state_desc|**nvarchar(256)**|PENDING<br /><br /> SEEDING<br /><br /> CATCH_UP|  
|role|**tinyint**|Роль георепликации, один из:<br /><br /> 0 = primary. Database_id относится к базе данных источнику в партнерстве георепликации.<br /><br /> 1 = вторичный.  Database_id относится к базе данных источнику в партнерстве георепликации.|  
|role_desc|**nvarchar(256)**|PRIMARY<br /><br /> SECONDARY|  
|secondary_allow_connections|**tinyint**|Тип вторичного, один из:<br /><br /> 0 = не должно быть прямых подключений к базе данных-получателе и базе данных не доступен для доступа на чтение.<br /><br /> 2 = all подключений к базе данных в дополнительный repl; йлы приложения для доступа только для чтения.|  
|secondary_allow_connections_desc|**nvarchar(256)**|Нет<br /><br /> All|  
|last_commit|**datetimeoffset**|Время последней транзакции, фиксируются в базе данных. Если извлечь базы данных-источника, он показывает время последней фиксации базы данных-источника. Если извлечь на базе данных-получателе, указывает время последней фиксации в базе данных-получателе. Если извлечены в базе данных-получателе при первичной канала репликации не работает, это значит, пока не достигает какой момент вторичной реплике.|
  
> [!NOTE]  
>  Если отношение репликации завершается путем удаления базы данных-получателя (раздел 4.2), строки для этой базы данных в **sys.dm_geo_replication_link_status** представление исчезает.  
  
## <a name="permissions"></a>Разрешения  
 Можно запрашивать любую учетную запись с разрешением view_database_state **sys.dm_geo_replication_link_status**.  
  
## <a name="example"></a>Пример  
 Показать задержек репликации и время последней репликации из моей базы данных-получатели.  
  
```  
SELECT   
     link_guid  
   , partner_server  
   , last_replication  
   , replication_lag_sec   
FROM sys.dm_geo_replication_link_status;  
```  
  
## <a name="see-also"></a>См. также  
 [ALTER DATABASE &#40;база данных Azure SQL&#41;](../../t-sql/statements/alter-database-azure-sql-database.md)   
 [sys.geo_replication_links &#40;базы данных SQL Azure&#41;](../../relational-databases/system-dynamic-management-views/sys-geo-replication-links-azure-sql-database.md)   
 [sys.dm_operation_status &#40;базы данных SQL Azure&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-operation-status-azure-sql-database.md)  
  
  
