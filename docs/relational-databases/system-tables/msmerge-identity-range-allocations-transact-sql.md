---
title: MSmerge_identity_range_allocations (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
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
- MSmerge_identity_range_allocations
- MSmerge_identity_range_allocations_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_identity_range_allocations system table
ms.assetid: 6362e35e-0ab3-4638-855b-1ce013f5fd6d
caps.latest.revision: 13
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 2f2a57c9122106d49dbb225a61482209cef907f3
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="msmergeidentityrangeallocations-transact-sql"></a>MSmerge_identity_range_allocations (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSmerge_identity_range_allocations** таблица используется для отслеживания назначений диапазонов идентификаторов для издателей и подписчиков, для опубликованных статей. Эта таблица хранится в базе данных распространителя.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**publisher_id**|**smallint**|Идентификатор издателя.|  
|**publisher_db**|**nvarchar(128)**|Имя базы данных публикации.|  
|**Публикации**|**nvarchar(128)**|Имя публикации.|  
|**В статье**|**nvarchar(128)**|Имя статьи.|  
|**подписчик**|**nvarchar(128)**|Имя подписчика.|  
|**subscriber_db**|**nvarchar(128)**|Имя базы данных подписки.|  
|**is_pub_range**|**бит**|Показывает, назначен ли диапазон идентификаторов издателю.|  
|**ranges_allocated**|**tinyint**|Число назначенных диапазонов идентификаторов.|  
|**range_begin**|**numeric(38)**|Начальное значение диапазона.|  
|**range_end**|**numeric(38)**|Конечное значение диапазона.|  
|**next_range_begin**|**numeric(38)**|Начальное значение следующего назначаемого диапазона.|  
|**next_range_end**|**numeric(38)**|Конечное значение следующего назначаемого диапазона.|  
|**max_used**|**numeric(38)**|Наибольшее использованное значение идентификатора.|  
|**time_of_allocation**|**datetime**|Время назначения.|  
  
## <a name="see-also"></a>См. также  
 [Таблицы репликации &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
