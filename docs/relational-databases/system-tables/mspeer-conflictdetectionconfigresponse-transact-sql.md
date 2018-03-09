---
title: "MSpeer_conflictdetectionconfigresponse (Transact-SQL) | Документы Microsoft"
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
- MSpeer_conflictdetectionconfigresponse
- MSpeer_conflictdetectionconfigresponse_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSpeer_conflictdetectionconfigureresponse
ms.assetid: 2685fb66-731d-40f7-af4b-596b9222c5d4
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: cb96eb44f44e3a7a0d1e1e4bcd0b1ce8dc00cf5e
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="mspeerconflictdetectionconfigresponse-transact-sql"></a>MSpeer_conflictdetectionconfigresponse (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Используется в одноранговой репликации для сохранения ответа каждого из узлов на запрос настройки на уровне топологии. Эта таблица хранится в базе данных публикации.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|request_id|**int**|Идентифицирует запись запроса настройки конфликта в [MSpeer_conflictdetectionconfigrequest](../../relational-databases/system-tables/mspeer-conflictdetectionconfigrequest-transact-sql.md) таблицы.|  
|peer_node|**sysname**|Имя экземпляра сервера, сформировавшего ответ.|  
|peer_db|**sysname**|База данных подписки на одноранговом узле, сформировавшем ответ.|  
|peer_version|**sysname**|Определяет номер версии издателя.|  
|peer_db_version|**sysname**|Указывает номер версии одноранговой базы данных.|  
|is_peer|**bit**|Указывает, является ли узел подписчиком, доступным только для чтения. Значение **0** указанный подписчик, доступный только для чтения.|  
|conflict_detection_enabled|**bit**|Указывает, включено ли обнаружение конфликтов для топологии.|  
|originator_id|**varbinary(16)**|Указывает каждый узел в топологии с целью обнаружения конфликтов. Дополнительные сведения см. в разделе [Conflict Detection in Peer-to-Peer Replication](../../relational-databases/replication/transactional/peer-to-peer-conflict-detection-in-peer-to-peer-replication.md).|  
|peer_conflict_retention|**int**|Срок (в днях), в течение которого метаданные хранятся в таблицах конфликтов.|  
|peer_subscriptions|**XML**|Сведения об узле, сформировавшем ответ на запрос.|  
|progress_phase|**nvarchar(32)**|Определяет текущую стадию обработки как одно из следующих значений:<br /><br /> Запущено<br /><br /> Собраны данные о версии однорангового узла<br /><br /> Собранные данные о состоянии|  
|modified_date|**datetime**|Дата и время завершения стадии.|  
  
## <a name="see-also"></a>См. также:  
 [Таблицы репликации &#40; Transact-SQL &#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
