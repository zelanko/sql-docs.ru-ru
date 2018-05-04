---
title: sys.server_events (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- server_events_TSQL
- sys.server_events_TSQL
- server_events
- sys.server_events
dev_langs:
- TSQL
helpviewer_keywords:
- sys.server_events catalog view
ms.assetid: 996f6c9b-6426-4847-95d9-6b77541422be
caps.latest.revision: 32
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 951df93c30a8922bf5b282c0c1ce7bfbe805c395
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sysserverevents-transact-sql"></a>sys.server_events (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Содержит одну строку для каждого события, для которого запускается уведомление о событии или триггер DDL уровня сервера. Столбцы **object_id** и **тип** однозначно определяют событие сервера.  

  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|Идентификатор запускаемого уведомления о событии или триггера DDL уровня сервера.|  
|**type**|**int**|Тип события, которое привело к срабатыванию уведомления о событии или триггера DDL.|  
|**type_desc**|**nvarchar(60)**|Описание события, которое привело к срабатыванию уведомления о событии или триггера DDL.|  
|**event_group_type**|**int**|Группа событий, для которой создается уведомление о триггере или событии, или значение NULL, если уведомления для группы событий не создаются.|  
|**event_group_type_desc**|**nvarchar(60)**|Описание группы событий, на основе которой создается триггер или уведомление о событии, или значение NULL, если триггер или уведомление о событии не были созданы на основе группы событий|  
  
## <a name="permissions"></a>Разрешения  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также  
 [Представления каталога объектов (Transact-SQL)](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
