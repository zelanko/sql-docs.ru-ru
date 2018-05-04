---
title: MSdistributiondbs (Transact-SQL) | Документы Microsoft
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
- MSdistributiondbs_TSQL
- MSdistributiondbs
dev_langs:
- TSQL
helpviewer_keywords:
- MSdistributiondbs system table
ms.assetid: d7ffa9df-bf1d-41b8-837e-b762c17c2764
caps.latest.revision: 18
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 55f7e90dead2285016cdbf3351fb9c7907e2f103
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="msdistributiondbs-transact-sql"></a>MSdistributiondbs (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSdistributiondbs** содержит по одной строке для каждой базы данных распространителя, определенных на локальном распространителе. Эта таблица хранится в **msdb** базы данных.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Имя базы данных распространителя.|  
|**min_distretention**|**int**|Минимальный период хранения в часах перед удалением транзакций.|  
|**max_distretention**|**int**|Максимальный период хранения в часах перед удалением транзакций.|  
|**history_retention**|**int**|Число часов хранения журнала.|  
  
## <a name="see-also"></a>См. также  
 [Таблицы репликации &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
