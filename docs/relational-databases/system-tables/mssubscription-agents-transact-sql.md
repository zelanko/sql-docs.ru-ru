---
title: "MSsubscription_agents (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- MSsubscription_agents
- MSsubscription_agents_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSsubscription_agents system table
ms.assetid: 86ad5891-0bef-4963-9381-7d5b45245a0c
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 11ad8bb029c1a083a4490cfe62e2bacf54b37d01
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="mssubscriptionagents-transact-sql"></a>MSsubscription_agents (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSsubscription_agents** таблица используется агентом распространителя и триггерами обновляемых подписок для отслеживания свойств подписок. Эта таблица хранится в базе данных подписки.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**идентификатор**|**int**|Идентификатор строки.|  
|**издатель**|**sysname**|Имя издателя.|  
|**publisher_db**|**sysname**|Имя базы данных публикации.|  
|**публикации**|**sysname**|Имя публикации.|  
|**subscription_type**|**int**|Тип подписки:<br /><br /> 0 = принудительная<br /><br /> 1 = по запросу;<br /><br /> 2 = анонимная по запросу.|  
|**queue_id**|**sysname**|Идентификатор [!INCLUDE[msCoName](../../includes/msconame-md.md)] сообщений очереди на издателе. *queue_id* равно **SQL** для основанных на SQL обновляемые посредством очередей.|  
|**update_mode**|**tinyint**|Тип обновления:<br /><br /> **0** = только для чтения.<br /><br /> **1** = немедленное обновление.<br /><br /> **2** = обновление посредством очередей с помощью очереди сообщений.<br /><br /> **3** = немедленное обновление посредством очередей как отработки отказа с помощью очереди сообщений.<br /><br /> **4** = обновление посредством очереди SQL Server очереди.<br /><br /> **5** = немедленное обновление с обновлением отработки отказа, с помощью очереди SQL Server.|  
|**failover_mode**|**bit**|Если выбрано обновление с отработкой отказа, может быть выбран следующий тип отработки отказа:<br /><br /> **0** = немедленное обновление, используется. Отработка отказа не включена.<br /><br /> **1** = в очереди используется обновление. Отработка отказа включена. Очередь, используемая для отработки отказа задается в *update_mode* значение.|  
|**Идентификатор SPID**|**int**|Идентификатор системного процесса для подключения, используемый агентом распространителя, выполняющимся в настоящее время или только что запущенным.|  
|**login_time**|**datetime**|Дата и время подключения агента распространителя, выполняющегося в настоящее время или только что запущенного.|  
|**allow_subscription_copy**|**bit**|Указывает, допускается ли возможность копирования базы данных подписки.|  
|**attach_state**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**attach_version**|**binary(16)**|Уникальный идентификатор, представляющий версию вложенной подписки.|  
|**last_sync_status**|**int**|Последнее состояние выполнения агента распространителя, выполняющегося в настоящее время или только что запущенного. Состояние может быть следующим:<br /><br /> **1** = запущен.<br /><br /> **2** = успешно.<br /><br /> **3** = выполняется.<br /><br /> **4** = бездействует.<br /><br /> **5** = "Повторить".<br /><br /> **6** = неуспешное завершение.|  
|**last_sync_summary**|**sysname**|Последнее сообщение агента распространителя, выполняющегося в настоящее время или только что запущенного. Состояние может быть следующим:<br /><br /> **Запущен.**<br /><br /> **Успешно выполнен.**<br /><br /> **В данный момент.**<br /><br /> **Бездействует.**<br /><br /> **Повторите попытку.**<br /><br /> **Сбой.**|  
|**last_sync_time**|**datetime**|Дата и время, когда *last_sync_summary* и *last_sync_status* столбцы были обновлены. Агенты распространителя по запросу или анонимные, выполняющиеся как задания службы агента SqlServer, не обновляют эти столбцы. Вместо этого данные журнала заносятся в таблицу журнала заданий.|  
|**queue_server**|**sysname**|Только для внутреннего применения.|  
  
## <a name="see-also"></a>См. также:  
 [Таблицы репликации &#40; Transact-SQL &#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации &#40; Transact-SQL &#41;](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [sp_helppullsubscription &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-helppullsubscription-transact-sql.md)  
  
  
