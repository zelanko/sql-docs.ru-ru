---
title: "MSpeer_originatorid_history (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/04/2017
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
- MSpeer_originatorid_history_TSQL
- MSpeer_originatorid_history
dev_langs:
- TSQL
helpviewer_keywords:
- MSpeer_originatorid_history
ms.assetid: c1f53d0f-4080-43ff-be38-2b10395c68c9
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5c98612ad170d6b8490b222defa60a5cdc46672b
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="mspeeroriginatoridhistory-transact-sql"></a>MSpeer_originatorid_history (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Содержит по одной строке для каждого идентификатора инициатора, определенного в топологии. Сюда входят и идентификаторы для узлов, которые уже неактивны. Таблица используется при настройке нового узла для обнаружения конфликтов и позволяет гарантировать, что указанный идентификатор инициатора еще не использовался. Эта таблица хранится в базе данных публикации. Дополнительные сведения об обнаружении конфликтов см. в разделе [обнаружение конфликтов в-одноранговая репликация](../../relational-databases/replication/transactional/peer-to-peer-conflict-detection-in-peer-to-peer-replication.md).  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|originator_publication|**sysname**|Публикация, для которой задан идентификатор инициатора.|  
|originator_id|**int**|Число, идентифицирующее каждый из узлов топологии в целях обнаружения конфликтов.|  
|originator_node|**sysname**|Экземпляр сервера, для которого был задан идентификатор инициатора.|  
|originator_db|**sysname**|База данных публикации, для которой был задан идентификатор инициатора.|  
|originator_db_version|**int**|Показывает номер версии исходной базы данных.|  
|originator_version|**int**|Определяет номер версии издателя.|  
|inserted_date|**datetime**|Дата и время вставки в эту таблицу строки для идентификатора инициатора.|  
  
## <a name="see-also"></a>См. также:  
 [Таблицы репликации &#40; Transact-SQL &#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
