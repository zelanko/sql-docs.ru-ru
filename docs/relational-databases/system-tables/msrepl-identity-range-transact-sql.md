---
title: MSrepl_identity_range (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- MSrepl_identity_range_TSQL
- MSrepl_identity_range
dev_langs:
- TSQL
helpviewer_keywords:
- MSrepl_identity_range system table
ms.assetid: 6e92a8e8-7667-4c98-b1c4-46735bac50d8
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 5d93e005e4774daebd967518d694d0cb67516280
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47704052"
---
# <a name="msreplidentityrange-transact-sql"></a>MSrepl_identity_range (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSrepl_identity_range** таблицы предоставляет поддержку управления диапазонами идентификаторов. Эта таблица хранится в базах данных публикации, распространителя и подписки.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**издатель**|**sysname**|Имя издателя.|  
|**publisher_db**|**sysname**|Имя базы данных публикации.|  
|**TableName**|**sysname**|Имя таблицы.|  
|**identity_support**|**int**|Определяет, включена ли автоматическая обработка диапазона идентификаторов. Значение 0 указывает, что автоматическая обработка диапазона идентификаторов отключена.|  
|**next_seed**|**bigint**|Если включен автоматический диапазон идентификаторов, указывает начальную точку следующего диапазона.|  
|**pub_range**|**bigint**|Размер диапазона идентификаторов издателя.|  
|**Диапазон**|**bigint**|Размер диапазона последовательных значений идентификаторов, выделяемого подписчикам.|  
|**max_identity**|**bigint**|Максимальный предел диапазона идентификаторов.|  
|**Пороговое значение**|**int**|Пороговое процентное значение диапазона идентификаторов.|  
|**current_max**|**bigint**|Текущее максимальное значение, которое может быть назначено, но не обязательно назначается.|  
  
## <a name="see-also"></a>См. также  
 [Таблицы репликации &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
