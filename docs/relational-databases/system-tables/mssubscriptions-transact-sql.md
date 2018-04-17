---
title: MSsubscriptions (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
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
- MSsubscriptions_TSQL
- MSsubscriptions
dev_langs:
- TSQL
helpviewer_keywords:
- MSsubscriptions system table
ms.assetid: b7e8301d-d115-41f6-8d4f-e0d25f453b25
caps.latest.revision: 18
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 65eec6696b85d904d61767c486d6ab42ba68a1ef
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="mssubscriptions-transact-sql"></a>MSsubscriptions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSsubscriptions** содержит по одной строке для каждой опубликованной статьи в подписке, предоставленной локальным распространителем. Эта таблица хранится в базе данных распространителя.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**publisher_database_id**|**int**|Идентификатор базы данных издателя.|  
|**publisher_id**|**smallint**|Идентификатор издателя.|  
|**publisher_db**|**sysname**|Имя базы данных издателя.|  
|**publication_id**|**int**|Идентификатор публикации.|  
|**article_id**|**int**|Идентификатор статьи.|  
|**subscriber_id**|**smallint**|Идентификатор подписчика.|  
|**subscriber_db**|**sysname**|Имя базы данных подписки.|  
|**subscription_type**|**int**|Тип подписки.<br /><br /> **0** = принудительно отправить.<br /><br /> **1** = по запросу.<br /><br /> **2** = анонимная.|  
|**sync_type**|**tinyint**|Тип синхронизации:<br /><br /> **1** = автоматическая.<br /><br /> **2** = нет синхронизации.|  
|**status**|**tinyint**|Состояние подписки.<br /><br /> **0** = неактивно.<br /><br /> **1** = подписка.<br /><br /> **2** = активно.|  
|**subscription_seqno**|**varbinary(16)**|Порядковый номер транзакции моментального снимка памяти.|  
|**snapshot_seqno_flag**|**бит**|Указывает источник порядкового номера транзакции снимка, где значение **1** означает, что **subscription_seqno** имеет порядковый номер моментального снимка.|  
|**independent_agent**|**бит**|Указывает, имеется ли для данной публикации изолированный агент распространителя.|  
|**subscription_time**|**datetime**|Только для внутреннего применения.|  
|**loopback_detection**|**бит**|Применяется к подпискам, которые являются частью двунаправленной топологии репликации транзакций. Механизм распознавания обратной связи определяет, отправляет ли агент распространителя транзакции, созданные в подписчике, обратно подписчику:<br /><br /> **1** = не отправляет обратно.<br /><br /> **0** = отправляет обратно.<br /><br /> Примечание: Этот столбец поддерживается только для обратной совместимости с функциями двунаправленной репликации в [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]. Для более поздних версий [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] следует использовать одноранговую репликацию. Дополнительные сведения см. в разделе [Peer-to-Peer Transactional Replication](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md).|  
|**agent_id**|**int**|Идентификатор агента.|  
|**update_mode**|**tinyint**|Тип обновления.|  
|**publisher_seqno**|**varbinary(16)**|Последовательный номер транзакции на издателе для этой подписки.|  
|**ss_cplt_seqno**|**varbinary(16)**|Последовательный номер, используемый для обозначения завершения одновременной обработки моментальных снимков.|  
  
## <a name="see-also"></a>См. также  
 [Таблицы репликации](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [sp_helpsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql.md)  
  
  
