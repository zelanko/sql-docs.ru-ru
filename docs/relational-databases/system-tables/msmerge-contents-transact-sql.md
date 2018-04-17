---
title: MSmerge_contents (Transact-SQL) | Документы Microsoft
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
- MSmerge_contents
- MSmerge_contents_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_contents system table
ms.assetid: 8d68a61a-683f-4b20-92f9-c0a8d9ba0ad1
caps.latest.revision: 19
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 48c2320fa26b86f9ee221a65e3a81eb809021cf4
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="msmergecontents-transact-sql"></a>MSmerge_contents (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSmerge_contents** содержит по одной строке для каждой строки, измененной в текущей базе данных с момента его публикации. Данная таблица используется процессом слияния для определения изменившихся строк. Эта таблица хранится в базах данных публикации и подписки.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**tablenick**|**int**|Псевдоним опубликованной таблицы.|  
|**ROWGUID**|**uniqueidentifier**|Идентификатор данной строки.|  
|**Создание**|**bigint**|Создание строки, **tablenick** и **rowguid**.|  
|**partchangegen**|**bigint**|Поколение, связанное с последним изменением данных, при котором могла измениться принадлежность строки к публикации с фильтром.|  
|**журнала обращений и преобразований**|**varbinary(501)**|Пары псевдонимов подписчиков и номеров версий, используемые для ведения журнала изменений данной строки.|  
|**colvl**|**varbinary(7489)**|Сведения о версии столбца.|  
|**маркер**|**uniqueidentifier**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**logical_record_parent_rowguid**|**uniqueidentifier**|Определяет строку родителя верхнего уровня в **MSmerge_contents** (по **rowguid**) для каждой соответствующей дочерней строки в логической записи.|  
|**logical_record_lineage**|**varbinary(501)**|Пары псевдонимов подписчиков и номеров версий, используемые для ведения журнала изменений родительской строки верхнего уровня в логической записи. Для всех дочерних строк в логической записи это значение равно NULL.|  
|**logical_relation_change_gen**|**bigint**|Поколение, связанное с последним изменением, вызвавшим перегруппировку в логической записи, при которой существующая строка была внесена в логическую запись или исключена оттуда.|  
  
## <a name="see-also"></a>См. также  
 [Таблицы репликации &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
