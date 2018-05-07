---
title: MSmerge_history (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- MSmerge_history_TSQL
- MSmerge_history
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_history system table
ms.assetid: 936195ad-ca07-41a8-a1a0-6699b6e63403
caps.latest.revision: 29
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 1e28c0aae7f29099ebef75d5c0aa7ef81eec0379
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="msmergehistory-transact-sql"></a>MSmerge_history (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSmerge_history** содержит строки журнала с подробными описаниями результатов предыдущих сеансов заданий агента слияния. В этой таблице содержится по одной строке для каждой строки вывода агента. Эта таблица используется в базе данных распространителя и всех базах данных подписки. В базе данных распространителя она содержит журнал для всех публикаций слиянием и подписок, использующих распространитель. В каждой базе данных подписки она содержит журнал для публикаций, на которые подписан подписчик.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**session_id**|**int**|Идентификатор задания агента слияния.|  
|**agent_id**|**int**|Идентификатор агента слияния.|  
|**Комментарии**|**nvarchar(255)**|Текст сообщения.|  
|**error_id**|**int**|Идентификатор ошибки в [MSrepl_errors](../../relational-databases/system-tables/msrepl-errors-transact-sql.md) системной таблицы.|  
|**timestamp**|**timestamp**|Столбец отметок времени этой таблицы.|  
|**updatable_row**|**бит**|Значение **1** Если строки журнала может быть перезаписан.|  
  
## <a name="see-also"></a>См. также  
 [Таблицы репликации &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
