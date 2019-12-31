---
title: MSmerge_conflict_publication_article (T-SQL)
description: Описывает MSmerge_conflict_publication_article хранимую процедуру, которая содержит сведения о строках с конфликтующими или измененными строками, которые были отменены для достижения конвергенции данных.
ms.custom: seo-lt-2019
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSmerge_conflict_publication_article_TSQL
- MSmerge_conflict_publication_article
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_conflict_publication_article system table
ms.assetid: dc4490b4-02d8-4dfc-98f5-0cf8de8e11be
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8d2c324f032f9cdd3206f6f2bed77fba74c2c0f5
ms.sourcegitcommit: 02d44167a1ee025ba925a6fefadeea966912954c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/20/2019
ms.locfileid: "75322127"
---
# <a name="msmerge_conflict_publication_article-transact-sql"></a>MSmerge_conflict_publication_article (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSmerge_conflict_publication_articleная** таблица содержит сведения о строках, которые были изменены или были отменены для достижения конвергенции данных. Для каждой реплицируемой таблицы в публикации существует таблица конфликтов, при этом к имени таблицы конфликтов добавляется имя публикации и имя статьи. Таблицы конфликтов по статьям расположены в базе данных, которая используется для занесения в журнал конфликтов; обычно ею является база данных публикации, однако при децентрализованном занесении в журнал конфликтов ею может быть и база данных подписки.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**_имя\_столбца\_статьи_**|**перемен**|Представляет столбец в реплицируемой таблице. В данной системной таблице содержится по одному столбцу на каждый столбец статьи таблицы.|  
|**rowguid**|**uniqueidentifier**|Идентификатор строки конфликта.|  
|**ModifiedDate**|**DateTime**|Время возникновения конфликта.|  
|**Идентификатор\_источника\_DataSource**|**uniqueidentifier**|Подписка, для которой изменение строк было отменено или конфликт был потерян.|  
  
## <a name="see-also"></a>См. также  
 [Таблицы репликации &#40;&#41;Transact-SQL](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации &#40;&#41;Transact-SQL](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
