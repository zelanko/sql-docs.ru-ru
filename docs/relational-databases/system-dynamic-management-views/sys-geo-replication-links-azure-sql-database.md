---
title: sys.geo_replication_links (база данных SQL Azure) | Документы Microsoft
ms.custom: ''
ms.date: 10/18/2016
ms.prod: ''
ms.prod_service: sql-database
ms.reviewer: ''
ms.service: sql-database
ms.component: dmv's
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- dm_geo_replication_links_TSQL
- dm_geo_replication_links
- sys.dm_geo_replication_links
- sys.dm_geo_replication_links_TSQL
helpviewer_keywords:
- sys.dm_geo_replication_links dynamic management view
- dm_geo_replication_links dynamic management view
ms.assetid: 58911798-1d60-4f28-87ab-2def2bfc3de7
caps.latest.revision: 14
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 3c8665b7371e1287df8bec1dcee8cd1faf057e31
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="sysgeoreplicationlinks-azure-sql-database"></a>sys.geo_replication_links (база данных SQL Azure)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Содержит по строке на каждый канал репликации между первичной и вторичной базы данных в связи георепликации. Данное представление находится в логической базе данных master.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|database_id|**int**|Идентификатор текущей базы данных в представлении sys.databases.|  
|start_date|**datetimeoffset**|Время в формате UTC в региональном центре данных базы данных SQL инициации репликации базы данных|  
|modify_date|**datetimeoffset**|Время в формате UTC в региональном центре данных базы данных SQL при завершении георепликация баз данных. Новая база данных синхронизирована с основной базой данных на этот момент времени. .|  
|link_guid|**uniqueidentifier**|Уникальный идентификатор связи георепликации.|  
|partner_server|**sysname**|Имя логического сервера, содержащего базу данных, географически реплицируются.|  
|partner_database|**sysname**|Имя базы данных, географически реплицируются на связанном сервере логических.|  
|replication_state|**tinyint**|Состояние географической репликации для этой базы данных, один из:.<br /><br /> 0 = ожидает согласования. Создание активной базы данных-получателя запланировано, но необходимые действия по подготовке еще не завершены.<br /><br /> 1 = заполнение. Географическую репликацию данных в целевой объект заполняется, но еще не синхронизированы двух баз данных. До завершения первоначального заполнения не удается подключиться к базе данных-получателей. Удаление баз данных-получателей с сервера-источника будет отменить присвоение начальных значений.<br /><br /> 2 = захват. База данных-получатель находится в состоянии транзакционно согласованной и постоянно синхронизируются с базой данных-источником.|  
|replication_state_desc|**nvarchar(256)**|PENDING<br /><br /> SEEDING<br /><br /> CATCH_UP|  
|роль|**tinyint**|Роль георепликации, один из:<br /><br /> 0 = primary. Database_id ссылается на базы данных-источника в партнерстве географической репликации.<br /><br /> 1 = получателя.  Database_id ссылается на базы данных-источника в партнерстве географической репликации.|  
|role_desc|**nvarchar(256)**|PRIMARY<br /><br /> SECONDARY|  
|secondary_allow_connections|**tinyint**|Вторичный тип, один из:<br /><br /> 0 = Нет. База данных-получатель до перехода на другой ресурс недоступен.<br /><br /> 1 = только для чтения. База данных-получатель доступен только для клиентских подключений с ApplicationIntent = ReadOnly.<br /><br /> 2= все. База данных-получатель доступен для любого клиентского соединения.|  
|secondary_allow_connections _desc|**nvarchar(256)**|Нет<br /><br /> все<br /><br /> Только для чтения|  
  
## <a name="permissions"></a>Разрешения  
 Это представление доступно только в **master** базы данных для имени входа субъекта серверного уровня.  
  
## <a name="example"></a>Пример  
 Показать все базы данных со ссылками на георепликацию.  
  
```  
SELECT   
     database_id  
   , start_date  
   , partner_server  
   , partner_database  
   , replication_state  
   , role_desc  
   , secondary_allow_connections_desc   
FROM sys.geo_replication_links;  
```  
  
## <a name="see-also"></a>См. также  
 [CREATE DATABASE (база данных SQL Azure)](../../t-sql/statements/alter-database-azure-sql-database.md)   
 [sys.dm_geo_replication_link_status &#40;базы данных SQL Azure&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-geo-replication-link-status-azure-sql-database.md)   
 [sys.dm_operation_status &#40;базы данных SQL Azure&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-operation-status-azure-sql-database.md)  
  
  
