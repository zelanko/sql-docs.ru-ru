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
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b1ba25e4f55debbe73a66de23986743a83d1feb5
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2018
ms.locfileid: "52765266"
---
# <a name="mstracerhistory-transact-sql"></a>MStracer_history (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MStracer_history** таблицы поддерживает запись всех трассировочных токенов, полученных на подписчике. Эта таблица хранится в базе данных распространителя и используется при репликации для наблюдения за производительностью.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**parent_tracer_id**|**int**|Уникальный идентификатор трассировочного токена.|  
|**agent_id**|**int**|Агент, обрабатывавший запись трассировочного токена.|  
|**subscriber_commit**|**datetime**|Дата и время фиксации записи трассировочного токена у подписчика.|  
  
## <a name="see-also"></a>См. также  
 [Таблицы репликации &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
