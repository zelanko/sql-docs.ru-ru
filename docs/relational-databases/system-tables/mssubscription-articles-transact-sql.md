---
title: MSsubscription_articles (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
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
- MSsubscription_articles
- MSsubscription_articles_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSsubscription_articles system table
ms.assetid: dbc1737f-261e-4017-b9cd-703b9fc4ac78
caps.latest.revision: 26
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ff060482ddd1b9a678cdd37a9f4f2d1f26077272
ms.sourcegitcommit: a431ca21eac82117492d7b84c398ddb3fced53cc
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/17/2018
ms.locfileid: "39103162"
---
# <a name="mssubscriptionarticles-transact-sql"></a>MSsubscription_articles (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSsubscription_articles** таблица содержит сведения о статьях в подписке с очередями. Данная таблица заполняется только для двух типов репликаций: как обновляемых посредством очередей, так и обновляемых немедленно, но которые стали обновляться через очереди из-за отработки отказа.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**agent_id**|**int**|Идентификатор агента, обслуживающего данную статью.|  
|**artid**|**int**|Идентификатор статьи из **sysarticles** таблицы.|  
|**Статья**|**sysname**|Имя статьи из **sysarticles** таблицы.|  
|**dest_table**|**sysname**|Имя целевой таблицы из **sysarticles** таблицы.|  
|**Владелец**|**sysname**|Владелец подписки.|  
|**cft_table**|**sysname**|Имя таблицы конфликтов для данной статьи, для типа репликации, обновляемого посредством очередей.|  
  
## <a name="see-also"></a>См. также  
 [Таблицы репликации &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
