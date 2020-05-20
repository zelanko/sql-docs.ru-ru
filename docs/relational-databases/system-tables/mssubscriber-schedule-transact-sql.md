---
title: MSsubscriber_schedule (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSsubscriber_schedule
- MSsubscriber_schedule_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSsubscriber_schedule system table
ms.assetid: ff428306-0ef4-49a3-b536-07ccdf6e2196
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: bb5a31470af2630b0df53907db285e1206cc6fb4
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82824819"
---
# <a name="mssubscriber_schedule-transact-sql"></a>MSsubscriber_schedule (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  В **MSsubscriber_schedule** таблице содержатся расписания слияния и синхронизации транзакций по умолчанию для каждой пары "издатель — подписчик". Эта таблица хранится в базе данных распространителя.  
  
> [!NOTE]
>  Эта системная таблица устарела и поддерживается для поддержки более ранних версий [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**publisher**|**sysname**|Имя издателя.|  
|**абонент**|**sysname**|Имя подписчика.|  
|**agent_type**|**smallint**|Тип агента:<br /><br /> 0 = агент распространителя;<br /><br /> 1 = агент слияния.|  
|**frequency_type**|**int**|Частота запуска агента распространителя по расписанию:<br /><br /> **1** = один раз.<br /><br /> **2** = по запросу.<br /><br /> **4** = ежедневное.<br /><br /> **8** = еженедельно.<br /><br /> **16** = ежемесячно.<br /><br /> **32** = ежемесячное относительное.<br /><br /> **64** = автозапуск.<br /><br /> **128** = повторяющаяся.|  
|**frequency_interval**|**int**|Значение, применяемое к частоте, установленной **frequency_type**.|  
|**frequency_relative_interval**|**int**|Период агента распространителя:<br /><br /> **1** = сначала.<br /><br /> **2** = секунда.<br /><br /> **4** = третий.<br /><br /> **8** = четвертый.<br /><br /> **16** = последняя.|  
|**frequency_recurrence_factor**|**int**|Коэффициент повторения, используемый **frequency_type**.|  
|**frequency_subday**|**int**|Частота изменения расписания в течение заданного периода:<br /><br /> **1** = один раз.<br /><br /> **2** = секунда.<br /><br /> **4** = минута.<br /><br /> **8** = час.|  
|**frequency_subday_interval**|**int**|Интервал для **frequency_subday**.|  
|**active_start_time_of_day**|**int**|Время, когда запланировано первое выполнение агента распространителя, в формате ЧЧММСС.|  
|**active_end_time_of_day**|**int**|Время, когда будет прекращено выполнение агента распространителя по расписанию, в формате ЧЧММСС.|  
|**active_start_date**|**int**|Дата, когда запланировано первое выполнение агента распространителя, в формате ГГГГММДД.|  
|**active_end_date**|**int**|Дата, когда будет прекращено выполнение агента распространителя по расписанию, в формате ГГГГММДД.|  
  
## <a name="see-also"></a>См. также  
 [Таблицы репликации &#40;&#41;Transact-SQL](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
