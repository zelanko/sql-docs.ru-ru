---
title: sys.dm_exec_session_wait_stats (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 04/24/2018
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_exec_session_wait_stats
- sys.dm_exec_session_wait_stats_tsql
- dm_exec_session_wait_stats
- dm_exec_session_wait_stats_tsql
helpviewer_keywords:
- sys.dm_exec_session_wait_stats
ms.assetid: df84842a-71eb-4fda-b448-5953cf9985dc
caps.latest.revision: 6
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 4d5932d5fa878f3816c636b6106c2723a40834be
ms.sourcegitcommit: 7019ac41524bdf783ea2c129c17b54581951b515
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2018
ms.locfileid: "34465080"
---
# <a name="sysdmexecsessionwaitstats-transact-sql"></a>sys.dm_exec_session_wait_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Возвращает сведения обо всех случаях ожидания, зафиксированных потоками, которые выполнены для каждого сеанса. Это представление можно использовать для диагностики проблем производительности с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сеанса и конкретных запросов и пакетов.  Это представление возвращает сеанс ту же информацию, которая суммируется для [sys.dm_os_wait_stats &#40;Transact-SQL&#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql.md) , но предоставляет **session_id** , он также.  
  
**Область применения**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (с[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] по [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]).  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|session_id|**smallint**|Идентификатор сеанса.|  
|wait_type|**nvarchar(60)**|Имя типа ожидания. Дополнительные сведения см. в разделе [sys.dm_os_wait_stats (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql.md).|  
|waiting_tasks_count|**bigint**|Число ожиданий данного типа. Этот счетчик наращивается каждый раз при начале ожидания.|  
|wait_time_ms|**bigint**|Общее время ожидания данного типа в миллисекундах. Это время включает в себя время signal_wait_time_ms.|  
|max_wait_time_ms|**bigint**|Максимальное время ожидания данного типа.|  
|signal_wait_time_ms|**bigint**|Разница между временем сигнализации ожидающего потока и временем начала его выполнения.|  
  
## <a name="remarks"></a>Примечания  
 Это динамическое административное Представление сбрасывает сведения для сеанса, при открытии сеанса или при сбросе сеанс (если пул соединений),  
  
 Сведения о типах ожидания см. в разделе [sys.dm_os_wait_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql.md).  
  
## <a name="permissions"></a>Разрешения  
 Если у пользователя есть **VIEW SERVER STATE** разрешение на сервере, пользователь увидит все выполняющиеся сеансы на экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]; в противном случае пользователь увидит только текущий сеанс.  
  
## <a name="see-also"></a>См. также  
 [Динамические административные представления и функции (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Динамические административные представления, относящиеся к операционной системе SQL Server &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)   
 [sys.dm_os_wait_stats (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql.md)  
 
