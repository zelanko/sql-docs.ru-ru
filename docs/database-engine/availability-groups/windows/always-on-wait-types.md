---
title: Идентификация задержек, связанных с группами доступности
description: Идентификация задержек, связанных с группами доступности Always On, с помощью Transact-SQL (T-SQL) и расширенных событий.
ms.custom: ag-guide, seodec18
ms.date: 06/13/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
ms.assetid: afa8caff-f325-48d9-a8ef-a30beab60389
author: rothja
ms.author: jroth
ms.openlocfilehash: a62145645a965d46c8da076eca14cd8a3dd85857
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67934967"
---
# <a name="identify-waits-associated-with-availability-groups"></a>Идентификация задержек, связанных с группами доступности
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  При устранении неполадок с задержкой для групп доступности AlwaysOn можно отслеживать накапливаемую статистику ожидания с помощью зависящих от групп доступности типов ожидания в динамическом административном представлении [sys.dm_os_wait_stats (Transact-SQL)](~/relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql.md).  
  
 Общие сведения об использовании статистики ожидания см. в разделе [Ожидания и очереди в SQL Server 2005](https://technet.microsoft.com/library/cc966413.aspx). Этот документ был написан для SQL Server 2005, но сведения в нем актуальны и для более поздних версий SQL Server.  
  
## <a name="query-for-availability-groups-wait-types"></a>Запрос для типов ожидания групп доступности  
 Чтобы получить всю статистику ожидания по типам ожидания групп доступности, используйте следующий запрос T-SQL:  
  
```sql  
SELECT * FROM sys.dm_os_wait_stats   
WHERE wait_type LIKE '%hadr%'  
ORDER BY wait_time_ms DESC  
```  
  
 Чтобы отслеживать статистику ожидания путем записи расширенных событий, используйте приведенную ниже команду T-SQL.  
  
```sql
CREATE EVENT SESSION [alwayson] ON SERVER   
ADD EVENT sqlos.wait_info(  
    WHERE ([wait_type]=(758) OR [wait_type]=(776) OR [wait_type]=(853) OR [wait_type]=(833)))  
WITH (MAX_MEMORY=4096 KB,EVENT_RETENTION_MODE=ALLOW_SINGLE_EVENT_LOSS,MAX_DISPATCH_LATENCY=30 SECONDS,  
MAX_EVENT_SIZE=0 KB,MEMORY_PARTITION_MODE=NONE,TRACK_CAUSALITY=OFF,STARTUP_STATE=OFF)  
GO  
```  
  
 Сопоставление ключа и значения для типа ожидания можно просмотреть, выполнив следующий запрос:  
  
```sql
SELECT * FROM sys.dm_xe_map_values   
WHERE name='wait_types' AND map_value LIKE '%hadr%'   
ORDER BY map_key ASC  
```  
  
## <a name="next-steps"></a>Следующие шаги  
 [Типы ожиданий](~/relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql.md#WaitTypes)  
  
  
