---
title: MSreplication_queue (Transact-SQL) | Документация Майкрософт
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
- MSreplication_queue
- MSreplication_queue_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSreplication_queue system table
ms.assetid: 664bf817-8021-4417-96d6-2bb1e4baabff
caps.latest.revision: 27
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 663a07279a7bfe0ba9afe8ce6dc37cd74c71434c
ms.sourcegitcommit: a431ca21eac82117492d7b84c398ddb3fced53cc
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/17/2018
ms.locfileid: "39102142"
---
# <a name="msreplicationqueue-transact-sql"></a>MSreplication_queue (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSreplication_queue** таблица используется процессом репликации для хранения отложенных команд все обновления подписок посредством очередей, которые на основе SQL в очередь. Эта таблица хранится в базе данных подписки.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**издатель**|**sysname**|Имя издателя.|  
|**publisher_db**|**sysname**|Имя базы данных публикации.|  
|**публикации**|**sysname**|Имя публикации.|  
|**tranid**|**sysname**|Идентификатор транзакции, в которой была выполнена команда из очереди.|  
|**data**|**varbinary(8000)**|Упакованный поток байтов, содержащий сведения об отложенных командах.|  
|**datalen**|**int**|Длина данных параметра в байтах.|  
|**CommandType**|**int**|Тип отложенной команды:<br /><br /> 1 = пользовательская команда в транзакции.<br /><br /> 2 = команда синхронизации подписки.|  
|**insertdate**|**datetime**|Дата вставки.|  
|**orderkey**|**bigint**|Столбец идентификаторов, постепенно увеличивающийся.|  
|**cmdstate**|**bit**|Состояние команды:<br /><br /> 0 = завершена.<br /><br /> 1 = частично.|  
  
## <a name="see-also"></a>См. также  
 [Таблицы репликации &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
