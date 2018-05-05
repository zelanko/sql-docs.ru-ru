---
title: MSmerge_conflict_&lt;публикации&gt;_&lt;статьи&gt; (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/16/2017
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
- MSmerge_conflict_publication_article_TSQL
- MSmerge_conflict_publication_article
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_conflict_publication_article system table
ms.assetid: dc4490b4-02d8-4dfc-98f5-0cf8de8e11be
caps.latest.revision: 31
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 7b5c5f308d1987f1f8458001545b3a6e540889ce
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="msmergeconflictltpublicationgtltarticlegt-transact-sql"></a>MSmerge_conflict_&lt;публикации&gt;_&lt;статьи&gt; (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSmerge_conflict_*публикации*_ * статьи*** таблица содержит сведения о конфликтующих строках либо об изменениях строк, которые были отменены для обеспечения конвергенции данных. Для каждой реплицируемой таблицы в публикации существует таблица конфликтов, при этом к имени таблицы конфликтов добавляется имя публикации и имя статьи. Таблицы конфликтов по статьям расположены в базе данных, которая используется для занесения в журнал конфликтов; обычно ею является база данных публикации, однако при децентрализованном занесении в журнал конфликтов ею может быть и база данных подписки.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|***article_column_name***|**variable**|Представляет столбец в реплицируемой таблице. В данной системной таблице содержится по одному столбцу на каждый столбец статьи таблицы.|  
|**ROWGUID**|**uniqueidentifier**|Идентификатор строки конфликта.|  
|**ModifiedDate**|**datetime**|Время возникновения конфликта.|  
|**origin_datasource_id**|**uniqueidentifier**|Подписка, для которой изменение строк было отменено или конфликт был потерян.|  
  
## <a name="see-also"></a>См. также  
 [Таблицы репликации &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
