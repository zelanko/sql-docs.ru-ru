---
title: MSrepl_identity_range (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
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
ms.openlocfilehash: 38f5037598e240585333d246a99c29c5fd8f40fe
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68079161"
---
# <a name="msrepl_identity_range-transact-sql"></a>MSrepl_identity_range (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSrepl_identity_range** таблица обеспечивает поддержку управления диапазонами идентификаторов. Эта таблица хранится в базах данных публикации, распространителя и подписки.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**издателя**|**имеет sysname**|Имя издателя.|  
|**publisher_db**|**имеет sysname**|Имя базы данных публикации.|  
|**TableName**|**имеет sysname**|Это имя таблицы.|  
|**identity_support**|**int**|Определяет, включена ли автоматическая обработка диапазона идентификаторов. Значение 0 указывает, что автоматическая обработка диапазона идентификаторов отключена.|  
|**next_seed**|**bigint**|Если включен автоматический диапазон идентификаторов, указывает начальную точку следующего диапазона.|  
|**pub_range**|**bigint**|Размер диапазона идентификаторов издателя.|  
|**разнообраз**|**bigint**|Размер диапазона последовательных значений идентификаторов, выделяемого подписчикам.|  
|**max_identity**|**bigint**|Максимальный предел диапазона идентификаторов.|  
|**значениями**|**int**|Пороговое процентное значение диапазона идентификаторов.|  
|**current_max**|**bigint**|Текущее максимальное значение, которое может быть назначено, но не обязательно назначается.|  
  
## <a name="see-also"></a>См. также:  
 [Таблицы репликации &#40;&#41;Transact-SQL](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации &#40;&#41;Transact-SQL](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
