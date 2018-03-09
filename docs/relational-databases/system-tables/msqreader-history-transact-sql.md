---
title: "MSqreader_history (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
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
- MSqreader_history
- MSqreader_history_TSQL
dev_langs: TSQL
helpviewer_keywords: MSqreader_history system table
ms.assetid: c5c91d39-513c-4a77-870b-c8ef74a1cd6b
caps.latest.revision: "15"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7c9615bb702c89d8b2a5be0087671df9d8a6a910
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="msqreaderhistory-transact-sql"></a>MSqreader_history (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSqreader_history** содержит строки журнала для агентов чтения очереди, связанные с локальным распространителем. Эта таблица хранится в базе данных распространителя.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**agent_id**|**int**|Идентификатор агента чтения очереди.|  
|**publication_id**|**int**|Идентификатор публикации.|  
|**runstatus**|**int**|Состояние выполнения агента:<br /><br /> **1** = выполнение начато.<br /><br /> **2** = успешно.<br /><br /> **3** = выполняется.<br /><br /> **4** = бездействует.<br /><br /> **5** = "Повторить".<br /><br /> **6** = неуспешное завершение.|  
|**start_time**|**datetime**|Дата и время начала сеанса агента.|  
|**time**|**datetime**|Дата и время последнего сообщения, записанного в журнал.|  
|**duration**|**int**|Продолжительность зарегистрированной активности сеанса в секундах.|  
|**комментарии**|**nvarchar(255)**|Описание.|  
|**transaction_id**|**nvarchar(40)**|Идентификатор транзакции, сохраненный с сообщением (если применимо).|  
|**transaction_status**|**int**|Состояние транзакции.|  
|**transactions_processed**|**int**|Совокупное число транзакций, обработанных за время сеанса.|  
|**commands_processed**|**int**|Совокупное число команд, обработанных за время сеанса.|  
|**delivery_rate**|**float(53)**|Среднее число доставленных команд в секунду.|  
|**transaction_rate**|**float(53)**|Скорость обработки транзакций.|  
|**подписчик**|**sysname**|Имя подписчика.|  
|**SubscriberDB**|**sysname**|Имя базы данных подписки.|  
|**error_id**|**int**|Если не равно нулю, то оно представляет [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сообщение об ошибке.|  
|**timestamp**|**timestamp**|Столбец отметок времени для данной таблицы.|  
  
## <a name="see-also"></a>См. также:  
 [Таблицы репликации &#40; Transact-SQL &#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
