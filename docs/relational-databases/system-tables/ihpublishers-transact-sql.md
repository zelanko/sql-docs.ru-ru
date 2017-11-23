---
title: "IHpublishers (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/03/2017
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
- IHpublishers
- IHpublishers_TSQL
dev_langs: TSQL
helpviewer_keywords: IHpublishers system table
ms.assetid: 77007246-f10b-4b87-8edf-7afc3c2096af
caps.latest.revision: "23"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a53ef3960364ea40ccd1911f26a31270ffd9b09b
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="ihpublishers-transact-sql"></a>IHpublishers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **IHpublishers** системная таблица содержит по одной строке для каждого отличном от издателя SQL Server с помощью текущего распространителя. Эта таблица хранится в базе данных распространителя.  
  
## <a name="definition"></a>Определение  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**publisher_id**|**smallint**|Определяет, является SQL Server издателем.|  
|**поставщика**|**sysname**|Имя поставщика для базы данных SQL Server.|  
|**publisher_guid**|**uniqueidentifier**|Идентификатор GUID издателя, не являющегося SQL Server.|  
|**flush_request_time**|**datetime**|Содержит дату и время последнего изменения метаданных статьи, потребовавшего от агента чтения журнала обновления кэша метаданных.|  
|**version**|**sysname**|Текстовая строка, характеризующая версию из отличном от издателя SQL Server.|  
  
## <a name="see-also"></a>См. также:  
 [Разнородная репликация базы данных](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [Таблицы репликации &#40; Transact-SQL &#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации &#40; Transact-SQL &#41;](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [sp_adddistpublisher &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-adddistpublisher-transact-sql.md)   
 [sp_changedistpublisher (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-changedistpublisher-transact-sql.md)   
 [Хранимая процедура sp_helpdistpublisher &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-helpdistpublisher-transact-sql.md)  
  
  
