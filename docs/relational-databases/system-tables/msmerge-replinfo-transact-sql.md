---
title: "MSmerge_replinfo (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
f1_keywords:
- MSmerge_replinfo_TSQL
- MSmerge_replinfo
dev_langs: TSQL
helpviewer_keywords: MSmerge_replinfo system table
ms.assetid: b0924094-c0cc-49c1-869a-65be0d0465a0
caps.latest.revision: "26"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5dfda378d9d5327ab62803d07316c12e0eb9d3a9
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="msmergereplinfo-transact-sql"></a>MSmerge_replinfo (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSmerge_replinfo** содержит по одной строке для каждой подписки. Эта таблица отслеживает сведения о подписках. Эта таблица хранится в базах данных публикации и подписки.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**repid**|**uniqueidentifier**|Уникальный идентификатор реплики.|  
|**use_interactive_resolver**|**bit**|Показывает, используется ли интерактивный сопоставитель во время проверки согласованности.<br /><br /> **0** = не использует интерактивный арбитр конфликтов.<br /><br /> **1** = использование интерактивного сопоставителя.|  
|**validation_level**|**int**|Тип проверки подписки. Уровень проверки может иметь одно из следующих значений:<br /><br /> **0** = проверка не выполняется.<br /><br /> **1** = Проверка достоверности только количества строк.<br /><br /> **2** = проверки достоверности по количеству строк и контрольной суммы.<br /><br /> **3** = количество строк и двоичной контрольной сумме.|  
|**resync_gen**|**bigint**|Номер поколения, используемый при повторной синхронизации подписки. Значение **– 1** указывает, что подписка не помечена для повторной синхронизации.|  
|**login_name**|**sysname**|Имя пользователя, создавшего подписку.|  
|**Имя узла**|**sysname**|Значение, используемое параметризованным фильтром строк при формировании секции для подписки.|  
|**merge_jobid**|**binary(16)**|Идентификатор задания слияния, соответствующий данной подписке.|  
|**sync_info**|**int**|Только для внутреннего использования.|  
  
## <a name="see-also"></a>См. также:  
 [Таблицы репликации &#40; Transact-SQL &#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
