---
title: MSpub_identity_range (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSpub_identity_range_TSQL
- MSpub_identity_range
dev_langs:
- TSQL
helpviewer_keywords:
- MSpub_identity_range system table
ms.assetid: 68746eef-32e1-42bc-aff0-9798cd0e88b8
author: stevestein
ms.author: sstein
ms.openlocfilehash: b1b204024d65e72eb65eefc9f63f914eab6ace29
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68032599"
---
# <a name="mspubidentityrange-transact-sql"></a>MSpub_identity_range (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSpub_identity_range** таблицы предоставляет поддержку управления диапазонами идентификаторов. Эта таблица хранится в базе данных публикации и базе данных подписки.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**objID**|**int**|Идентификатор таблицы, содержащей столбец идентификаторов, управляемый репликацией.|  
|**Диапазон**|**bigint**|Управляет размером диапазона последовательных значений идентификаторов, который будет назначен подписке при настройке.|  
|**pub_range**|**bigint**|Управляет размером диапазона последовательных значений идентификаторов, который будет назначен публикации при настройке.|  
|**current_pub_range**|**bigint**|Текущий диапазон, используемый публикацией. Он может отличаться от *pub_range* Если просматривается после изменения с **sp_changearticle** и перед следующей корректировкой диапазона.|  
|**Пороговое значение**|**int**|Процентное значение, определяющее, когда агентом распространителя выделяется новый диапазон идентификаторов. При указании процентное отношение значений в *пороговое значение* будет использовано, агент распространителя создает новый диапазон идентификаторов.|  
|**last_seed**|**bigint**|Нижняя граница текущего диапазона.|  
  
## <a name="see-also"></a>См. также  
 [Таблицы репликации &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
