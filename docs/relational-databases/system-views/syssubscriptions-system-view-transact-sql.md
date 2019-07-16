---
title: syssubscriptions (Системное представление) (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- syssubscriptions_TSQL
- syssubscriptions
dev_langs:
- TSQL
helpviewer_keywords:
- syssubscriptions view
ms.assetid: c9613858-9512-43a9-aa53-7ee8064f064c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3a50ce1b42c8963aac0bc152e08c6d39eec73eb2
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68094778"
---
# <a name="syssubscriptions-system-view-transact-sql"></a>syssubscriptions (системное представление) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **Syssubscriptions** представление отображает сведения о подписках. Это представление хранится в базе данных распространителя.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**artid**|**int**|Уникальный идентификатор статьи подписки.|  
|**srvid**|**smallint**|Идентификатор сервера подписчика.|  
|**dest_db**|**sysname**|Имя базы данных подписки.|  
|**status**|**tinyint**|Состояние подписки.<br /><br /> **0** = неактивно.<br /><br /> **1** = подписка.<br /><br /> **2** = активно.|  
|**sync_type**|**tinyint**|Тип начальной синхронизации.<br /><br /> **1** = автоматическая.<br /><br /> **2** = none.|  
|**login_name**|**sysname**|Имя входа, которое используется при подключении к издателю для добавления подписки.|  
|**subscription_type**|**int**|Тип подписки.<br /><br /> **0** = принудительно отправить — агент распространителя запускается на распространителе.<br /><br /> **1** = запрашивать — агент распространителя запускается на подписчике.|  
|**distribution_jobid**|**binary(16)**|Определяет задание агента распространителя, который используется для синхронизации подписки.|  
|**timestmap**|**timestamp**|Дата и время создания подписки.|  
|**update_mode**|**tinyint**|Режим обновления.<br /><br /> **0** = только для чтения.<br /><br /> **1** = немедленное обновление.|  
|**loopback_detection**|**bit**|Применяется к подпискам, которые являются частью двунаправленной топологии репликации транзакций. Механизм распознавания обратной связи определяет, отправляет ли агент распространителя транзакции, созданные в подписчике, обратно подписчику:<br /><br /> **0** = отправляет обратно.<br /><br /> **1** = не отправляет обратно.|  
|**queued_reinit**|**bit**|Определяет, помечена ли статья для инициализации или повторной инициализации. Значение **1** указывает, что подписанная статья помечена для инициализации или повторной инициализации.|  
|**nosync_type**|**tinyint**|Тип инициализации подписки:<br /><br /> **0** = автоматический (моментальный снимок)<br /><br /> **1** = поддержка только репликации<br /><br /> **2** = инициализация с помощью службы архивации<br /><br /> **3** = инициализация регистрационном номере (LSN)<br /><br /> Дополнительные сведения см. в разделе **@sync_type** параметр [sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md).<br /><br /> **3** = [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**SRVNAME**|**sysname**|Имя подписчика.|  
  
## <a name="see-also"></a>См. также  
 [Таблицы репликации &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [syssubscriptions (Transact-SQL)](../../relational-databases/system-tables/syssubscriptions-transact-sql.md)  
  
  
