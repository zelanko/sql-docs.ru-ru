---
title: MSrepl_identity_range (Transact-SQL) | Документация Майкрософт
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
- MSrepl_identity_range_TSQL
- MSrepl_identity_range
dev_langs:
- TSQL
helpviewer_keywords:
- MSrepl_identity_range system table
ms.assetid: 6e92a8e8-7667-4c98-b1c4-46735bac50d8
caps.latest.revision: 27
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 8cb090c20142a1e081b5af3401ba8e7a35a5a6c8
ms.sourcegitcommit: a431ca21eac82117492d7b84c398ddb3fced53cc
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/17/2018
ms.locfileid: "39101672"
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
  
  
