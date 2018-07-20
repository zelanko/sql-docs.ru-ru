---
title: MSmerge_conflict_&lt;публикации&gt;_&lt;статье&gt; (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/16/2017
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
- MSmerge_conflict_publication_article_TSQL
- MSmerge_conflict_publication_article
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_conflict_publication_article system table
ms.assetid: dc4490b4-02d8-4dfc-98f5-0cf8de8e11be
caps.latest.revision: 31
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 0b5ec935f352e64678b98136953dfbb5041430a0
ms.sourcegitcommit: a431ca21eac82117492d7b84c398ddb3fced53cc
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/17/2018
ms.locfileid: "39101202"
---
# <a name="msmergeconflictltpublicationgtltarticlegt-transact-sql"></a>MSmerge_conflict_&lt;публикации&gt;_&lt;статье&gt; (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSmerge_conflict_*публикации*_ * статье*** таблица содержит сведения о конфликтующих строках или об изменениях строк, которые были отменены для обеспечения конвергенции данных. Для каждой реплицируемой таблицы в публикации существует таблица конфликтов, при этом к имени таблицы конфликтов добавляется имя публикации и имя статьи. Таблицы конфликтов по статьям расположены в базе данных, которая используется для занесения в журнал конфликтов; обычно ею является база данных публикации, однако при децентрализованном занесении в журнал конфликтов ею может быть и база данных подписки.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|***article_column_name***|**variable**|Представляет столбец в реплицируемой таблице. В данной системной таблице содержится по одному столбцу на каждый столбец статьи таблицы.|  
|**столбец ROWGUID**|**uniqueidentifier**|Идентификатор строки конфликта.|  
|**ModifiedDate**|**datetime**|Время возникновения конфликта.|  
|**origin_datasource_id**|**uniqueidentifier**|Подписка, для которой изменение строк было отменено или конфликт был потерян.|  
  
## <a name="see-also"></a>См. также  
 [Таблицы репликации &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
