---
title: MSmerge_history (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSmerge_history_TSQL
- MSmerge_history
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_history system table
ms.assetid: 936195ad-ca07-41a8-a1a0-6699b6e63403
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 9ca908d080a77eb580f945856c3bc2a28a066f4a
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85736718"
---
# <a name="msmerge_history-transact-sql"></a>MSmerge_history (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Таблица **MSmerge_history** содержит строки журнала с подробным описанием результатов предыдущих сеансов задания агент слияния. В этой таблице содержится по одной строке для каждой строки вывода агента. Эта таблица используется в базе данных распространителя и всех базах данных подписки. В базе данных распространителя она содержит журнал для всех публикаций слиянием и подписок, использующих распространитель. В каждой базе данных подписки она содержит журнал для публикаций, на которые подписан подписчик.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**session_id**|**int**|Идентификатор задания агента слияния.|  
|**agent_id**|**int**|Идентификатор агента слияния.|  
|**обсуждения**|**nvarchar(255)**|Текст сообщения.|  
|**error_id**|**int**|Идентификатор ошибки в системной таблице [MSrepl_errors](../../relational-databases/system-tables/msrepl-errors-transact-sql.md) .|  
|**timestamp**|**timestamp**|Столбец отметок времени этой таблицы.|  
|**updatable_row**|**bit**|Задайте значение **1** , если строка журнала может быть перезаписана.|  
  
## <a name="see-also"></a>См. также  
 [Таблицы репликации &#40;&#41;Transact-SQL](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
