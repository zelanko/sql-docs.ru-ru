---
title: "MStracer_tokens (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- MStracer_tokens_TSQL
- MStracer_tokens
dev_langs:
- TSQL
helpviewer_keywords:
- MStracer_tokens system table
ms.assetid: b273aa48-8188-4213-8e2c-311543c3236f
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1f0c91d79bbb85208e7c154787943fec4be9f039
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="mstracertokens-transact-sql"></a>MStracer_tokens (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MStracer_tokens** таблица поддерживает запись записях трассировочных токенов, вставленных в публикацию. Эта таблица хранится в базе данных распространителя и используется при репликации для наблюдения за производительностью.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**tracer_id**|**int**|Идентифицирует запись трассировочного токена.|  
|**publication_id**|**int**|Определяет публикацию, в которую была вставлена запись трассировочного токена.|  
|**publisher_commit**|**datetime**|Дата и время фиксации трассировочного токена на стороне издателя.|  
|**distributor_commit**|**datetime**|Дата и время фиксации трассировочного токена на стороне распространителя.|  
  
## <a name="see-also"></a>См. также:  
 [Таблицы репликации &#40; Transact-SQL &#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
