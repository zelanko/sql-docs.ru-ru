---
title: sys.geo_replication_links (база данных SQL Azure) | Документация Майкрософт
ms.custom: ''
ms.date: 10/18/2016
ms.prod: ''
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: system-objects
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
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 6b37ca384c2d3402a3b9ec01a4b9d6ccbfb7d402
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47610114"
---
# <a name="sysgeoreplicationlinks-azure-sql-database"></a>sys.geo_replication_links (база данных SQL Azure)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Содержит по строке на каждый канал репликации между первичной и вторичной базы данных в партнерстве георепликации. Данное представление находится в логической базе данных master.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|database_id|**int**|Идентификатор текущей базы данных в представлении sys.databases.|  
|start_date|**datetimeoffset**|Время в формате UTC в региональном центре данных базы данных SQL при репликации базы данных была начата|  
|modify_date|**datetimeoffset**|Время в формате UTC в региональном центре данных базы данных SQL после завершения георепликации базы данных. Новая база данных синхронизируется с базы данных-источника на этот момент времени. .|  
|link_guid|**uniqueidentifier**|Уникальный идентификатор связи георепликации.|  
|partner_server|**sysname**|Имя логического сервера, содержащего геореплицированную базу данных.|  
|partner_database|**sysname**|Имя геореплицированную базу данных на связанном сервере логических.|  
|replication_state|**tinyint**|Состояние географической репликации для этой базы данных, один из:.<br /><br /> 0 = ожидает согласования. Создание активной базы данных-получателя запланировано, но необходимые действия по подготовке еще не завершены.<br /><br /> 1 = заполнение. Георепликация целевой объект заполняется, но еще не синхронизированы две базы данных. До завершения первоначального заполнения, не удается подключиться к базе данных-получателе. Удаление базы данных-получателя из основного отменит операции заполнения.<br /><br /> 2 = захват. База данных-получатель находится в состоянии транзакционной согласованности и постоянно синхронизируются с базы данных-источника.|  
|replication_state_desc|**nvarchar(256)**|PENDING<br /><br /> SEEDING<br /><br /> CATCH_UP|  
|роль|**tinyint**|Роль георепликации, один из:<br /><br /> 0 = primary. Database_id относится к базе данных источнику в партнерстве георепликации.<br /><br /> 1 = вторичный.  Database_id относится к базе данных источнику в партнерстве георепликации.|  
|role_desc|**nvarchar(256)**|PRIMARY<br /><br /> SECONDARY|  
|secondary_allow_connections|**tinyint**|Тип вторичного, один из:<br /><br /> 0 = Нет. База данных-получатель недоступен до отработки отказа.<br /><br /> 1 = только для чтения. База данных-получатель доступен только для клиентских соединений посредством ApplicationIntent = ReadOnly.<br /><br /> 2= все. Любое клиентское подключение доступен базы данных-получателя.|  
|secondary_allow_connections _desc|**nvarchar(256)**|Нет<br /><br /> All<br /><br /> Только для чтения|  
  
## <a name="permissions"></a>Разрешения  
 Это представление доступно только в **master** базы данных имени входа субъекта уровня сервера.  
  
## <a name="example"></a>Пример  
 Отобразить все базы данных с соединениями георепликации.  
  
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
  
  
