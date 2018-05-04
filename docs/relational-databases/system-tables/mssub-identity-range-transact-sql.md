---
title: MSsub_identity_range (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
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
- MSsub_identity_range_TSQL
- MSsub_identity_range
dev_langs:
- TSQL
helpviewer_keywords:
- MSsub_identity_range system table
ms.assetid: 26e20d28-14ed-44fc-af3b-4de386de4bb8
caps.latest.revision: 26
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 01008e8cd5bd740c333b483703ca5f27ab499c94
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="mssubidentityrange-transact-sql"></a>MSsub_identity_range (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSsub_identity_range** таблицы обеспечивает поддержку управления диапазонами идентификаторов для подписок. Эта таблица хранится в базе данных подписки.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**objID**|**int**|Идентификатор таблицы, содержащей столбец идентификаторов, управляемый репликацией.|  
|**диапазон**|**bigint**|Определяет размер интервала последовательных значений идентичности, которые могут быть назначены на подписчике при настройке.|  
|**last_seed**|**bigint**|Нижняя граница текущего диапазона.|  
|**Пороговое значение**|**int**|Процентное значение, определяющее, когда агентом распространителя выделяется новый диапазон идентификаторов. Если указанный процент значений в *пороговое значение* будет использовано, агент распространителя создает новый диапазон идентификаторов.|  
  
## <a name="see-also"></a>См. также  
 [Таблицы репликации &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
