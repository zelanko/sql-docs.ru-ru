---
title: sysarticleupdates (Transact-SQL) | Документы Microsoft
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
- sysarticleupdates_TSQL
- sysarticleupdates
dev_langs:
- TSQL
helpviewer_keywords:
- sysarticleupdates system table
ms.assetid: 11a53bcd-a215-4d0b-9db8-233981d3ef5d
caps.latest.revision: 28
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2fe7ffac2dce09058796e5e41bd40b90d7f65faf
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="sysarticleupdates-transact-sql"></a>sysarticleupdates (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Содержит одну строку для каждой статьи, поддерживающей немедленно обновляемые подписки. Эта таблица хранится в реплицируемой базе данных.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**artid**|**int**|Столбец идентификаторов, который предоставляет уникальный идентификационный номер для статьи.|  
|**pubid**|**int**|Идентификатор публикации, к которой принадлежит статья.|  
|**sync_ins_proc**|**int**|Идентификатор хранимой процедуры, обрабатывающей синхронизирующие транзакции вставки. |  
|**sync_upd_proc**|**int**|Идентификатор хранимой процедуры, обрабатывающей синхронизирующие транзакции обновления. |  
|**sync_del_proc**|**int**|Идентификатор хранимой процедуры, обрабатывающей синхронизирующие транзакции удаления. |  
|**autogen**|**бит**|Показывает, что хранимые процедуры автоматически созданы.<br /><br /> **0** = false, созданы не автоматически.<br /><br /> **1** = true, автоматический.|  
|**sync_upd_trig**|**int**|Идентификатор триггера автоматического управления версиями в таблице статьи. |  
|**conflict_tableid**|**int**|Идентификатор таблицы конфликтов.|  
|**ins_conflict_proc**|**int**|Идентификатор процедуры, записывающей конфликты в **conflict_table**.|  
|**identity_support**|**бит**|Определяет, включена ли автоматическая обработка диапазона идентификаторов при использовании очереди обновления.  **0** поддержки диапазона означает, что ни одна учетная запись.|  
  
## <a name="see-also"></a>См. также  
 [Таблицы репликации &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
