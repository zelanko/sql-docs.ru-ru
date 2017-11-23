---
title: "IHpublisherindexes (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
f1_keywords:
- IHpublisherindexes
- IHpublisherindexes_TSQL
dev_langs: TSQL
helpviewer_keywords: IHpublisherindexes system table
ms.assetid: 6008ef89-eeb9-46dc-93a2-f7623298cf0f
caps.latest.revision: "12"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4e8bf3c3e201c817fa76138df488eec70afb1173
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="ihpublisherindexes-transact-sql"></a>IHpublisherindexes (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **IHpublisherindexes** системная таблица содержит по одной строке на каждый индекс, реплицированный с отличных от издателей SQL Server с помощью текущего распространителя. Эта таблица хранится в базе данных распространителя.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**publisherindex_id**|**int**|Идентифицирует опубликованный индекс.|  
|**table_id**|**int**|Идентифицирует таблицу из [IHpublishertables](../../relational-databases/system-tables/ihpublishertables-transact-sql.md) , которой принадлежит индекс.|  
|**publisher_id**|**smallint**|Определяет, отличном от издателя SQL Server из которой публикуется индекс.|  
|**name**|**sysname**|Имя опубликованного индекса.|  
|**type**|**nvarchar(255)**|Поддерживаемый тип индекса из [IHindextypes](../../relational-databases/system-tables/ihindextypes-transact-sql.md) системной таблицы.|  
  
## <a name="see-also"></a>См. также:  
 [Разнородная репликация базы данных](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [Таблицы репликации &#40; Transact-SQL &#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
