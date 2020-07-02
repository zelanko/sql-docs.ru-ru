---
title: MStracer_history (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MStracer_history
- MStracer_history_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MStracer_history system table
ms.assetid: 97237a0c-d574-4b17-8a94-1a8730b31d98
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 82b0bf1e251d1a2a8b900845b93001296f814e80
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85758655"
---
# <a name="mstracer_history-transact-sql"></a>MStracer_history (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  В **MStracer_history** таблице хранится запись всех трассировочных токенов, полученных на подписчике. Эта таблица хранится в базе данных распространителя и используется при репликации для наблюдения за производительностью.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**parent_tracer_id**|**int**|Уникальный идентификатор трассировочного токена.|  
|**agent_id**|**int**|Агент, обрабатывавший запись трассировочного токена.|  
|**subscriber_commit**|**datetime**|Дата и время фиксации записи трассировочного токена у подписчика.|  
  
## <a name="see-also"></a>См. также  
 [Таблицы репликации &#40;&#41;Transact-SQL](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
