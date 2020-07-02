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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: df899a146a8cf2c797f980baec1bb1792a8f2b6f
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85725445"
---
# <a name="mspub_identity_range-transact-sql"></a>MSpub_identity_range (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  **MSpub_identity_range** таблица обеспечивает поддержку управления диапазонами идентификаторов. Эта таблица хранится в базе данных публикации и базе данных подписки.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**objid**|**int**|Идентификатор таблицы, содержащей столбец идентификаторов, управляемый репликацией.|  
|**range**|**bigint**|Управляет размером диапазона последовательных значений идентификаторов, который будет назначен подписке при настройке.|  
|**pub_range**|**bigint**|Управляет размером диапазона последовательных значений идентификаторов, который будет назначен публикации при настройке.|  
|**current_pub_range**|**bigint**|Текущий диапазон, используемый публикацией. Оно может отличаться от *pub_range* при просмотре после изменения **sp_changearticle** и до следующей корректировки диапазона.|  
|**threshold**|**int**|Процентное значение, определяющее, когда агентом распространителя выделяется новый диапазон идентификаторов. При использовании процента значений, указанных в *пороговом значении* , агент распространения создает новый диапазон идентификаторов.|  
|**last_seed**|**bigint**|Нижняя граница текущего диапазона.|  
  
## <a name="see-also"></a>См. также  
 [Таблицы репликации &#40;&#41;Transact-SQL](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
