---
title: Ихпублишерконстраинтс (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- IHpublisherconstraints
- IHpublisherconstraints_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- IHpublisherconstraints system table
ms.assetid: 537b1e1a-7228-4680-aa27-5ad7072ea01e
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: fa87169a0988336e8a00537a76126120fb95d196
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85773770"
---
# <a name="ihpublisherconstraints-transact-sql"></a>IHpublisherconstraints (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Системная таблица **ихпублишерконстраинтс** содержит по одной строке для каждого ограничения, реплицированного от издателей, отличных от SQL Server, с помощью текущего распространителя. Эта таблица хранится в базе данных распространителя.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**publisherconstraint_id**|**int**|Идентифицирует опубликованное ограничение.|  
|**table_id**|**int**|Определяет таблицу из [IHpublishertables](../../relational-databases/system-tables/ihpublishertables-transact-sql.md) , к которой принадлежит ограничение.|  
|**publisher_id**|**smallint**|Обозначает издателя, отличного от SQL Server, который публикует столбец.|  
|**Name**|**Имеет sysname**|Имя опубликованного ограничения.|  
|**Type**|**nvarchar(255)**|Поддерживаемый тип ограничения из системной таблицы [ихконстраинттипес](../../relational-databases/system-tables/ihconstrainttypes-transact-sql.md) .|  
  
## <a name="see-also"></a>См. также  
 [Разнородная репликация базы данных](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [Таблицы репликации &#40;&#41;Transact-SQL](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
