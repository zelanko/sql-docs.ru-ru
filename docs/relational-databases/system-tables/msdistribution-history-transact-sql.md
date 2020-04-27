---
title: MSdistribution_history (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
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
ms.openlocfilehash: 1053181486dba8c8119f9160d9c08cb8d2bbe56b
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "67907394"
---
# <a name="msdistribution_history-transact-sql"></a>MSdistribution_history (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Таблица **MSdistribution_history** содержит строки журнала для агентов распространителя, связанных с локальным распространителем. Эта таблица хранится в базе данных распространителя.  
  
## <a name="definition"></a>Определение  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**agent_id**|**int**|Идентификатор агента распространителя.|  
|**runstatus**|**int**|Состояние выполнения:<br /><br /> **1** = запуск.<br /><br /> **2** = выполнена.<br /><br /> **3** = выполняется.<br /><br /> **4** = бездействие.<br /><br /> **5** = повторная попытка.<br /><br /> **6** = ошибка.|  
|**start_time**|**datetime**|Время для начала выполнения задания.|  
|**time**|**datetime**|Время занесения сообщения в журнал.|  
|**duration**|**int**|Продолжительность сеанса сообщения в секундах.|  
|**обсуждения**|**nvarchar(4000)**|Текст сообщения.|  
|**xact_seqno**|**varbinary (16)**|Номер последней обработанной последовательности транзакций.|  
|**current_delivery_rate**|**float**|Среднее число команд, доставляемых в секунду со времени последней записи в журнале.|  
|**current_delivery_latency**|**int**|Задержка между вводом команды в базе данных распространителя и ее выполнением на стороне подписчика со времени последней записи в журнале. В миллисекундах.|  
|**delivered_transactions**|**int**|Общее число транзакций, доставленных в течение сеанса.|  
|**delivered_commands**|**int**|Общее число команд, переданных за время сеанса.|  
|**average_commands**|**int**|Среднее число команд, переданных за время сеанса.|  
|**delivery_rate**|**float**|Среднее число доставленных команд в секунду.|  
|**delivery_latency**|**int**|Задержка между командой, подаваемой в базе данных распространителя и ее выполнением в базе данных подписчика. В миллисекундах.|  
|**total_delivered_commands**|**bigint**|Общее число команд, доставленных за время жизни подписки.|  
|**error_id**|**int**|Идентификатор ошибки в системной таблице **MSrepl_error** .|  
|**updateable_row**|**bit**|Задайте значение **1** , если строка журнала может быть перезаписана.|  
|**timestamp**|**timestamp**|Столбец отметок времени этой таблицы.|  
  
## <a name="see-also"></a>См. также  
 [Таблицы репликации &#40;&#41;Transact-SQL](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
