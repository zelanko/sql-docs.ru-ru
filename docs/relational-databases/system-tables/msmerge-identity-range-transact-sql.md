---
title: "MSmerge_identity_range (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- MSmerge_identity_range_TSQL
- MSmerge_identity_range
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_identity_range system table
ms.assetid: 493a2028-88a0-4e83-ad89-ae5661d9f477
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ec799b6fcf16f4cb7f0146c6e01915d7e40d464a
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="msmergeidentityrange-transact-sql"></a>MSmerge_identity_range (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSmerge_identity_range** таблица используется для отслеживания числовых диапазонов, назначенных столбцам идентификаторов для подписок на публикации, репликация которых автоматически управляет этими назначениями диапазонов. Эта таблица хранится в базах данных публикации и подписки.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**subid**|**uniqueidentifier**|Уникальный идентификатор данной подписки.|  
|**artid**|**uniqueidentifier**|Уникальный идентификационный номер данной статьи.|  
|**range_begin**|**numeric(38)**|Значение идентификатора в начале текущего диапазона.|  
|**range_end**|**numeric(38)**|Значение идентификатора в конце текущего диапазона.|  
|**next_range_begin**|**numeric(38)**|Значение идентификатора в начале следующего назначенного диапазона.|  
|**next_range_end**|**numeric(38)**|Значение идентификатора в конце следующего назначенного диапазона.|  
|**is_pub_range**|**bit**|Значение **1** Если диапазон идентификаторов назначен публикации.|  
|**max_used**|**numeric(38)**|Максимальное значение идентификатора, которое может быть назначено.|  
  
## <a name="see-also"></a>См. также:  
 [Таблицы репликации &#40; Transact-SQL &#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
