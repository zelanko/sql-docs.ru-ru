---
description: MSarticles (Transact-SQL)
title: Мсартиклес (Transact-SQL) | Документация Майкрософт
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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: f6a33127f1ba95fb17daff02ddcfaf64232cf94c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88463907"
---
# <a name="msarticles-transact-sql"></a>MSarticles (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Таблица **мсартиклес** содержит по одной строке для каждой статьи, реплицируемой издателем. Эта таблица хранится в базе данных распространителя.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**publisher_id**|**smallint**|Идентификатор издателя.|  
|**publisher_db**|**sysname**|Имя базы данных издателя.|  
|**publication_id**|**int**|Идентификатор публикации.|  
|**статья**|**sysname**|Имя статьи.|  
|**article_id**|**int**|Идентификатор статьи.|  
|**destination_object**|**sysname**|Имя таблицы, созданной на стороне подписчика.|  
|**source_owner**|**sysname**|Имя владельца схемы исходной таблицы на стороне издателя.|  
|**source_object**|**sysname**|Имя исходного объекта, из которого добавляется статья.|  
|**description**|**nvarchar(255)**|Описание статьи.|  
|**destination_owner**|**sysname**|Имя владельца схемы таблицы, созданной на стороне подписчика.|  
  
## <a name="see-also"></a>См. также:  
 [Таблицы репликации &#40;&#41;Transact-SQL ](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
