---
title: sys.dm_hadr_name_id_map (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
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
caps.latest.revision: 8
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 69b1fd2e09b4f7c13540928328e4d5ca0697a530
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sysdmhadrnameidmap-transact-sql"></a>sys.dm_hadr_name_id_map (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Показывает сопоставление групп доступности AlwaysOn, что текущий экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] присоединился к трем уникальным идентификаторам: Идентификатору группы доступности, Идентификатору ресурса WSFC и идентификатору группы WSFC Цель такого сопоставления состоит в обработке сценария, в ходе которого ресурс/группа WSFC переименовывается.  
   
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**ag_name**|**nvarchar(256)**|Имя группы доступности. Определяемое пользователем имя, которое должно быть уникальным в пределах отказоустойчивого кластера Windows Server (WSFC).|  
|**ag_id**|**uniqueidentifier**|Уникальный идентификатор (GUID) группы доступности.|  
|**ag_resource_id**|**nvarchar(256)**|Уникальный идентификатор группы ресурсов в виде ресурса в кластере WSFC.|  
|**ag_group_id**|**nvarchar(256)**|Уникальный групповой идентификатор WSFC группы доступности.|  
  
## <a name="permissions"></a>Разрешения  
 необходимо разрешение VIEW SERVER STATE на сервере.  
  
## <a name="see-also"></a>См. также  
 [Динамические представления управления и функции, связанные с группами доступности AlwaysOn (Transact-SQL)](../../relational-databases/system-dynamic-management-views/always-on-availability-groups-dynamic-management-views-functions.md)   
 [Представления каталога групп доступности AlwaysOn (Transact-SQL)](../../relational-databases/system-catalog-views/always-on-availability-groups-catalog-views-transact-sql.md)   
 [Отслеживание групп доступности & #40; Transact-SQL & #41;](../../database-engine/availability-groups/windows/monitor-availability-groups-transact-sql.md)   
 [Группы доступности AlwaysOn (SQL Server)](../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md)  
  
  
