---
description: MSpeer_lsns (Transact-SQL)
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
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 6b08e7631633f56cb2f697dad862378685ee635a
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/08/2020
ms.locfileid: "89545545"
---
# <a name="mspeer_lsns-transact-sql"></a>MSpeer_lsns (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Таблица **Mspeer_lsns** используется для отображения каждой транзакции в подписке в одноранговой топологии репликации. Эта таблица хранится в каждой базе данных публикации в одноранговой топологии репликации и в базе данных подписки всех подписчиков на одноранговую публикацию. Дополнительные сведения об этом типе топологии репликации транзакций см. в разделе [одноранговая репликация транзакций](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md). Эта таблица хранится в базе данных публикации.  
  
## <a name="definition"></a>Определение  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**идентификатор**|**int**|Определяет одноранговый номер LSN.|  
|**last_updated**|**datetime**|**Дата и время** , когда было произведено Последнее обновление строки.|  
|**правителю**|**sysname**|Имя издателя, начавшего транзакцию.|  
|**originator_db**|**sysname**|Имя базы данных, в которой была начата транзакция.|  
|**originator_publication**|**sysname**|Имя публикации, в которой была начата транзакция.|  
|**originator_publication_id**|**int**|Идентификатор публикации, в которой была начата транзакция.|  
|**originator_db_version**|**int**|Показывает номер версии исходной базы данных.|  
|**originator_lsn**|**int**|Идентифицирует LSN в исходной публикации.|  
|**originator_version**|**int**|Определяет номер версии издателя.|  
|**originator_id**|**smallint**|Указывает каждый узел в топологии с целью обнаружения конфликтов. Дополнительные сведения см. в разделе [Conflict Detection in Peer-to-Peer Replication](../../relational-databases/replication/transactional/peer-to-peer-conflict-detection-in-peer-to-peer-replication.md).|  
  
## <a name="see-also"></a>См. также:  
 [Таблицы репликации &#40;&#41;Transact-SQL ](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
