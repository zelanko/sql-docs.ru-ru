---
title: MSarticles (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSarticles
- MSarticles_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSarticles system table
ms.assetid: 1acd79a5-b3e2-4161-9592-7acc2a41ba38
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 5d04b79bb2d7cb70e2e36261547e462e1a7f2742
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62817252"
---
# <a name="msarticles-transact-sql"></a>MSarticles (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSarticles** таблица содержит по одной строке для каждой статьи, реплицируемой издателем. Эта таблица хранится в базе данных распространителя.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**publisher_id**|**smallint**|Идентификатор издателя.|  
|**publisher_db**|**sysname**|Имя базы данных издателя.|  
|**publication_id**|**int**|Идентификатор публикации.|  
|**Статья**|**sysname**|Имя статьи.|  
|**article_id**|**int**|Идентификатор статьи.|  
|**destination_object**|**sysname**|Имя таблицы, созданной на стороне подписчика.|  
|**source_owner**|**sysname**|Имя владельца схемы исходной таблицы на стороне издателя.|  
|**source_object**|**sysname**|Имя исходного объекта, из которого добавляется статья.|  
|**Описание**|**nvarchar(255)**|Описание статьи.|  
|**destination_owner**|**sysname**|Имя владельца схемы таблицы, созданной на стороне подписчика.|  
  
## <a name="see-also"></a>См. также  
 [Таблицы репликации &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
