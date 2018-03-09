---
title: "MSrepl_commands (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/03/2017
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
- MSrepl_commands
- MSrepl_commands_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSrepl_commands system table
ms.assetid: 53b9f9cd-9429-47a0-aba2-908fc60e7036
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ee2da8ec88cc85128e13ef502c083358c623c92f
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="msreplcommands-transact-sql"></a>MSrepl_commands (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSrepl_commands** таблица содержит записи реплицированных команд. Эта таблица хранится в базе данных распространителя.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**publisher_database_id**|**int**|Идентификатор базы данных издателя.|  
|**xact_seqno**|**varbinary(16)**|Номер последовательности транзакции.|  
|**type**|**int**|Тип команды.|  
|**article_id**|**int**|Идентификатор статьи.|  
|**originator_id**|**int**|Идентификатор инициатора.|  
|**command_id**|**int**|Идентификатор команды.|  
|**partial_command**|**bit**|Показывает, частичная эта команда или нет.|  
|**команда**|**varbinary(1024)**|Значение команды.|  
|**hashKey**|**int**|Только для внутреннего использования.|  
|**originator_lsn**|**varbinary(16)**|Определяет номер LSN для команды в порождающей публикации. Используется для одноранговой репликации транзакций.|  
  
## <a name="see-also"></a>См. также:  
 [Таблицы репликации &#40; Transact-SQL &#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации &#40; Transact-SQL &#41;](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [sp_replcmds &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-replcmds-transact-sql.md)  
  
  
