---
title: MSmerge_contents (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
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
- MSmerge_contents
- MSmerge_contents_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_contents system table
ms.assetid: 8d68a61a-683f-4b20-92f9-c0a8d9ba0ad1
caps.latest.revision: 19
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 4643b0ba6bdfd9eea4405be02ca481133f0db096
ms.sourcegitcommit: a431ca21eac82117492d7b84c398ddb3fced53cc
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/17/2018
ms.locfileid: "39101562"
---
# <a name="msmergecontents-transact-sql"></a>MSmerge_contents (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSmerge_contents** таблица содержит по одной строке для каждой строки, измененной в текущей базе данных с момента его публикации. Данная таблица используется процессом слияния для определения изменившихся строк. Эта таблица хранится в базах данных публикации и подписки.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**tablenick**|**int**|Псевдоним опубликованной таблицы.|  
|**столбец ROWGUID**|**uniqueidentifier**|Идентификатор данной строки.|  
|**Создание**|**bigint**|Создание строки, **tablenick** и **rowguid**.|  
|**partchangegen**|**bigint**|Поколение, связанное с последним изменением данных, при котором могла измениться принадлежность строки к публикации с фильтром.|  
|**журнала обращений и преобразований**|**Varbinary(501)**|Пары псевдонимов подписчиков и номеров версий, используемые для ведения журнала изменений данной строки.|  
|**colvl**|**varbinary(7489)**|Сведения о версии столбца.|  
|**маркер**|**uniqueidentifier**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**logical_record_parent_rowguid**|**uniqueidentifier**|Идентифицирует родительскую строку верхнего уровня в **MSmerge_contents** (с **rowguid**) для каждой соответствующей дочерней строки в логической записи.|  
|**logical_record_lineage**|**Varbinary(501)**|Пары псевдонимов подписчиков и номеров версий, используемые для ведения журнала изменений родительской строки верхнего уровня в логической записи. Для всех дочерних строк в логической записи это значение равно NULL.|  
|**logical_relation_change_gen**|**bigint**|Поколение, связанное с последним изменением, вызвавшим перегруппировку в логической записи, при которой существующая строка была внесена в логическую запись или исключена оттуда.|  
  
## <a name="see-also"></a>См. также  
 [Таблицы репликации &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
