---
title: sys.fn_hadr_distributed_ag_database_replica (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/14/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.fn_hadr_distributed_ag_database_replica
- sys.fn_hadr_distributed_ag_database_replica_TSQL
- fn_hadr_distributed_ag_database_replica
- fn_hadr_distributed_ag_database_replica_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.fn_hadr_distributed_ag_database_replica
ms.assetid: 0e6202a1-e872-4f53-99d7-c16b6f712efc
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 2acff9f5d78549fe1e00397d566053ec19f628a8
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68120241"
---
# <a name="sysfnhadrdistributedagdatabasereplica-transact-sql"></a>sys.fn_hadr_distributed_ag_database_replica (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Используется для сопоставления базы данных в распределенной группе доступности с базой данных в группе доступности локальных ресурсов.  
   
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sys.fn_hadr_distributed_ag_database_replica( lag_Id, database_id )  
```  
  
## <a name="arguments"></a>Аргументы  
 '*lag_Id*'  
 — Это идентификатор распределенной группы доступности. *lag_Id* является типом **uniqueidentifier**.  
  
 "*database_id*"  
 — Это идентификатор базы данных в распределенной группе доступности. *database_id* является типом **uniqueidentifier**.  
  
## <a name="tables-returned"></a>Возвращаемые таблицы  
 Возвращает следующие данные.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**group_database_id**|**uniqueidentifier**|Идентификатор базы данных в группе доступности локальных ресурсов.|  
  
## <a name="examples"></a>Примеры  
  
### <a name="using-sysfnhadrdistributedagdatabasereplica"></a>С помощью sys.fn_hadr_distributed_ag_database_replica  
 В следующем примере передается в идентификатор базы данных в распределенной группе доступности. Она возвращает таблицу с Идентификатором базы данных, связанные с группой доступности локальных ресурсов.  
  
```  
DECLARE @lagId uniqueidentifier = '4A03D1A8-4AE6-B153-E7E9-ED22A546008D'  
DECLARE @databaseId uniqueidentifier = '3FFA882A-C4C3-5B9E-A203-8F44BD9659F7'  
  
SELECT * FROM sys.fn_hadr_distributed_ag_database_replica(@lagId, @databaseId)  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Функции групп доступности Always On &#40;Transact-SQL&#41;](../../relational-databases/system-functions/always-on-availability-groups-functions-transact-sql.md)   
 [Группы доступности AlwaysOn (SQL Server)](../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md)   
 [Распределенные группы доступности &#40;группы доступности AlwaysOn&#41;](../../database-engine/availability-groups/windows/distributed-availability-groups-always-on-availability-groups.md)   
 [CREATE AVAILABILITY GROUP (Transact-SQL)](../../t-sql/statements/create-availability-group-transact-sql.md)   
 [ALTER AVAILABILITY GROUP (Transact-SQL)](../../t-sql/statements/alter-availability-group-transact-sql.md)  
  
  
