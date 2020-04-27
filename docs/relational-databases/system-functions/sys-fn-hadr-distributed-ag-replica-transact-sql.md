---
title: sys. fn_hadr_distributed_ag_replica (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
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
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: b4e6437a07aa571fc538f2630124dd52496d08e9
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "67906170"
---
# <a name="sysfn_hadr_distributed_ag_replica-transact-sql"></a>sys. fn_hadr_distributed_ag_replica (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Используется для отображения реплики в распределенной группе доступности в локальной группе доступности.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sys.fn_hadr_distributed_ag_replica( lag_Id, replica_id )  
```  
  
## <a name="arguments"></a>Аргументы  
 "*lag_Id*"  
 Идентификатор распределенной группы доступности. *lag_Id* имеет тип **uniqueidentifier**.  
  
 "*replica_id*"  
 Идентификатор реплики в распределенной группе доступности. *replica_id* имеет тип **uniqueidentifier**.  
  
## <a name="tables-returned"></a>Возвращаемые таблицы  
 Возвращает следующие данные.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**group_id**|**uniqueidentifier**|Уникальный идентификатор (GUID) локальной группы доступности.|  
  
## <a name="examples"></a>Примеры  
  
### <a name="using-sysfn_hadr_distributed_ag_replica"></a>Использование Sys. fn_hadr_distributed_ag_replica  
 В следующем примере возвращается таблица с идентификатором локальной группы доступности, связанной с указанной распределенной группой доступности и репликой.  
  
```  
DECLARE @lagId uniqueidentifier = '4A03D1A8-4AE6-B153-E7E9-ED22A546008D'  
DECLARE @replicaId uniqueidentifier = 'D5517513-04A8-FD82-14C6-E684EC913935'  
  
SELECT * FROM sys.fn_hadr_distributed_ag_replica(@lagId, @replicaId)  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Функции группы доступности AlwaysOn &#40;Transact-SQL&#41;](../../relational-databases/system-functions/always-on-availability-groups-functions-transact-sql.md)   
 [Группы доступности AlwaysOn &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md)   
 [Распределенные группы доступности &#40;группы доступности AlwaysOn&#41;](../../database-engine/availability-groups/windows/distributed-availability-groups-always-on-availability-groups.md)  
 [Создание группы доступности &#40;&#41;Transact-SQL](../../t-sql/statements/create-availability-group-transact-sql.md)   
 [ALTER AVAILABILITY GROUP (Transact-SQL)](../../t-sql/statements/alter-availability-group-transact-sql.md)  
  
  
