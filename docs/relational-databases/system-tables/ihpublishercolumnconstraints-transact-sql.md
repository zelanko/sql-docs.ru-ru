---
title: IHpublishercolumnconstraints (Transact-SQL) | Документация Майкрософт
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
manager: craigg
ms.openlocfilehash: 89c6e254dfc163e75f16ccffaf97d3c2c8b222be
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2018
ms.locfileid: "52779586"
---
# <a name="ihpublishercolumnconstraints-transact-sql"></a>IHpublishercolumnconstraints (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **IHpublishercolumnconstraints** системная таблица сопоставляет столбцы публикации SQL Server в [IHpublishercolumns](../../relational-databases/system-tables/ihpublishercolumns-transact-sql.md) системная таблица ограничений в [IHpublisherconstraints ](../../relational-databases/system-tables/ihpublisherconstraints-transact-sql.md) системная таблица. Эта таблица хранится в базе данных распространителя.  
  
## <a name="definition"></a>Определение  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**publishercolumn_id**|**int**|Указывает столбец из [IHpublishercolumns](../../relational-databases/system-tables/ihpublishercolumns-transact-sql.md) с ассоциированным ограничением.|  
|**publisherconstraint_id**|**int**|Указывает ограничение из [IHpublisherconstraints](../../relational-databases/system-tables/ihpublisherconstraints-transact-sql.md) связанные со столбцом.|  
|**Если столбец indid равен**|**int**|Указывает местоположение столбца в опубликованной таблице.|  
  
## <a name="see-also"></a>См. также  
 [Разнородная репликация базы данных](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [Таблицы репликации &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
