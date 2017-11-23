---
title: "syssubscriptions (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
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
- syssubscriptions_TSQL
- syssubscriptions
dev_langs: TSQL
helpviewer_keywords: syssubscriptions system table
ms.assetid: 106c1707-e0e0-49b4-ba50-25380c40fab2
caps.latest.revision: "30"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c581c037ed78a82a194f74faae709bd81d6bd41c
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="syssubscriptions-transact-sql"></a>syssubscriptions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Содержит одну строку для каждой подписки в базе данных. Эта таблица хранится в базе данных публикации.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**artid**|**int**|Уникальный идентификатор статьи.|  
|**srvid**|**smallint**|Идентификатор сервера подписчика.|  
|**dest_db**|**sysname**|Имя целевой базы данных.|  
|**status**|**tinyint**|Состояние подписки.<br /><br /> **0** = неактивно.<br /><br /> **1** = подписка.<br /><br /> **2** = активно.|  
|**параметром sync_type, равным**|**tinyint**|Тип начальной синхронизации.<br /><br /> **1** = автоматическая.<br /><br /> **2** = нет|  
|**login_name**|**sysname**|Имя входа, использованное при добавлении подписки.|  
|**subscription_type**|**int**|Тип подписки.<br /><br /> 0 = принудительная, агент распространителя запускается на распространителе.<br /><br /> 1 = по запросу, агент распространителя запускается на подписчике.|  
|**distribution_jobid**|**binary(16)**|Идентификатор задания агента распространителя.|  
|**timestamp**|**timestamp**|Отметка времени.|  
|**update_mode**|**tinyint**|Режим обновления.<br /><br /> **0** = только для чтения.<br /><br /> **1** = немедленное обновление.|  
|**loopback_detection**|**bit**|Применяется к подпискам, которые являются частью двунаправленной топологии репликации транзакций. Механизм распознавания обратной связи определяет, отправляет ли агент распространителя транзакции, созданные в подписчике, обратно подписчику:<br /><br /> **0** = отправляет обратно.<br /><br /> **1** = не отправляет обратно.|  
|**queued_reinit**|**bit**|Определяет, помечена ли статья для инициализации или повторной инициализации. Значение **1** указывает, что подписанная статья помечена для инициализации или повторной инициализации.|  
|**nosync_type**|**tinyint**|Тип инициализации подписки:<br /><br /> **0** = автоматический (моментальный снимок)<br /><br /> **1** = поддержка только репликации<br /><br /> **2** = инициализация с помощью резервного копирования<br /><br /> **3** = инициализация начиная регистрационного номера транзакции в (журнале LSN)<br /><br /> Дополнительные сведения см. в разделе  **@sync_type**  параметр [sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md).|  
|**SRVNAME**|**sysname**|Имя подписчика.|  
  
## <a name="see-also"></a>См. также:  
 [Таблицы репликации &#40; Transact-SQL &#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
