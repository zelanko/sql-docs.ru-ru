---
title: MSsub_identity_range (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSsub_identity_range_TSQL
- MSsub_identity_range
dev_langs:
- TSQL
helpviewer_keywords:
- MSsub_identity_range system table
ms.assetid: 26e20d28-14ed-44fc-af3b-4de386de4bb8
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 7a300f4be77bf6e63722f41553f0cb998cb48827
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2018
ms.locfileid: "52750466"
---
# <a name="mssubidentityrange-transact-sql"></a>MSsub_identity_range (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSsub_identity_range** таблицы предоставляет поддержку управления диапазонами идентификаторов для подписки. Эта таблица хранится в базе данных подписки.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**objID**|**int**|Идентификатор таблицы, содержащей столбец идентификаторов, управляемый репликацией.|  
|**Диапазон**|**bigint**|Определяет размер интервала последовательных значений идентичности, которые могут быть назначены на подписчике при настройке.|  
|**last_seed**|**bigint**|Нижняя граница текущего диапазона.|  
|**Пороговое значение**|**int**|Процентное значение, определяющее, когда агентом распространителя выделяется новый диапазон идентификаторов. При указании процентное отношение значений в *пороговое значение* будет использовано, агент распространителя создает новый диапазон идентификаторов.|  
  
## <a name="see-also"></a>См. также  
 [Таблицы репликации &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
