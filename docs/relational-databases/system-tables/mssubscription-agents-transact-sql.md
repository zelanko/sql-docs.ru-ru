---
title: MSsubscription_agents (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSsubscription_agents
- MSsubscription_agents_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSsubscription_agents system table
ms.assetid: 86ad5891-0bef-4963-9381-7d5b45245a0c
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 4b1b8680343f233c35b704f3805b06ea9dc47c12
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2018
ms.locfileid: "52808506"
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
|**queue_id**|**sysname**|Идентификатор [!INCLUDE[msCoName](../../includes/msconame-md.md)] сообщений очереди на издателе. *queue_id* присваивается **SQL** для на базе SQL обновляемые посредством очередей.|  
|**update_mode**|**tinyint**|Тип обновления:<br /><br /> **0** = только для чтения.<br /><br /> **1** = немедленное обновление.<br /><br /> **2** = обновление посредством очередей с помощью очереди сообщений.<br /><br /> **3** = немедленное обновление посредством очередей при отработке отказа с помощью очереди сообщений.<br /><br /> **4** = обновление посредством очереди SQL Server очереди.<br /><br /> **5** = немедленное обновление с отработкой отказа очередности обновления, с помощью очереди SQL Server.|  
|**failover_mode**|**bit**|Если выбрано обновление с отработкой отказа, может быть выбран следующий тип отработки отказа:<br /><br /> **0** = немедленное обновление, используется. Отработка отказа не включена.<br /><br /> **1** = в очереди используется обновление. Отработка отказа включена. Очередь, используемая для отработки отказа указывается в *update_mode* значение.|  
|**spid**|**int**|Идентификатор системного процесса для подключения, используемый агентом распространителя, выполняющимся в настоящее время или только что запущенным.|  
|**login_time**|**datetime**|Дата и время подключения агента распространителя, выполняющегося в настоящее время или только что запущенного.|  
|**allow_subscription_copy**|**bit**|Указывает, допускается ли возможность копирования базы данных подписки.|  
|**attach_state**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**attach_version**|**binary(16)**|Уникальный идентификатор, представляющий версию вложенной подписки.|  
|**last_sync_status**|**int**|Последнее состояние выполнения агента распространителя, выполняющегося в настоящее время или только что запущенного. Состояние может быть следующим:<br /><br /> **1** = к работе.<br /><br /> **2** = выполнено успешно.<br /><br /> **3** = выполняется.<br /><br /> **4** = бездействует.<br /><br /> **5** = повторных попыток.<br /><br /> **6** = неуспешное завершение.|  
|**last_sync_summary**|**sysname**|Последнее сообщение агента распространителя, выполняющегося в настоящее время или только что запущенного. Состояние может быть следующим:<br /><br /> **К работе.**<br /><br /> **Успешно завершено.**<br /><br /> **В процессе выполнения.**<br /><br /> **Бездействует.**<br /><br /> **Повторите попытку.**<br /><br /> **Сбой.**|  
|**last_sync_time**|**datetime**|Дата и время, когда *last_sync_summary* и *last_sync_status* столбцы были обновлены. Агенты распространителя по запросу или анонимные, выполняющиеся как задания службы агента SqlServer, не обновляют эти столбцы. Вместо этого данные журнала заносятся в таблицу журнала заданий.|  
|**queue_server**|**sysname**|Только для внутреннего применения.|  
  
## <a name="see-also"></a>См. также  
 [Таблицы репликации &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [sp_helppullsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helppullsubscription-transact-sql.md)  
  
  
