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
ms.openlocfilehash: a7164afe24d15abf195ebff96e4e96a82877deae
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68079996"
---
# <a name="msreplication_subscriptions-transact-sql"></a>MSreplication_subscriptions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Таблица **MSreplication_subscriptions** содержит одну строку сведений о репликации для каждого агент распространения обслуживания базы данных локального подписчика. Эта таблица хранится в базе данных подписки.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**издателя**|**имеет sysname**|Имя издателя.|  
|**publisher_db**|**имеет sysname**|Имя базы данных издателя.|  
|**публикации**|**имеет sysname**|Имя публикации.|  
|**independent_agent**|**bit**|Указывает, имеется ли для данной публикации изолированный агент распространителя.|  
|**subscription_type**|**int**|Тип подписки.<br /><br /> 0 = принудительная<br /><br /> 1 = по запросу<br /><br /> 2 = анонимная|  
|**distribution_agent**|**имеет sysname**|Имя агента распространителя.|  
|**Таймаут**|**smalldatetime**|Время последнего обновления агентом распространителя.|  
|**nописание**|**nvarchar(255)**|Описание подписки.|  
|**transaction_timestamp**|**varbinary (16)**|Только для внутреннего использования.|  
|**update_mode**|**tinyint**|Тип обновления.|  
|**agent_id**|**двоичный (16)**|Идентификатор агента.|  
|**subscription_guid**|**двоичный (16)**|Глобальный идентификатор для версии подписки на эту публикацию.|  
|**subid**|**двоичный (16)**|Глобальный идентификатор для анонимной подписки.|  
|**immediate_sync**|**bit**|Указывает, создаются ли повторно файлы синхронизации при каждом запуске агента моментальных снимков.|  
  
## <a name="see-also"></a>См. также:  
 [Таблицы репликации &#40;&#41;Transact-SQL](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации &#40;&#41;Transact-SQL](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [sp_helpsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql.md)  
  
  
