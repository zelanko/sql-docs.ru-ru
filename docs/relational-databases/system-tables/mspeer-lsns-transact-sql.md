---
title: MSpeer_lsns (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSpeer_lsns
- MSpeer_lsns_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSpeer_lsns system table
ms.assetid: 0ba33907-601b-4c3d-8099-2663f680a161
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 08926758b2d217bde6f858405ebde1c2b38b4d66
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63026745"
---
# <a name="mspeerlsns-transact-sql"></a>MSpeer_lsns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **Mspeer_lsns** таблица используется для сопоставления каждой транзакции с подпиской в топологии репликации peer-to-peer. Эта таблица хранится в каждой базе данных публикации в одноранговой топологии репликации и в базе данных подписки всех подписчиков на одноранговую публикацию. Дополнительные сведения об этом типе топологии репликации транзакций см. в разделе [репликации транзакций Peer-to-Peer](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md). Эта таблица хранится в базе данных публикации.  
  
## <a name="definition"></a>Определение  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**идентификатор**|**int**|Определяет одноранговый номер LSN.|  
|**last_updated**|**datetime**|**Datetime** на котором выполнялось последнее обновление строки.|  
|**Инициатор**|**sysname**|Имя издателя, начавшего транзакцию.|  
|**originator_db**|**sysname**|Имя базы данных, в которой была начата транзакция.|  
|**originator_publication**|**sysname**|Имя публикации, в которой была начата транзакция.|  
|**originator_publication_id**|**int**|Идентификатор публикации, в которой была начата транзакция.|  
|**originator_db_version**|**int**|Показывает номер версии исходной базы данных.|  
|**originator_lsn**|**int**|Идентифицирует LSN в исходной публикации.|  
|**originator_version**|**int**|Определяет номер версии издателя.|  
|**originator_id**|**smallint**|Указывает каждый узел в топологии с целью обнаружения конфликтов. Дополнительные сведения см. в разделе [Conflict Detection in Peer-to-Peer Replication](../../relational-databases/replication/transactional/peer-to-peer-conflict-detection-in-peer-to-peer-replication.md).|  
  
## <a name="see-also"></a>См. также  
 [Таблицы репликации &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
