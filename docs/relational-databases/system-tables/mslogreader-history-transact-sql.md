---
title: MSlogreader_history (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
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
- MSlogreader_history_TSQL
- MSlogreader_history
dev_langs:
- TSQL
helpviewer_keywords:
- MSlogreader_history system table
ms.assetid: 2e399fa1-3591-4c1c-96b7-7964fe82c7c4
caps.latest.revision: 29
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 2971d515327089de4c528bdc9ee661b7598de5c9
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="mslogreaderhistory-transact-sql"></a>MSlogreader_history (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSlogreader_history** содержит строки журнала для агентов чтения журнала, связанные с локальным распространителем. Эта таблица хранится в базе данных распространителя.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**agent_id**|**int**|Идентификатор агента чтения журнала.|  
|**runstatus**|**int**|Состояние выполнения:<br /><br /> 1 = запуск;<br /><br /> 2 = успешное завершение;<br /><br /> 3 = выполняется;<br /><br /> 4 = Idle.<br /><br /> 5 = повтор;<br /><br /> 6 = аварийное завершение.|  
|**start_time**|**datetime**|Время для начала выполнения задания.|  
|**time**|**datetime**|Время занесения сообщения в журнал.|  
|**duration**|**int**|Продолжительность сеанса сообщения в секундах.|  
|**Комментарии**|**nvarchar(255)**|Текст сообщения.|  
|**xact_seqno**|**varbinary(16)**|Номер последней обработанной последовательности транзакций.|  
|**delivery_time**|**int**|Время доставки первой транзакции.|  
|**delivered_transactions**|**int**|Общее число транзакций, доставленных в течение сеанса.|  
|**delivered_commands**|**int**|Общее число команд, переданных за время сеанса.|  
|**average_commands**|**int**|Среднее число команд, переданных за время сеанса.|  
|**delivery_rate**|**float**|Среднее число доставленных команд в секунду.|  
|**delivery_latency**|**int**|Задержка между попаданием команды в публикуемую базу данных и в базу данных распространителя. В миллисекундах.|  
|**error_id**|**int**|Идентификатор ошибки в **MSrepl_error** системной таблицы.|  
|**timestamp**|**timestamp**|Столбец отметок времени этой таблицы.|  
|**updateable_row**|**бит**|Значение **1** Если строки журнала может быть перезаписан.|  
  
## <a name="see-also"></a>См. также  
 [Таблицы репликации &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
