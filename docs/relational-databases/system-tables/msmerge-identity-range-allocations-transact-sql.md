---
description: MSmerge_identity_range_allocations (Transact-SQL)
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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 1e258632e47664d88c6bfbe5f9b732672b5f9827
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88488815"
---
# <a name="msmerge_identity_range_allocations-transact-sql"></a>MSmerge_identity_range_allocations (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Таблица **MSmerge_identity_range_allocations** используется для мониторинга журнала назначений диапазонов идентификаторов как для издателей, так и для подписчиков для опубликованных статей. Эта таблица хранится в базе данных распространителя.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**publisher_id**|**smallint**|Идентификатор издателя.|  
|**publisher_db**|**nvarchar(128)**|Имя базы данных публикации.|  
|**публикации**|**nvarchar(128)**|Имя публикации.|  
|**статья**|**nvarchar(128)**|Имя статьи.|  
|**абонент**|**nvarchar(128)**|Имя подписчика.|  
|**subscriber_db**|**nvarchar(128)**|Имя базы данных подписки.|  
|**is_pub_range**|**bit**|Показывает, назначен ли диапазон идентификаторов издателю.|  
|**ranges_allocated**|**tinyint**|Число назначенных диапазонов идентификаторов.|  
|**range_begin**|**numeric (38)**|Начальное значение диапазона.|  
|**range_end**|**numeric (38)**|Конечное значение диапазона.|  
|**next_range_begin**|**numeric (38)**|Начальное значение следующего назначаемого диапазона.|  
|**next_range_end**|**numeric (38)**|Конечное значение следующего назначаемого диапазона.|  
|**max_used**|**numeric (38)**|Наибольшее использованное значение идентификатора.|  
|**time_of_allocation**|**datetime**|Время назначения.|  
  
## <a name="see-also"></a>См. также  
 [Таблицы репликации &#40;&#41;Transact-SQL ](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
