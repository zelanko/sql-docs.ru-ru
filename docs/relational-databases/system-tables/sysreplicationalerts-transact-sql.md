---
title: sysreplicationalerts (Transact-SQL) | Документы Microsoft
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
- sysreplicationalerts_TSQL
- sysreplicationalerts
dev_langs:
- TSQL
helpviewer_keywords:
- sysreplicationalerts system table
ms.assetid: 6ed15828-8cca-4cf0-b2ff-1ecd0d8db11a
caps.latest.revision: 27
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 0b3cbb8ee462007f59eac4aea41a10e0253651b3
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="sysreplicationalerts-transact-sql"></a>sysreplicationalerts (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Содержит сведения об условиях срабатывания оповещения о репликации. Эта таблица хранится в **msdb** базы данных.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**alert_id**|**int**|Идентификатор предупреждения.|  
|**status**|**int**|Определяемое пользователем значение:<br /><br /> **0** = необслуживаемое.<br /><br /> **1** = обслуживание.|  
|**agent_type**|**int**|Тип агента:<br /><br /> **1** = агент моментальных снимков.<br /><br /> **2** = агент чтения журнала.<br /><br /> **3** = агент распространителя.<br /><br /> **4** = агент слияния.|  
|**agent_id**|**int**|Идентификатор агента из таблиц **MSsnapshot_agents**, **MSlogreader_agents**, **MSdistribution_agents**, или **MSmerge_agents**.|  
|**error_id**|**int**|Идентификатор ошибки, хранящийся в **MSrepl_errors**.|  
|**alert_error_code**|**int**|Идентификатор предупреждения, сработавшего при регистрации данной записи.|  
|**time**|**datetime**|Время добавления записи.|  
|**издатель**|**sysname**|Имя издателя, связанного с запустившим данное предупреждение агентом.|  
|**publisher_db**|**sysname**|Имя базы данных издателя, связанной с запустившим данное предупреждение агентом.|  
|**Публикации**|**sysname**|Имя публикации, связанной с запустившим данное предупреждение агентом.|  
|**publication_type**|**int**|Тип публикации:<br /><br /> **0** = моментальный снимок.<br /><br /> **1** = публикация транзакций.<br /><br /> **2** = публикация слиянием.|  
|**подписчик**|**sysname**|Имя подписчика, связанного с запустившим данное предупреждение агентом.|  
|**subscriber_db**|**sysname**|Имя базы данных подписчика, связанного с запустившим данное предупреждение агентом.|  
|**В статье**|**sysname**|Имя статьи, связанной с агентом, запустившим данное предупреждение.|  
|**destination_object**|**sysname**|Имя таблицы подписки, связанной с предупреждением.|  
|**source_object**|**sysname**|Имя опубликованной таблицы, связанной с предупреждением.|  
|**alert_error_text**|**ntext**|Текст предупреждения.|  
  
## <a name="see-also"></a>См. также  
 [Таблицы репликации &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
