---
description: MSsub_identity_range (Transact-SQL)
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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 7ec13e409f637063abbf5d2d3b99549a13d2d5ee
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88419098"
---
# <a name="mssub_identity_range-transact-sql"></a>MSsub_identity_range (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Таблица **MSsub_identity_range** предоставляет поддержку управления диапазонами идентификаторов для подписок. Эта таблица хранится в базе данных подписки.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**objid**|**int**|Идентификатор таблицы, содержащей столбец идентификаторов, управляемый репликацией.|  
|**range**|**bigint**|Определяет размер интервала последовательных значений идентичности, которые могут быть назначены на подписчике при настройке.|  
|**last_seed**|**bigint**|Нижняя граница текущего диапазона.|  
|**threshold**|**int**|Процентное значение, определяющее, когда агентом распространителя выделяется новый диапазон идентификаторов. При использовании процента значений, указанных в *пороговом значении* , агент распространения создает новый диапазон идентификаторов.|  
  
## <a name="see-also"></a>См. также:  
 [Таблицы репликации &#40;&#41;Transact-SQL ](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
