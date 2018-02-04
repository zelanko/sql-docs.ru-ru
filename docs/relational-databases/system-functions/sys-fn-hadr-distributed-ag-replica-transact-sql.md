---
title: "sys.fn_hadr_distributed_ag_replica (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.fn_hadr_distributed_ag_replica
- sys.fn_hadr_distributed_ag_replica_TSQL
- fn_hadr_distributed_ag_replica
- fn_hadr_distributed_ag_replica_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.fn_hadr_distributed_ag_replica
ms.assetid: a1e5f9cb-c350-4bb4-a04f-7394f6f25d62
caps.latest.revision: 
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f53f1eac87a7b02197412283e8413849c1450f86
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/03/2018
---
# <a name="sysfnhadrdistributedagreplica-transact-sql"></a>sys.fn_hadr_distributed_ag_replica (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Используется для сопоставления реплики в распределенную группу доступности к группе доступности локальных ресурсов.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sys.fn_hadr_distributed_ag_replica( lag_Id, replica_id )  
```  
  
## <a name="arguments"></a>Аргументы  
 '*lag_Id*'  
 — Это идентификатор распределенной группы доступности. *lag_Id* — тип **uniqueidentifier**.  
  
 '*replica_id*'  
 — Это идентификатор реплики в распределенной группы доступности. *replica_id* — тип **uniqueidentifier**.  
  
## <a name="tables-returned"></a>Возвращаемые таблицы  
 Возвращает следующие данные.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**group_id**|**uniqueidentifier**|Уникальный идентификатор (GUID) группы доступности локальных ресурсов.|  
  
## <a name="examples"></a>Примеры  
  
### <a name="using-sysfnhadrdistributedagreplica"></a>С помощью sys.fn_hadr_distributed_ag_replica  
 Следующий пример возвращает таблицу с идентификатором группы доступности локальных ресурсов, связанный с указанным распределенной группы доступности и реплики.  
  
```  
DECLARE @lagId uniqueidentifier = '4A03D1A8-4AE6-B153-E7E9-ED22A546008D'  
DECLARE @replicaId uniqueidentifier = 'D5517513-04A8-FD82-14C6-E684EC913935'  
  
SELECT * FROM sys.fn_hadr_distributed_ag_replica(@lagId, @replicaId)  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Функции &#40; групп доступности AlwaysOn Transact-SQL &#41;](../../relational-databases/system-functions/always-on-availability-groups-functions-transact-sql.md)   
 [Группы доступности AlwaysOn &#40; SQL Server &#41;](../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md)   
 [Распределенные группы доступности &#40; Группы доступности AlwaysOn &#41;](../../database-engine/availability-groups/windows/distributed-availability-groups-always-on-availability-groups.md)  
 [Создание группы ДОСТУПНОСТИ &#40; Transact-SQL &#41;](../../t-sql/statements/create-availability-group-transact-sql.md)   
 [ALTER AVAILABILITY GROUP &#40; Transact-SQL &#41;](../../t-sql/statements/alter-availability-group-transact-sql.md)  
  
  
