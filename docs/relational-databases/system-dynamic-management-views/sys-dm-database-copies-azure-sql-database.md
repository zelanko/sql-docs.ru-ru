---
title: "sys.dm_database_copies (база данных SQL Azure) | Документы Microsoft"
ms.custom: 
ms.date: 06/10/2016
ms.prod: 
ms.prod_service: sql-database
ms.reviewer: 
ms.service: sql-database
ms.component: dmv's
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dm_database_copies_TSQL
- sys.dm_database_copies
- dm_database_copies
- sys.dm_database_copies_TSQL
dev_langs: TSQL
helpviewer_keywords:
- dm_database_copies
- sys.dm_database_copies
ms.assetid: d03d4657-86d1-4496-97e6-cc3bc292e0b1
caps.latest.revision: "25"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a9ea0a5834ae83cd49deec2731f6ce2c3f8ccacc
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmdatabasecopies-azure-sql-database"></a>sys.dm_database_copies (база данных SQL Azure)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Возвращает сведения о копии базы данных.  
  
Чтобы вернуть сведения о георепликации ссылки, используйте [sys.geo_replication_links](../../relational-databases/system-dynamic-management-views/sys-geo-replication-links-azure-sql-database.md) или [sys.dm_geo_replication_link_status](../../relational-databases/system-dynamic-management-views/sys-dm-geo-replication-link-status-azure-sql-database.md) представления (доступно в базе данных SQL V12).
  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**database_id**|**int**|Идентификатор текущей базы данных в представлении `sys.databases`.|  
|**start_date**|**datetimeoffset**|Время начала копирования базы данных в формате UTC в региональном центре обработки данных [!INCLUDE[ssSDS](../../includes/sssds-md.md)].|  
|**modify_date**|**datetimeoffset**|Время завершения копирования базы данных в формате UTC в региональном центре обработки данных [!INCLUDE[ssSDS](../../includes/sssds-md.md)]. После копирования новая база данных транзакционно согласована с базой данных-источником. Сведения о выполнении обновляется каждую минуту.<br /><br />Время в формате UTC последнего обновления поля percent_complete отражения.|  
|**percent_complete**|**real**|Процентное соотношение скопированных данных в байтах. Допустимы значения от 0 до 100. [!INCLUDE[ssSDS](../../includes/sssds-md.md)] может автоматически восстановиться после некоторых ошибок, например отработки отказа, и перезапустить копирование базы данных. В этом случае percent_complete перезапустится при значении 0.|  
|**error_code**|**int**|Если значение больше 0, это код ошибки, возникшей при копировании. Значение равно 0, если ошибки не возникли.|  
|**error_desc**|**nvarchar(4096)**|Описание ошибки, возникшей при копировании.|  
|**ERROR_SEVERITY**|**int**|Возвращает 16, если во время копирования базы данных произошла ошибка.|  
|**функция ERROR_STATE**|**int**|Возвращает значение 1, если при копировании возникла ошибка.|  
|**copy_guid**|**uniqueidentifier**|Уникальный идентификатор операции копирования.|  
|**partner_server**|**sysname**|Имя базы данных SQL server, где создается копия.|  
|**partner_database**|**sysname**|Имя копии базы данных на сервере-участнике.|  
|**replication_state**|**tinyint**|Состояние репликации непрерывного копирования для этой базы данных. Возможны следующие значения.<br /><br /> 0 = ожидает согласования. Создание копии базы данных запланировано, но необходимые действия по подготовке еще не завершены или временно заблокированы квотой заполнения.<br /><br /> 1 = заполнение. Копировать базу данных, инициируемых еще не синхронизирована полностью с исходной базой данных. В этом состоянии не удается подключиться к копии. Чтобы отменить операцию заполнения в данный момент, должны быть удалены Копировать базу данных.|  
|**replication_state_desc**|**nvarchar(256)**|Описание replication_state (одно из следующих значений):<br /><br /> PENDING<br /><br /> SEEDING<br />|  
|**maximum_lag**|**int**|Зарезервированное поле.|  
|**is_continuous_copy**|**bit**|0 = возвращает значение 0|  
|**is_target_role**|**bit**|0 = база данных-источник<br /><br /> 1 = копирование базы данных|  
|**is_interlink_connected**|bit|Зарезервированное поле.|  
|**is_offline_secondary**|bit|Зарезервированное поле.|  
  
## <a name="permissions"></a>Permissions  
 Это представление доступно только в **master** базы данных для имени входа субъекта серверного уровня.  
  
## <a name="remarks"></a>Замечания  
 Можно использовать **sys.dm_database_copies** просмотра в **master** базы данных источника или целевого объекта [!INCLUDE[ssSDS](../../includes/sssds-md.md)] сервера. После успешного завершения копирования базы данных и новая база данных переходит в оперативный режим, в строке **sys.dm_database_copies** представление удаляется автоматически.  
  
  
