---
title: MScached_peer_lsns (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MScached_peer_lsns_TSQL
- MScached_peer_lsns
dev_langs:
- TSQL
helpviewer_keywords:
- MScached_peer_lsns system table
ms.assetid: f8b6089a-0230-45f9-8c34-9fe0d2a3a74e
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 406715f59a3a45184b9700d72331688911bc83e2
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62817033"
---
# <a name="mscachedpeerlsns-transact-sql"></a>MScached_peer_lsns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MScached_peer_lsns** таблица используется для отслеживания значений LSN в журнале транзакций, которые используются для определения, какие команды возвращаются к данному подписчику в peer-to-peer репликации. Эта таблица хранится в базе данных распространителя.  
  
## <a name="definition"></a>Определение  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**agent_id**|**int**|Идентификатор агента распространителя.|  
|**Инициатор**|**sysname**|Имя исходного издателя.|  
|**originator_db**|**sysname**|Имя базы данных исходной публикации.|  
|**originator_publication_id**|**int**|Идентифицирует исходную публикацию.|  
|**originator_db_version**|**int**|Показывает номер версии исходной базы данных.|  
|**originator_lsn**|**varbinary(16)**|LSN-номер транзакции.|  
  
## <a name="remarks"></a>Примечания  
 Значения LSN используются немедленно после вставки и не имеют последующего значения для системы.  
  
## <a name="see-also"></a>См. также  
 [Таблицы репликации &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
