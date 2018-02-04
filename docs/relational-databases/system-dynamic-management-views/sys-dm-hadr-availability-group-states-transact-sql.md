---
title: "sys.dm_hadr_availability_group_states (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.dm_hadr_availability_group_states
- sys.dm_hadr_availability_group_states_TSQL
- dm_hadr_availability_group_states_TSQL
- dm_hadr_availability_group_states
dev_langs:
- TSQL
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- sys.dm_hadr_availability_group_states dynamic management view
ms.assetid: d18019dd-f8dc-4492-b035-b1a639369b65
caps.latest.revision: 
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b4d6dbddbf0fb211335789eefeff5f2a392f2d59
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/03/2018
---
# <a name="sysdmhadravailabilitygroupstates-transact-sql"></a>sys.dm_hadr_availability_group_states (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Возвращает по одной строке для каждой группы доступности AlwaysOn, у которых имеется реплика доступности на локальном экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Каждая строка отображает состояния работоспособности определенной группы доступности.  
  
> [!NOTE]  
>  Чтобы получить полный список, запросите [sys.availability_groups](../../relational-databases/system-catalog-views/sys-availability-groups-transact-sql.md) представления каталога.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**group_id**|**uniqueidentifier**|Уникальный идентификатор группы доступности.|  
|**primary_replica**|**varchar(128)**|Имя экземпляра сервера, на котором размещена текущая первичная реплика.<br /><br /> NULL = не первичная реплика, или не удается связаться с отказоустойчивым кластером WSFC.|  
|**primary_recovery_health**|**tinyint**|Указывает состояние работоспособности (восстановления) первичной реплики, одно из следующих значений:<br /><br /> 0 = выполняется<br /><br /> 1 = в сети<br /><br /> NULL<br /><br /> На вторичных репликах **primary_recovery_health** столбец имеет значение NULL.|  
|**primary_recovery_health_desc**|**nvarchar(60)**|Описание **primary_replica_health**, одно из:<br /><br /> ONLINE_IN_PROGRESS<br /><br /> ONLINE<br /><br /> NULL|  
|**secondary_recovery_health**|**tinyint**|Указывает состояние работоспособности восстановления реплики вторичной реплики, одно из:<br /><br /> 0 = выполняется<br /><br /> 1 = в сети<br /><br /> NULL<br /><br /> В первичной реплике **secondary_recovery_health** столбец имеет значение NULL.|  
|**secondary_recovery_health_desc**|**nvarchar(60)**|Описание **secondary_recovery_health**, одно из:<br /><br /> ONLINE_IN_PROGRESS<br /><br /> ONLINE<br /><br /> NULL|  
|**synchronization_health**|**tinyint**|Отражает свертку **synchronization_health** всех реплик доступности в группе доступности. Ниже приведены возможные значения и их описания.<br /><br /> 0: неработоспособны. Ни одна из реплик доступности не имеет исправное состояние **synchronization_health** (2 = HEALTHY).<br /><br /> 1: частично работоспособна. Некоторые, но не все реплики доступности находятся в исправном состоянии.<br /><br /> 2: исправен. Все реплики доступности находятся в исправном состоянии синхронизации.<br /><br /> Сведения об исправности синхронизации реплики см. в разделе **synchronization_health** столбца в [sys.dm_hadr_availability_replica_states &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-replica-states-transact-sql.md).|  
|**synchronization_health_desc**|**nvarchar(60)**|Описание **synchronization_health**, одно из:<br /><br /> NOT_HEALTHY<br /><br /> PARTIALLY_HEALTHY<br /><br /> HEALTHY|  
  
## <a name="security"></a>безопасность  
  
### <a name="permissions"></a>Разрешения  
 необходимо разрешение VIEW SERVER STATE на сервере.  
  
## <a name="see-also"></a>См. также  
 [Отслеживание групп доступности &#40; Transact-SQL &#41;](../../database-engine/availability-groups/windows/monitor-availability-groups-transact-sql.md)   
 [Группы доступности AlwaysOn (SQL Server)](../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md)   
 [Динамические административные представления и функции &#40; с группами доступности Always On Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/always-on-availability-groups-dynamic-management-views-functions.md)  
  
  
