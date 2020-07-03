---
title: MSsubscription_articles (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSsubscription_articles
- MSsubscription_articles_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSsubscription_articles system table
ms.assetid: dbc1737f-261e-4017-b9cd-703b9fc4ac78
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: e44a88869e4a064896e15a1040e90d6ff66e9da3
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85889337"
---
# <a name="mssubscription_articles-transact-sql"></a>MSsubscription_articles (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Таблица **MSsubscription_articles** содержит сведения о статьях в подписке, поставленной в очередь. Данная таблица заполняется только для двух типов репликаций: как обновляемых посредством очередей, так и обновляемых немедленно, но которые стали обновляться через очереди из-за отработки отказа.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**agent_id**|**int**|Идентификатор агента, обслуживающего данную статью.|  
|**artid**|**int**|Идентификатор статьи из таблицы **sysarticles** .|  
|**статья**|**sysname**|Имя статьи из таблицы **sysarticles** .|  
|**dest_table**|**sysname**|Имя целевой таблицы из таблицы **sysarticles** .|  
|**владельцев**|**sysname**|Владелец подписки.|  
|**cft_table**|**sysname**|Имя таблицы конфликтов для данной статьи, для типа репликации, обновляемого посредством очередей.|  
  
## <a name="see-also"></a>См. также  
 [Таблицы репликации &#40;&#41;Transact-SQL](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
