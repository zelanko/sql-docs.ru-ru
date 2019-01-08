---
title: MSreplication_subscriptions (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSreplication_subscriptions
- MSreplication_subscriptions_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSreplication_subscriptions system table
ms.assetid: fd0c5843-4e9b-4448-8bfb-0a4067d1d8d1
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 0fa68012f419939c3f77980020795f23c4ca4672
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2018
ms.locfileid: "52794536"
---
# <a name="msreplicationsubscriptions-transact-sql"></a>MSreplication_subscriptions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSreplication_subscriptions** таблица содержит по одной строке сведений о репликации для каждого агента распространителя, обслуживающего локальной базы данных подписчика. Эта таблица хранится в базе данных подписки.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**издатель**|**sysname**|Имя издателя.|  
|**publisher_db**|**sysname**|Имя базы данных издателя.|  
|**публикации**|**sysname**|Имя публикации.|  
|**independent_agent**|**bit**|Указывает, имеется ли для данной публикации изолированный агент распространителя.|  
|**subscription_type**|**int**|Тип подписки.<br /><br /> 0 = принудительная<br /><br /> 1 = по запросу<br /><br /> 2 = анонимная|  
|**distribution_agent**|**sysname**|Имя агента распространителя.|  
|**Time**|**smalldatetime**|Время последнего обновления агентом распространителя.|  
|**Описание**|**nvarchar(255)**|Описание подписки.|  
|**transaction_timestamp**|**varbinary(16)**|Только для внутреннего использования.|  
|**update_mode**|**tinyint**|Тип обновления.|  
|**agent_id**|**binary(16)**|Идентификатор агента.|  
|**subscription_guid**|**binary(16)**|Глобальный идентификатор для версии подписки на эту публикацию.|  
|**subid**|**binary(16)**|Глобальный идентификатор для анонимной подписки.|  
|**immediate_sync**|**bit**|Указывает, создаются ли повторно файлы синхронизации при каждом запуске агента моментальных снимков.|  
  
## <a name="see-also"></a>См. также  
 [Таблицы репликации &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [sp_helpsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql.md)  
  
  
