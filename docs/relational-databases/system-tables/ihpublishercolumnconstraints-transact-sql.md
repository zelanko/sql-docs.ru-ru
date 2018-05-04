---
title: IHpublishercolumnconstraints (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/03/2017
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
- IHpublishercolumnconstraints
- IHpublishercolumnconstraints_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- IHpublishercolumnconstraints system table
ms.assetid: d7a41da6-e067-430a-8da2-3f6745b8a4f3
caps.latest.revision: 26
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: a64def1d2115478d96d8432a38365b77a5396527
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="ihpublishercolumnconstraints-transact-sql"></a>IHpublishercolumnconstraints (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **IHpublishercolumnconstraints** системная таблица сопоставляет столбцы публикации SQL Server в [IHpublishercolumns](../../relational-databases/system-tables/ihpublishercolumns-transact-sql.md) ограничений в системной таблице [IHpublisherconstraints ](../../relational-databases/system-tables/ihpublisherconstraints-transact-sql.md) системной таблицы. Эта таблица хранится в базе данных распространителя.  
  
## <a name="definition"></a>Определение  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**publishercolumn_id**|**int**|Указывает столбец из [IHpublishercolumns](../../relational-databases/system-tables/ihpublishercolumns-transact-sql.md) с ассоциированным ограничением.|  
|**publisherconstraint_id**|**int**|Указывает ограничение из [IHpublisherconstraints](../../relational-databases/system-tables/ihpublisherconstraints-transact-sql.md) связанные со столбцом.|  
|**indid**|**int**|Указывает местоположение столбца в опубликованной таблице.|  
  
## <a name="see-also"></a>См. также  
 [Разнородная репликация базы данных](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [Таблицы репликации &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
