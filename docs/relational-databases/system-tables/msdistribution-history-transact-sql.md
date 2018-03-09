---
title: "MSdistribution_history (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/03/2017
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
- MSdistribution_history
- MSdistribution_history_TSQL
dev_langs: TSQL
helpviewer_keywords: MSdistribution_history system table
ms.assetid: 55665bd2-9e1d-4efc-8f60-c63a24f66b28
caps.latest.revision: "23"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: fa93b984ecd15cc3c0629e0eaaf6310142943dfe
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="msdistributionhistory-transact-sql"></a>MSdistribution_history (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSdistribution_history** содержит строки журнала агентов распространителя, связанных с локальным распространителем. Эта таблица хранится в базе данных распространителя.  
  
## <a name="definition"></a>Определение  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**agent_id**|**int**|Идентификатор агента распространителя.|  
|**runstatus**|**int**|Состояние выполнения:<br /><br /> **1** = выполнение начато.<br /><br /> **2** = успешно.<br /><br /> **3** = выполняется.<br /><br /> **4** = бездействует.<br /><br /> **5** = "Повторить".<br /><br /> **6** = неуспешное завершение.|  
|**start_time**|**datetime**|Время для начала выполнения задания.|  
|**time**|**datetime**|Время занесения сообщения в журнал.|  
|**duration**|**int**|Продолжительность сеанса сообщения в секундах.|  
|**комментарии**|**nvarchar(4000)**|Текст сообщения.|  
|**xact_seqno**|**varbinary(16)**|Номер последней обработанной последовательности транзакций.|  
|**current_delivery_rate**|**float**|Среднее число команд, доставляемых в секунду со времени последней записи в журнале.|  
|**current_delivery_latency**|**int**|Задержка между вводом команды в базе данных распространителя и ее выполнением на стороне подписчика со времени последней записи в журнале. В миллисекундах.|  
|**delivered_transactions**|**int**|Общее число транзакций, доставленных в течение сеанса.|  
|**delivered_commands**|**int**|Общее число команд, переданных за время сеанса.|  
|**average_commands**|**int**|Среднее число команд, переданных за время сеанса.|  
|**delivery_rate**|**float**|Среднее число доставленных команд в секунду.|  
|**delivery_latency**|**int**|Задержка между командой, подаваемой в базе данных распространителя и ее выполнением в базе данных подписчика. В миллисекундах.|  
|**total_delivered_commands**|**bigint**|Общее число команд, доставленных за время жизни подписки.|  
|**error_id**|**int**|Идентификатор ошибки в **MSrepl_error** системной таблицы.|  
|**updateable_row**|**bit**|Значение **1** Если строки журнала может быть перезаписан.|  
|**timestamp**|**timestamp**|Столбец отметок времени этой таблицы.|  
  
## <a name="see-also"></a>См. также:  
 [Таблицы репликации &#40; Transact-SQL &#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
