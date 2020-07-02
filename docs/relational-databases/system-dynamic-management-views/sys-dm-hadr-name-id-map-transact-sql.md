---
title: sys. dm_hadr_name_id_map (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_hadr_name_id_map
- sys.dm_hadr_name_id_map_TSQL
- dm_hadr_name_id_map
- dm_hadr_name_id_map_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- sys.dm_hadr_name_id_map dynamic management view
ms.assetid: e07bb8a9-37de-4a39-a257-950d7c3ae8fb
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 0bf0e07bd621161a512d7096bff2949039d3ba1b
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85752839"
---
# <a name="sysdm_hadr_name_id_map-transact-sql"></a>sys.dm_hadr_name_id_map (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Показывает сопоставление группы доступности Always On, что текущий экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] соединен с тремя уникальными идентификаторами: идентификатор группы доступности, идентификатор ресурса WSFC и идентификатор группы WSFC. Цель такого сопоставления состоит в обработке сценария, в ходе которого ресурс/группа WSFC переименовывается.  
   
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**ag_name**|**nvarchar(256)**|Имя группы доступности. Определяемое пользователем имя, которое должно быть уникальным в пределах отказоустойчивого кластера Windows Server (WSFC).|  
|**ag_id**|**uniqueidentifier**|Уникальный идентификатор (GUID) группы доступности.|  
|**ag_resource_id**|**nvarchar(256)**|Уникальный идентификатор группы ресурсов в виде ресурса в кластере WSFC.|  
|**ag_group_id**|**nvarchar(256)**|Уникальный групповой идентификатор WSFC группы доступности.|  
  
## <a name="permissions"></a>Разрешения  
 необходимо разрешение VIEW SERVER STATE на сервере.  
  
## <a name="see-also"></a>См. также  
 [Always On динамические административные представления и функции групп доступности &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/always-on-availability-groups-dynamic-management-views-functions.md)   
 [Always On представления каталога групп доступности &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/always-on-availability-groups-catalog-views-transact-sql.md)   
 [Мониторинг групп доступности &#40;&#41;Transact-SQL](../../database-engine/availability-groups/windows/monitor-availability-groups-transact-sql.md)   
 [Группы доступности AlwaysOn (SQL Server)](../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md)  
  
  
