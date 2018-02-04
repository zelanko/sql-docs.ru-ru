---
title: "sys.dm_geo_replication_link_status (база данных SQL Azure) | Документы Microsoft"
ms.custom: 
ms.date: 10/13/2016
ms.prod: 
ms.prod_service: sql-database
ms.reviewer: 
ms.service: sql-database
ms.component: dmv's
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- dm_geo_replication_link_status
- dm_geo_replication_link_status_TSQL
- sys.dm_geo_replication_link_status
- sys.dm_geo_replication_link_status_TSQL
helpviewer_keywords:
- dm_geo_replication_link_status dynamic management view
- sys.dm_geo_replication_link_status dynamic management view
ms.assetid: d763d679-470a-4c21-86ab-dfe98d37e9fd
caps.latest.revision: 
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 37bb0b6c2252a213824e24c51178711a704d2e85
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/03/2018
---
# <a name="sysdmgeoreplicationlinkstatus-azure-sql-database"></a>sys.dm_geo_replication_link_status (база данных SQL Azure)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Содержит по строке на каждый канал репликации между первичной и вторичной базы данных в связи георепликации. Это касается первичных и вторичных баз данных. Если для заданной базы данных-источника существует более одной связи с непрерывной репликацией, эта таблица содержит по одной строке для каждой связи. Во всех базах данных, включая логической базе данных master создается представление. Однако запрос этого представления для логической базы данных master возвращает пустой набор.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|link_guid|**uniqueidentifier**|Уникальный идентификатор канала репликации.|  
|partner_server|**sysname**|Имя логического сервера, содержащего связанной базы данных.|  
|partner_database|**sysname**|Имя связанной базы данных на связанном сервере логических.|  
|last_replication|**datetimeoffset**|Отметка времени последней транзакции подтверждения вторичным в формате базы данных-источника. Это значение доступно только основной базе данных.|  
|replication_lag_sec|**int**|Разница во времени в секундах между значением last_replication и отметки времени фиксации этой транзакции на сервере-источнике в формате базы данных-источника.  Это значение доступно только основной базе данных.|  
|replication_state|**tinyint**|Состояние географической репликации для этой базы данных, один из:.<br /><br /> 1 = заполнение. Географическую репликацию данных в целевой объект заполняется, но еще не синхронизированы двух баз данных. До завершения первоначального заполнения не удается подключиться к базе данных-получателей. Удаление баз данных-получателей с сервера-источника будет отменить присвоение начальных значений.<br /><br /> 2 = захват. База данных-получатель находится в состоянии транзакционно согласованной и постоянно синхронизируются с базой данных-источником.<br /><br /> 4 = Suspended. Это неактивная связь непрерывного копирования. Это состояние обычно означает, что доступной для Interlink полосы пропускания недостаточно для уровня активности транзакций в базе данных-источнике. Однако связь непрерывного копирования не повреждена.|  
|replication_state_desc|**nvarchar(256)**|PENDING<br /><br /> SEEDING<br /><br /> CATCH_UP|  
|роль|**tinyint**|Роль георепликации, один из:<br /><br /> 0 = primary. Database_id ссылается на базы данных-источника в партнерстве географической репликации.<br /><br /> 1 = получателя.  Database_id ссылается на базы данных-источника в партнерстве географической репликации.|  
|role_desc|**nvarchar(256)**|PRIMARY<br /><br /> SECONDARY|  
|secondary_allow_connections|**tinyint**|Вторичный тип, один из:<br /><br /> 0 = нет прямых подключений базы данных-получателя и базы данных не разрешен доступ для чтения.<br /><br /> 2 = all подключений к базе данных в дополнительный repl; приложений для доступа только для чтения.|  
|secondary_allow_connections_desc|**nvarchar(256)**|нет<br /><br /> все|  
|last_commit|**datetimeoffset**|Время последней транзакции фиксируются в базе данных. Если извлечение базы данных-источника, он показывает время последней фиксации базы данных-источника. Если извлечение на базу данных-получатель, он показывает время последней фиксации на базу данных-получатель. Если получены на базу данных-получатель, если основной канала репликации не работает, это означает, что пока какой момент сервер-получатель устранил отставание.|
  
> [!NOTE]  
>  Если связь репликации прерывается путем удаления базы данных-получателя (раздел 4.2), строки для этой базы данных в **sys.dm_geo_replication_link_status** представление исчезает.  
  
## <a name="permissions"></a>Разрешения  
 Можно запросить любой учетной записи с разрешением view_database_state **sys.dm_geo_replication_link_status**.  
  
## <a name="example"></a>Пример  
 Показать задержки репликации и времени последнего репликации моих баз данных-получателей.  
  
```  
SELECT   
     link_guid  
   , partner_server  
   , last_replication  
   , replication_lag_sec   
FROM sys.dm_geo_replication_link_status;  
```  
  
## <a name="see-also"></a>См. также  
 [ALTER DATABASE &#40; База данных Azure SQL &#41;](../../t-sql/statements/alter-database-azure-sql-database.md)   
 [sys.geo_replication_links &#40; База данных Azure SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-geo-replication-links-azure-sql-database.md)   
 [sys.dm_operation_status &#40; База данных Azure SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-operation-status-azure-sql-database.md)  
  
  
