---
description: MSmerge_subscriptions (Transact-SQL)
title: MSmerge_subscriptions (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSmerge_subscriptions
- MSmerge_subscriptions_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_subscriptions system table
ms.assetid: cafd954a-92f8-44cb-a5d0-dce9aafa5ee1
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: e5648de8dd4d93e2f1fe1ed9290b9942f66cfe02
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88460420"
---
# <a name="msmerge_subscriptions-transact-sql"></a>MSmerge_subscriptions (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Таблица **MSmerge_subscriptions** содержит по одной строке для каждой подписки, обслуживаемой агент слияния на подписчике. Эта таблица хранится в базе данных распространителя.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**publisher_id**|**smallint**|Идентификатор издателя.|  
|**publisher_db**|**sysname**|Имя базы данных издателя.|  
|**publication_id**|**int**|Идентификатор публикации.|  
|**subscriber_id**|**smallint**|Идентификатор подписчика.|  
|**subscriber_db**|**sysname**|Имя базы данных подписки.|  
|**subscription_type**|**int**|Тип подписки.<br /><br /> 0 = принудительная<br /><br /> 1 = по запросу<br /><br /> 2 = анонимная|  
|**sync_type**|**tinyint**|Тип синхронизации:<br /><br /> 1 = автоматическая.<br /><br /> 2 = синхронизация отсутствует.|  
|**status**|**tinyint**|Состояние подписки.|  
|**subscription_time**|**datetime**|Время добавления подписки.|  
  
## <a name="see-also"></a>См. также:  
 [Таблицы репликации &#40;&#41;Transact-SQL ](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
