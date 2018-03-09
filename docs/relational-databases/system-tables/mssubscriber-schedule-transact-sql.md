---
title: "MSsubscriber_schedule (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- MSsubscriber_schedule
- MSsubscriber_schedule_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSsubscriber_schedule system table
ms.assetid: ff428306-0ef4-49a3-b536-07ccdf6e2196
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 983ea7374e26cfae1c3313f1e4eaec9bd287ff22
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="mssubscriberschedule-transact-sql"></a>MSsubscriber_schedule (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSsubscriber_schedule** таблица содержит расписания синхронизации транзакций для каждой пары издатель-подписчик и слияния по умолчанию. Эта таблица хранится в базе данных распространителя.  
  
> [!NOTE]  
>  Эта системная таблица является устаревшим и сохраняется для поддержки более ранних версиях [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**издатель**|**sysname**|Имя издателя.|  
|**подписчик**|**sysname**|Имя подписчика.|  
|**agent_type**|**smallint**|Тип агента:<br /><br /> 0 = агент распространителя;<br /><br /> 1 = агент слияния.|  
|**frequency_type**|**int**|Частота запуска агента распространителя по расписанию:<br /><br /> **1** = один раз.<br /><br /> **2** = по запросу.<br /><br /> **4** = ежедневно.<br /><br /> **8** = еженедельно.<br /><br /> **16** = ежемесячно.<br /><br /> **32** = ежемесячное расписание.<br /><br /> **64** = автозапуск.<br /><br /> **128** = повторять.|  
|**frequency_interval**|**int**|Значение, которое применяется к частоте, установленной аргументом **frequency_type**.|  
|**frequency_relative_interval**|**int**|Период агента распространителя:<br /><br /> **1** = первый.<br /><br /> **2** = секунда.<br /><br /> **4** = третий.<br /><br /> **8** = четвертый.<br /><br /> **16** = последний.|  
|**frequency_recurrence_factor**|**int**|Коэффициент повторения, используемый **frequency_type**.|  
|**frequency_subday**|**int**|Частота изменения расписания в течение заданного периода:<br /><br /> **1** = один раз.<br /><br /> **2** = секунда.<br /><br /> **4** = минута.<br /><br /> **8** = час.|  
|**frequency_subday_interval**|**int**|Интервал для **frequency_subday**.|  
|**active_start_time_of_day**|**int**|Время, когда запланировано первое выполнение агента распространителя, в формате ЧЧММСС.|  
|**active_end_time_of_day**|**int**|Время, когда будет прекращено выполнение агента распространителя по расписанию, в формате ЧЧММСС.|  
|**active_start_date**|**int**|Дата, когда запланировано первое выполнение агента распространителя, в формате ГГГГММДД.|  
|**active_end_date**|**int**|Дата, когда будет прекращено выполнение агента распространителя по расписанию, в формате ГГГГММДД.|  
  
## <a name="see-also"></a>См. также:  
 [Таблицы репликации &#40; Transact-SQL &#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
