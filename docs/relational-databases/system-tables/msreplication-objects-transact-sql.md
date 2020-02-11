---
title: MSreplication_objects (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSreplication_objects
- MSreplication_objects_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSreplication_objects system table
ms.assetid: 08f9710d-976d-448e-bead-ac9835e87bc5
author: stevestein
ms.author: sstein
ms.openlocfilehash: 058e1948fa79ed2ba250a4f4d504f95201d1e254
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68079083"
---
# <a name="msreplication_objects-transact-sql"></a>MSreplication_objects (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Таблица **MSreplication_objects** содержит по одной строке для каждого объекта, связанного с репликацией в базе данных подписчика. Эта таблица хранится в базе данных подписки.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**издателя**|**имеет sysname**|Имя издателя.|  
|**publisher_db**|**имеет sysname**|Имя базы данных издателя.|  
|**публикации**|**имеет sysname**|Имя публикации.|  
|**object_name**|**имеет sysname**|Имя объекта.|  
|**object_type**|**char (2)**|Тип объекта:<br /><br /> **u** = таблица.<br /><br /> **t** = триггер.<br /><br /> **p** = хранимая процедура.|  
|**рассмотрен**|**имеет sysname**|Имя статьи, с которой связан объект.|  
  
## <a name="see-also"></a>См. также:  
 [Таблицы репликации &#40;&#41;Transact-SQL](../../relational-databases/system-tables/replication-tables-transact-sql.md)  
  
  
