---
title: sys. fn_hadr_distributed_ag_database_replica (Transact-SQL) | Документация Майкрософт
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
ms.openlocfilehash: d7b894919a4149d37181d543b8d58fc820aad10b
ms.sourcegitcommit: 703968b86a111111a82ef66bb7467dbf68126051
ms.contentlocale: ru-RU
ms.lasthandoff: 07/07/2020
ms.locfileid: "86053042"
---
# <a name="sysfn_hadr_distributed_ag_database_replica-transact-sql"></a>sys. fn_hadr_distributed_ag_database_replica (Transact-SQL)
[!INCLUDE [sqlserver2016](../../includes/applies-to-version/sqlserver2016.md)]

  Используется для преобразования базы данных в распределенной группе доступности в базу данных в локальной группе доступности.  
   
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sys.fn_hadr_distributed_ag_database_replica( lag_Id, database_id )  
```  
  
## <a name="arguments"></a>Аргументы  
 "*lag_Id*"  
 Идентификатор распределенной группы доступности. *lag_Id* имеет тип **uniqueidentifier**.  
  
 "*database_id*"  
 Идентификатор базы данных в распределенной группе доступности. *database_id* имеет тип **uniqueidentifier**.  
  
## <a name="tables-returned"></a>Возвращаемые таблицы  
 Возвращает следующие данные.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**group_database_id**|**uniqueidentifier**|Идентификатор базы данных в локальной группе доступности.|  
  
## <a name="examples"></a>Примеры  
  
### <a name="using-sysfn_hadr_distributed_ag_database_replica"></a>Использование Sys. fn_hadr_distributed_ag_database_replica  
 В следующем примере идентификатор базы данных передается в распределенной группе доступности. Он возвращает таблицу с ИДЕНТИФИКАТОРом базы данных, связанным с локальной группой доступности.  
  
```  
DECLARE @lagId uniqueidentifier = '4A03D1A8-4AE6-B153-E7E9-ED22A546008D'  
DECLARE @databaseId uniqueidentifier = '3FFA882A-C4C3-5B9E-A203-8F44BD9659F7'  
  
SELECT * FROM sys.fn_hadr_distributed_ag_database_replica(@lagId, @databaseId)  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Функции групп доступности Always On &#40;Transact-SQL&#41;](../../relational-databases/system-functions/always-on-availability-groups-functions-transact-sql.md)   
 [Always On группы доступности &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md)   
 [Распределенные группы доступности &#40;группы доступности Always On&#41;](../../database-engine/availability-groups/windows/distributed-availability-groups-always-on-availability-groups.md)   
 [CREATE AVAILABILITY GROUP (Transact-SQL)](../../t-sql/statements/create-availability-group-transact-sql.md)   
 [ALTER AVAILABILITY GROUP (Transact-SQL)](../../t-sql/statements/alter-availability-group-transact-sql.md)  
  
  
