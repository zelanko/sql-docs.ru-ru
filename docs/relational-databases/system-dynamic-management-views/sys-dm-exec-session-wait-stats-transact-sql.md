---
title: sys. dm_exec_session_wait_stats (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 04/24/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_exec_session_wait_stats
- sys.dm_exec_session_wait_stats_tsql
- dm_exec_session_wait_stats
- dm_exec_session_wait_stats_tsql
helpviewer_keywords:
- sys.dm_exec_session_wait_stats
ms.assetid: df84842a-71eb-4fda-b448-5953cf9985dc
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6fc51bec78cf01522e6731648bdb7870ea7d9fb0
ms.sourcegitcommit: e37636c275002200cf7b1e7f731cec5709473913
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/13/2019
ms.locfileid: "73982610"
---
# <a name="sysdm_exec_session_wait_stats-transact-sql"></a>sys. dm_exec_session_wait_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Возвращает сведения обо всех ожиданиях, обнаруженных потоками, которые выполнялись для каждого сеанса. Это представление можно использовать для диагностики проблем с производительностью [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сеансе, а также с конкретными запросами и пакетами.  Это представление возвращает сеанс с теми же сведениями, которые объединены для [sys &#40;. dm_os_wait_stats Transact&#41; -SQL](../../relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql.md) , но также предоставляет номер **session_id** .  
  
**Применимо к**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] и выше).  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|session_id|**smallint**|Идентификатор сеанса.|  
|wait_type|**nvarchar(60)**|Имя типа ожидания. Дополнительные сведения см. в разделе [sys.dm_os_wait_stats (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql.md).|  
|waiting_tasks_count|**bigint**|Число ожиданий данного типа. Этот счетчик наращивается каждый раз при начале ожидания.|  
|wait_time_ms|**bigint**|Общее время ожидания данного типа в миллисекундах. Это время включает в себя время signal_wait_time_ms.|  
|max_wait_time_ms|**bigint**|Максимальное время ожидания данного типа.|  
|signal_wait_time_ms|**bigint**|Разница между временем сигнализации ожидающего потока и временем начала его выполнения.|  
  
## <a name="remarks"></a>Remarks  
 Это динамическое административное представление сбрасывает сведения для сеанса при открытии сеанса или при сбросе сеанса (если пул соединений).  
  
 Дополнительные сведения о типах ожидания см. в разделе [sys. &#40;DM_OS_WAIT_STATS Transact-&#41;SQL](../../relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql.md).  
  
## <a name="permissions"></a>Разрешения  
 Если пользователь имеет разрешение **View Server State** на сервере, он увидит все выполненные сеансы на экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]; в противном случае пользователь увидит только текущий сеанс.  
  
## <a name="see-also"></a>См. также статью  
 [Динамические административные представления и функции (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [SQL Server динамическое представление &#40;управления, связанное с операционной&#41; системой,  Transact-SQL](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
 [sys.dm_os_wait_stats (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql.md)  
 
