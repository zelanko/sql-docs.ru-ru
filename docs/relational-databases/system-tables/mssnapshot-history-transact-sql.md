---
title: MSsnapshot_history (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSsnapshot_history
- MSsnapshot_history_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSsnapshot_history system table
ms.assetid: 56bf4128-1689-4963-9343-432dd0898d31
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ca24fdce036c4f63e49e7d0eb12054d2d67aa6aa
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2018
ms.locfileid: "52800726"
---
# <a name="mssnapshothistory-transact-sql"></a>MSsnapshot_history (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSsnapshot_history** таблица содержит строки журнала агентов моментальных снимков, связанных с локальным распространителем. Эта таблица хранится в базе данных распространителя.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**agent_id**|**int**|Идентификатор агента моментальных снимков.|  
|**runstatus**|**int**|Состояние выполнения:<br /><br /> **1** = start.<br /><br /> **2** = успешно.<br /><br /> **3** = выполняется.<br /><br /> **4** = бездействует.<br /><br /> **5** = повторных попыток.<br /><br /> **6** = неуспешное завершение.|  
|**start_time**|**datetime**|Время для начала выполнения задания.|  
|**time**|**datetime**|Время занесения сообщения в журнал.|  
|**duration**|**int**|Продолжительность сеанса сообщения в секундах.|  
|**Комментарии**|**nvarchar(255)**|Текст сообщения.|  
|**delivered_transactions**|**int**|Общее число транзакций, доставленных в течение сеанса.|  
|**delivered_commands**|**int**|Число доставленных команд в секунду.|  
|**delivery_rate**|**float(53)**|Среднее число доставленных команд в секунду.|  
|**error_id**|**int**|Идентификатор ошибки в [MSrepl_errors](../../relational-databases/system-tables/msrepl-errors-transact-sql.md) системная таблица.|  
|**timestamp**|**timestamp**|Столбец отметок времени этой таблицы.|  
  
## <a name="see-also"></a>См. также  
 [Таблицы репликации &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
