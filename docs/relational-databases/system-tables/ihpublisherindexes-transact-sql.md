---
description: IHpublisherindexes (Transact-SQL)
title: Ихпублишериндексес (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- IHpublisherindexes
- IHpublisherindexes_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- IHpublisherindexes system table
ms.assetid: 6008ef89-eeb9-46dc-93a2-f7623298cf0f
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: d86c2f362c3ddf0e6b6cb9e3ff8967f819339820
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88419148"
---
# <a name="ihpublisherindexes-transact-sql"></a>IHpublisherindexes (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Системная таблица **ихпублишериндексес** содержит по одной строке для каждого индекса, реплицированного из издателей, отличных от SQL Server, использующих текущий распространитель. Эта таблица хранится в базе данных распространителя.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**publisherindex_id**|**int**|Идентифицирует опубликованный индекс.|  
|**table_id**|**int**|Определяет таблицу из [IHpublishertables](../../relational-databases/system-tables/ihpublishertables-transact-sql.md) , к которой принадлежит индекс.|  
|**publisher_id**|**smallint**|Идентифицирует издатель, отличный от SQL Server и публикующий данный индекс.|  
|**name**|**sysname**|Имя опубликованного индекса.|  
|**type**|**nvarchar(255)**|Поддерживаемый тип индекса из системной таблицы [ихиндекстипес](../../relational-databases/system-tables/ihindextypes-transact-sql.md) .|  
  
## <a name="see-also"></a>См. также:  
 [Разнородная репликация базы данных](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [Таблицы репликации &#40;&#41;Transact-SQL ](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
