---
title: MSrepl_queuedtraninfo (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/04/2017
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
- MSrepl_queuedtraninfo_TSQL
- MSrepl_queuedtraninfo
dev_langs:
- TSQL
helpviewer_keywords:
- MSrepl_queuedtraninfo system table
ms.assetid: af7a5baf-32ea-475f-b6b9-68c557b4980c
caps.latest.revision: 25
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 6f3975e2d4a48e6c68dcf5f369f3d477bb5a1a13
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="msreplqueuedtraninfo-transact-sql"></a>MSrepl_queuedtraninfo (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSreplication_queuedtraninfo** таблица используется процессом репликации для хранения сведений об отложенных команд все очереди обновляемых подписок, использующих обновление посредством очередей на основе SQL. Эта таблица хранится в базе данных подписки.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**издатель**|**sysname**|Имя издателя.|  
|**publisher_db**|**sysname**|Имя базы данных публикации.|  
|**Публикации**|**sysname**|Имя публикации.|  
|**Tranid**|**sysname**|Идентификатор транзакции, в которой была выполнена команда из очереди.|  
|**maxorderkey**|**bigint**|Только для внутреннего использования.|  
|**commandcount**|**bigint**|Только для внутреннего использования.|  
  
## <a name="see-also"></a>См. также  
 [Таблицы репликации &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
