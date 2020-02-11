---
title: Ихпублишерколумнконстраинтс (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- IHpublishercolumnconstraints
- IHpublishercolumnconstraints_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- IHpublishercolumnconstraints system table
ms.assetid: d7a41da6-e067-430a-8da2-3f6745b8a4f3
author: stevestein
ms.author: sstein
ms.openlocfilehash: 58ef9c5e68e7d209262ebf43891ba5c1bcc4174f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67990282"
---
# <a name="ihpublishercolumnconstraints-transact-sql"></a>IHpublishercolumnconstraints (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Системная таблица **ихпублишерколумнконстраинтс** сопоставляет столбцы публикации, отличной от SQL Server, в системной таблице [ихпублишерколумнс](../../relational-databases/system-tables/ihpublishercolumns-transact-sql.md) с ограничениями в системной таблице [ихпублишерконстраинтс](../../relational-databases/system-tables/ihpublisherconstraints-transact-sql.md) . Эта таблица хранится в базе данных распространителя.  
  
## <a name="definition"></a>Определение  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**publishercolumn_id**|**int**|Определяет столбец из [ихпублишерколумнс](../../relational-databases/system-tables/ihpublishercolumns-transact-sql.md) с соответствующим ограничением.|  
|**publisherconstraint_id**|**int**|Определяет ограничение от [ихпублишерконстраинтс](../../relational-databases/system-tables/ihpublisherconstraints-transact-sql.md) , связанного со столбцом.|  
|**столбец indid**|**int**|Указывает местоположение столбца в опубликованной таблице.|  
  
## <a name="see-also"></a>См. также:  
 [Разнородная репликация базы данных](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [Таблицы репликации &#40;&#41;Transact-SQL](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации &#40;&#41;Transact-SQL](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
