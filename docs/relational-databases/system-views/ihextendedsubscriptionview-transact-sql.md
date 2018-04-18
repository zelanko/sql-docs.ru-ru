---
title: IHextendedSubscriptionView (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- IHextendedSubscriptionView_TSQL
- IHextendedSubscriptionView
dev_langs:
- TSQL
helpviewer_keywords:
- IHextendedSubscriptionView view
ms.assetid: 124756a4-463a-4a81-bf5b-de7e8ffc7a62
caps.latest.revision: 11
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c4425a28e270c738a2908e0595f796fdded3710a
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="ihextendedsubscriptionview-transact-sql"></a>IHextendedSubscriptionView (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **IHextendedSubscriptionView** отображает сведения о подписке на публикацию SQL Server. Это представление хранится в **распространения** базы данных.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**article_id**|**int**|Уникальный идентификатор статьи.|  
|**dest_db**|**sysname**|Имя целевой базы данных.|  
|**srvid**|**smallint**|Уникальный идентификатор подписчика.|  
|**login_name**|**sysname**|Имя входа, используемое для подключения к подписчику.|  
|**distribution_jobid**|**binary**|Идентифицирует задание агента распространителя.|  
|**publisher_database_id**|**int**|Определяет базу данных публикации.|  
|**subscription_type**|**int**|Тип подписки.<br /><br /> **0** = принудительно отправить — агент распространителя запускается на подписчике.<br /><br /> **1** = запрашивать — агент распространителя запускается на распространителе.|  
|**sync_type**|**tinyint**|Тип начальной синхронизации.<br /><br /> **1** = automatic<br /><br /> **2** = нет|  
|**status**|**tinyint**|Состояние подписки.<br /><br /> **0** = неактивно<br /><br /> **1** = подписка<br /><br /> **2** = активно|  
|**snapshot_seqno_flag**|**бит**|Указывает, используется ли порядковый номер моментального снимка.|  
|**independent_agent**|**бит**|Показывает наличие изолированного агента распространителя для этой публикации.<br /><br /> **0** = публикация использует общий агент распространителя, и каждой паре базы данных издателя базы данных/подписчика соответствует единственный общий агент.<br /><br /> **1** = отсутствует для этой публикации изолированный агент распространителя.|  
|**subscription_time**|**datetime**|Только для внутреннего применения.|  
|**loopback_detection**|**бит**|Применяется к подпискам, которые являются частью двунаправленной топологии репликации транзакций. Механизм распознавания обратной связи определяет, отправляет ли агент распространителя транзакции, созданные в подписчике, обратно подписчику:<br /><br /> **1** = не отправляет обратно.<br /><br /> **0** = отправляет обратно.|  
|**agent_id**|**int**|Уникальный идентификатор агента распространителя.|  
|**update_mode**|**tinyint**|Указывает один из следующих типов режима обновления:<br /><br /> **0** = только для чтения.<br /><br /> **1** = немедленное обновление.<br /><br /> **2** = обновление посредством очередей с помощью очереди сообщений.<br /><br /> **3** = немедленное обновление посредством очередей как отработки отказа с помощью очереди сообщений.<br /><br /> **4** = обновление посредством очереди SQL Server очереди.<br /><br /> **5** = немедленное обновление с обновлением отработки отказа, с помощью очереди SQL Server.|  
|**publisher_seqno**|**varbinary(16)**|Последовательный номер транзакции на издателе для этой подписки.|  
|**ss_cplt_seqno**|**varbinary(16)**|Последовательный номер, используемый для обозначения завершения одновременной обработки моментальных снимков.|  
  
## <a name="see-also"></a>См. также  
 [Разнородная репликация базы данных](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [Таблицы репликации &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
