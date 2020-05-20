---
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
ms.openlocfilehash: 5ae1ee49522e55a632ff876251a831bc7b071a1c
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82832408"
---
# <a name="ihpublisherindexes-transact-sql"></a>IHpublisherindexes (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Системная таблица **ихпублишериндексес** содержит по одной строке для каждого индекса, реплицированного из издателей, отличных от SQL Server, использующих текущий распространитель. Эта таблица хранится в базе данных распространителя.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**publisherindex_id**|**int**|Идентифицирует опубликованный индекс.|  
|**table_id**|**int**|Определяет таблицу из [IHpublishertables](../../relational-databases/system-tables/ihpublishertables-transact-sql.md) , к которой принадлежит индекс.|  
|**publisher_id**|**smallint**|Идентифицирует издатель, отличный от SQL Server и публикующий данный индекс.|  
|**name**|**sysname**|Имя опубликованного индекса.|  
|**type**|**nvarchar(255)**|Поддерживаемый тип индекса из системной таблицы [ихиндекстипес](../../relational-databases/system-tables/ihindextypes-transact-sql.md) .|  
  
## <a name="see-also"></a>См. также  
 [Разнородная репликация базы данных](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [Таблицы репликации &#40;&#41;Transact-SQL](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
