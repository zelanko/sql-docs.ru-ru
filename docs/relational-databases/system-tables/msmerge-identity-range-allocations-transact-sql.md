---
title: MSmerge_identity_range_allocations (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSmerge_identity_range_allocations
- MSmerge_identity_range_allocations_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_identity_range_allocations system table
ms.assetid: 6362e35e-0ab3-4638-855b-1ce013f5fd6d
author: stevestein
ms.author: sstein
ms.openlocfilehash: de0325925bb1ad1626987361435056ff21a26be6
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68072649"
---
# <a name="msmerge_identity_range_allocations-transact-sql"></a>MSmerge_identity_range_allocations (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Таблица **MSmerge_identity_range_allocations** используется для мониторинга журнала назначений диапазонов идентификаторов как для издателей, так и для подписчиков для опубликованных статей. Эта таблица хранится в базе данных распространителя.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**publisher_id**|**smallint**|Идентификатор издателя.|  
|**publisher_db**|**nvarchar(128**|Имя базы данных публикации.|  
|**публикации**|**nvarchar(128**|Имя публикации.|  
|**рассмотрен**|**nvarchar(128**|Имя статьи.|  
|**абонент**|**nvarchar(128**|Имя подписчика.|  
|**subscriber_db**|**nvarchar(128**|Имя базы данных подписки.|  
|**is_pub_range**|**bit**|Показывает, назначен ли диапазон идентификаторов издателю.|  
|**ranges_allocated**|**tinyint**|Число назначенных диапазонов идентификаторов.|  
|**range_begin**|**numeric (38)**|Начальное значение диапазона.|  
|**range_end**|**numeric (38)**|Конечное значение диапазона.|  
|**next_range_begin**|**numeric (38)**|Начальное значение следующего назначаемого диапазона.|  
|**next_range_end**|**numeric (38)**|Конечное значение следующего назначаемого диапазона.|  
|**max_used**|**numeric (38)**|Наибольшее использованное значение идентификатора.|  
|**time_of_allocation**|**datetime**|Время назначения.|  
  
## <a name="see-also"></a>См. также:  
 [Таблицы репликации &#40;&#41;Transact-SQL](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации &#40;&#41;Transact-SQL](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
