---
title: MSlogreader_history (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSlogreader_history_TSQL
- MSlogreader_history
dev_langs:
- TSQL
helpviewer_keywords:
- MSlogreader_history system table
ms.assetid: 2e399fa1-3591-4c1c-96b7-7964fe82c7c4
author: stevestein
ms.author: sstein
ms.openlocfilehash: 9fbd2240bdeba50d8ae41bce8d3a8d58b28de036
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "67907294"
---
# <a name="mslogreader_history-transact-sql"></a>MSlogreader_history (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Таблица **MSlogreader_history** содержит строки журнала для агентов чтения журнала, связанных с локальным распространителем. Эта таблица хранится в базе данных распространителя.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**agent_id**|**int**|Идентификатор агента чтения журнала.|  
|**runstatus**|**int**|Состояние выполнения:<br /><br /> 1 = запуск;<br /><br /> 2 = успешное завершение;<br /><br /> 3 = выполняется;<br /><br /> 4 = бездействует;<br /><br /> 5 = повтор;<br /><br /> 6 = аварийное завершение.|  
|**start_time**|**datetime**|Время для начала выполнения задания.|  
|**time**|**datetime**|Время занесения сообщения в журнал.|  
|**duration**|**int**|Продолжительность сеанса сообщения в секундах.|  
|**обсуждения**|**nvarchar(255)**|Текст сообщения.|  
|**xact_seqno**|**varbinary (16)**|Номер последней обработанной последовательности транзакций.|  
|**delivery_time**|**int**|Время доставки первой транзакции.|  
|**delivered_transactions**|**int**|Общее число транзакций, доставленных в течение сеанса.|  
|**delivered_commands**|**int**|Общее число команд, переданных за время сеанса.|  
|**average_commands**|**int**|Среднее число команд, переданных за время сеанса.|  
|**delivery_rate**|**float**|Среднее число доставленных команд в секунду.|  
|**delivery_latency**|**int**|Задержка между попаданием команды в публикуемую базу данных и в базу данных распространителя. В миллисекундах.|  
|**error_id**|**int**|Идентификатор ошибки в системной таблице **MSrepl_error** .|  
|**timestamp**|**timestamp**|Столбец отметок времени этой таблицы.|  
|**updateable_row**|**bit**|Задайте значение **1** , если строка журнала может быть перезаписана.|  
  
## <a name="see-also"></a>См. также  
 [Таблицы репликации &#40;&#41;Transact-SQL](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
