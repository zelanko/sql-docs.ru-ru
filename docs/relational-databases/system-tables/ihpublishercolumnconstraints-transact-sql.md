---
description: IHpublishercolumnconstraints (Transact-SQL)
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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: e683c32184ffa781fbd3e0b3a11d4e96343ee189
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88492815"
---
# <a name="ihpublishercolumnconstraints-transact-sql"></a>IHpublishercolumnconstraints (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Системная таблица **ихпублишерколумнконстраинтс** сопоставляет столбцы публикации, отличной от SQL Server, в системной таблице [ихпублишерколумнс](../../relational-databases/system-tables/ihpublishercolumns-transact-sql.md) с ограничениями в системной таблице [ихпублишерконстраинтс](../../relational-databases/system-tables/ihpublisherconstraints-transact-sql.md) . Эта таблица хранится в базе данных распространителя.  
  
## <a name="definition"></a>Определение  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**publishercolumn_id**|**int**|Определяет столбец из [ихпублишерколумнс](../../relational-databases/system-tables/ihpublishercolumns-transact-sql.md) с соответствующим ограничением.|  
|**publisherconstraint_id**|**int**|Определяет ограничение от [ихпублишерконстраинтс](../../relational-databases/system-tables/ihpublisherconstraints-transact-sql.md) , связанного со столбцом.|  
|**столбец indid**|**int**|Указывает местоположение столбца в опубликованной таблице.|  
  
## <a name="see-also"></a>См. также:  
 [Разнородная репликация базы данных](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [Таблицы репликации &#40;&#41;Transact-SQL ](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
