---
title: MSmerge_replinfo (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- MSmerge_replinfo_TSQL
- MSmerge_replinfo
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_replinfo system table
ms.assetid: b0924094-c0cc-49c1-869a-65be0d0465a0
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 7257ce7d12fe4797c09836de2de45829500afd6b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47790662"
---
# <a name="msmergereplinfo-transact-sql"></a>MSmerge_replinfo (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSmerge_replinfo** таблица содержит по одной строке для каждой подписки. Эта таблица отслеживает сведения о подписках. Эта таблица хранится в базах данных публикации и подписки.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**repid**|**uniqueidentifier**|Уникальный идентификатор реплики.|  
|**use_interactive_resolver**|**bit**|Показывает, используется ли интерактивный сопоставитель во время проверки согласованности.<br /><br /> **0** = не использует интерактивный арбитр конфликтов.<br /><br /> **1** = использовать интерактивный Сопоставитель.|  
|**validation_level**|**int**|Тип проверки подписки. Уровень проверки может иметь одно из следующих значений:<br /><br /> **0** = проверка не выполняется.<br /><br /> **1** = проверка только количества строк.<br /><br /> **2** = проверки достоверности по количеству строк и контрольной сумме.<br /><br /> **3** = количество строк и двоичной контрольной сумме.|  
|**resync_gen**|**bigint**|Номер поколения, используемый при повторной синхронизации подписки. Значение **– 1** указывает, что подписка не помечена для повторной синхронизации.|  
|**login_name**|**sysname**|Имя пользователя, создавшего подписку.|  
|**Имя узла**|**sysname**|Значение, используемое параметризованным фильтром строк при формировании секции для подписки.|  
|**merge_jobid**|**binary(16)**|Идентификатор задания слияния, соответствующий данной подписке.|  
|**sync_info**|**int**|Только для внутреннего использования.|  
  
## <a name="see-also"></a>См. также  
 [Таблицы репликации &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
