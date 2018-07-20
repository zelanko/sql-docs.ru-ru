---
title: MSmerge_history (Transact-SQL) | Документация Майкрософт
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
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a46c6c1ebaad6cb24ce8ad6bd3185cda74768113
ms.sourcegitcommit: a431ca21eac82117492d7b84c398ddb3fced53cc
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/17/2018
ms.locfileid: "39103632"
---
# <a name="msmergehistory-transact-sql"></a>MSmerge_history (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSmerge_history** таблица содержит строки журнала с подробными описаниями результатов предыдущих сеансов заданий агента слияния. В этой таблице содержится по одной строке для каждой строки вывода агента. Эта таблица используется в базе данных распространителя и всех базах данных подписки. В базе данных распространителя она содержит журнал для всех публикаций слиянием и подписок, использующих распространитель. В каждой базе данных подписки она содержит журнал для публикаций, на которые подписан подписчик.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**session_id**|**int**|Идентификатор задания агента слияния.|  
|**agent_id**|**int**|Идентификатор агента слияния.|  
|**Комментарии**|**nvarchar(255)**|Текст сообщения.|  
|**error_id**|**int**|Идентификатор ошибки в [MSrepl_errors](../../relational-databases/system-tables/msrepl-errors-transact-sql.md) системная таблица.|  
|**timestamp**|**timestamp**|Столбец отметок времени этой таблицы.|  
|**updatable_row**|**bit**|Значение **1** Если строку журнала может быть перезаписана.|  
  
## <a name="see-also"></a>См. также  
 [Таблицы репликации &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
