---
title: MSdistribution_history (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- MSdistribution_history
- MSdistribution_history_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSdistribution_history system table
ms.assetid: 55665bd2-9e1d-4efc-8f60-c63a24f66b28
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 8f1db56fafb069836c7fa2ecd2f85cfac38ae548
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47830222"
---
# <a name="msdistributionhistory-transact-sql"></a>MSdistribution_history (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSdistribution_history** таблица содержит строки журнала агентов распространителя, связанных с локальным распространителем. Эта таблица хранится в базе данных распространителя.  
  
## <a name="definition"></a>Определение  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**agent_id**|**int**|Идентификатор агента распространителя.|  
|**runstatus**|**int**|Состояние выполнения:<br /><br /> **1** = start.<br /><br /> **2** = успешно.<br /><br /> **3** = выполняется.<br /><br /> **4** = бездействует.<br /><br /> **5** = повторных попыток.<br /><br /> **6** = неуспешное завершение.|  
|**start_time**|**datetime**|Время для начала выполнения задания.|  
|**time**|**datetime**|Время занесения сообщения в журнал.|  
|**duration**|**int**|Продолжительность сеанса сообщения в секундах.|  
|**Комментарии**|**nvarchar(4000)**|Текст сообщения.|  
|**xact_seqno**|**varbinary(16)**|Номер последней обработанной последовательности транзакций.|  
|**current_delivery_rate**|**float**|Среднее число команд, доставляемых в секунду со времени последней записи в журнале.|  
|**current_delivery_latency**|**int**|Задержка между вводом команды в базе данных распространителя и ее выполнением на стороне подписчика со времени последней записи в журнале. В миллисекундах.|  
|**delivered_transactions**|**int**|Общее число транзакций, доставленных в течение сеанса.|  
|**delivered_commands**|**int**|Общее число команд, переданных за время сеанса.|  
|**average_commands**|**int**|Среднее число команд, переданных за время сеанса.|  
|**delivery_rate**|**float**|Среднее число доставленных команд в секунду.|  
|**delivery_latency**|**int**|Задержка между командой, подаваемой в базе данных распространителя и ее выполнением в базе данных подписчика. В миллисекундах.|  
|**total_delivered_commands**|**bigint**|Общее число команд, доставленных за время жизни подписки.|  
|**error_id**|**int**|Идентификатор ошибки в **MSrepl_error** системная таблица.|  
|**updateable_row**|**bit**|Значение **1** Если строку журнала может быть перезаписана.|  
|**timestamp**|**timestamp**|Столбец отметок времени этой таблицы.|  
  
## <a name="see-also"></a>См. также  
 [Таблицы репликации &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
