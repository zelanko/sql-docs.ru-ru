---
title: "MSmerge_articlehistory (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
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
- MSmerge_articlehistory
- MSmerge_articlehistory_TSQL
dev_langs: TSQL
helpviewer_keywords: MSmerge_articlehistory system table
ms.assetid: 2870e7ea-dbec-4636-9171-c2cee96018ac
caps.latest.revision: "17"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: dbd2fef95a478eebc6526fc888fa621c1ec198ab
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="msmergearticlehistory-transact-sql"></a>MSmerge_articlehistory (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSmerge_articlehistory** таблица отслеживает изменения, внесенные в статьи во время сеанса синхронизации агента слияния, по одной строке для каждой статьи, в которую были внесены изменения. Эта таблица хранится в базе данных распространителя.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**session_id**|**int**|Идентификатор сеанса задания агента слияния в [MSmerge_sessions](../../relational-databases/system-tables/msmerge-sessions-transact-sql.md) системной таблицы.|  
|**phase_id**|**int**|Фаза сеанса синхронизации, которая может выглядеть следующим образом:<br /><br /> **1** = выгрузка.<br /><br /> **2** = загрузка.<br /><br /> **4** = очистки.<br /><br /> **5** = завершение работы.<br /><br /> **6** = изменения схемы.<br /><br /> **7** = BCP.|  
|**имя_статьи**|**sysname**|Имя статьи, в которой были выполнены изменения.|  
|**start_time**|**datetime**|Время начала обработки статьи агентом.|  
|**duration**|**int**|Отрезок времени (в секундах), в течение которого агент обрабатывал статью.|  
|**Вставляет**|**int**|Количество вставок, примененных к определенной статье во время синхронизации. Это значение будет увеличиваться во время процесса синхронизации, и конечное значение представляет собой общее число.|  
|**обновления**|**int**|Количество обновлений, примененных к определенной статье во время синхронизации. Это значение будет увеличиваться во время процесса синхронизации, и конечное значение представляет собой общее число.|  
|**Удаляет**|**int**|Количество удалений, примененных к определенной статье во время синхронизации. Это значение будет увеличиваться во время процесса синхронизации, и конечное значение представляет собой общее число.|  
|**конфликты**|**int**|Количество конфликтов, возникших во время синхронизации. Это значение будет увеличиваться во время процесса синхронизации, и конечное значение представляет собой общее число.|  
|**conflicts_resolved**|**int**|Количество разрешенных конфликтов, возникших во время синхронизации. Это значение будет увеличиваться во время процесса синхронизации, и конечное значение представляет собой общее число.|  
|**rows_retried**|**int**|Количество строк, к которым были выполнены неудачные обращения, и обращения к которым были повторены во время синхронизации. Это значение будет увеличиваться во время процесса синхронизации, и конечное значение представляет собой общее число.|  
|**percent_complete**|**decimal**|Процент общего времени синхронизации, потраченного агентом слияния на статью во время сеанса. До завершения сеанса это значение равно NULL.|  
|**estimated_changes**|**int**|Оценка количества изменений строк, которые должны быть применены к статье.|  
|**relative_cost**|**decimal**|Время, затраченное на применение изменений для статьи, по отношению к общему времени выполнения сеанса.|  
  
## <a name="see-also"></a>См. также:  
 [Таблицы репликации (Transact-SQL)](../../relational-databases/system-tables/replication-tables-transact-sql.md)  
  
  
