---
title: MSsubscriber_schedule (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- MSsubscriber_schedule
- MSsubscriber_schedule_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSsubscriber_schedule system table
ms.assetid: ff428306-0ef4-49a3-b536-07ccdf6e2196
caps.latest.revision: 34
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 1424947221413447e0277df4c10b17c0ea08d8b2
ms.sourcegitcommit: a431ca21eac82117492d7b84c398ddb3fced53cc
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/17/2018
ms.locfileid: "39103662"
---
# <a name="mssubscriberschedule-transact-sql"></a>MSsubscriber_schedule (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSsubscriber_schedule** таблица содержит слияния по умолчанию и расписаний синхронизации транзакций для каждой пары издатель-подписчик. Эта таблица хранится в базе данных распространителя.  
  
> [!NOTE]  
>  Эта системная таблица устарела и поддерживается для поддержки более ранних версиях [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**издатель**|**sysname**|Имя издателя.|  
|**подписчик**|**sysname**|Имя подписчика.|  
|**agent_type**|**smallint**|Тип агента:<br /><br /> 0 = агент распространителя;<br /><br /> 1 = агент слияния.|  
|**frequency_type**|**int**|Частота запуска агента распространителя по расписанию:<br /><br /> **1** = один раз.<br /><br /> **2** = по запросу.<br /><br /> **4** = ежедневно.<br /><br /> **8** = еженедельно.<br /><br /> **16** = ежемесячно.<br /><br /> **32** = ежемесячное расписание.<br /><br /> **64** = автозапуск.<br /><br /> **128** = повторять.|  
|**frequency_interval**|**int**|Значение, которое применяется к частоте, задаваемой аргументом **frequency_type**.|  
|**frequency_relative_interval**|**int**|Период агента распространителя:<br /><br /> **1** = первый.<br /><br /> **2** = секунда.<br /><br /> **4** = третий.<br /><br /> **8** = четвертый.<br /><br /> **16** = последний.|  
|**frequency_recurrence_factor**|**int**|Коэффициент повторения, используемый с **frequency_type**.|  
|**frequency_subday**|**int**|Частота изменения расписания в течение заданного периода:<br /><br /> **1** = один раз.<br /><br /> **2** = секунда.<br /><br /> **4** = минута.<br /><br /> **8** = час.|  
|**frequency_subday_interval**|**int**|Интервал для **frequency_subday**.|  
|**active_start_time_of_day**|**int**|Время, когда запланировано первое выполнение агента распространителя, в формате ЧЧММСС.|  
|**active_end_time_of_day**|**int**|Время, когда будет прекращено выполнение агента распространителя по расписанию, в формате ЧЧММСС.|  
|**active_start_date**|**int**|Дата, когда запланировано первое выполнение агента распространителя, в формате ГГГГММДД.|  
|**active_end_date**|**int**|Дата, когда будет прекращено выполнение агента распространителя по расписанию, в формате ГГГГММДД.|  
  
## <a name="see-also"></a>См. также  
 [Таблицы репликации &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
