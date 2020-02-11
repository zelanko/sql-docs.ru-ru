---
title: MSmerge_past_partition_mappings (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSmerge_past_partition_mappings
- MSmerge_past_partition_mappings_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_past_partition_mappings system table
ms.assetid: 06d54ff5-4d29-4eeb-b8be-64d032e53134
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7d56debf540de7b1e7f33f741fdd4c3f52d3f04a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67984889"
---
# <a name="msmerge_past_partition_mappings-transact-sql"></a>MSmerge_past_partition_mappings (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  В **MSmerge_past_partition_mappings** таблице хранится по одной строке для каждого идентификатора секции, для которой была указана измененная строка, которая была использована, но больше не принадлежит. Эта таблица хранится в базе данных публикации.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**publication_number**|**smallint**|Номер публикации, который хранится в **sysmergepublications**.|  
|**tablenick**|**int**|Псевдоним опубликованной таблицы.|  
|**rowguid**|**UNIQUEIDENTIFIER**|Идентификатор данной строки.|  
|**partition_id**|**int**|Идентификатор секции, к которой принадлежит строка. Значение равно-1, если изменение строки относится ко всем подписчикам.|  
|**поколения**|**bigint**|Этап создания, на котором произошло изменение секции.|  
|**reason**|**tinyint**|Только для внутреннего использования.|  
  
## <a name="see-also"></a>См. также:  
 [Таблицы репликации &#40;&#41;Transact-SQL](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации &#40;&#41;Transact-SQL](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
