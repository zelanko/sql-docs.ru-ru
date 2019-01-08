---
title: IHpublishercolumnindexes (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- IHpublishercolumnindexes
- IHpublishercolumnindexes_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- IHpublishercolumnindexes system table
ms.assetid: 95b95a1d-b502-4838-825f-82a456487e25
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 70fce3c0c919a9d898e0dadf9d56e5ae5adaa0a7
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2018
ms.locfileid: "52802486"
---
# <a name="ihpublishercolumnindexes-transact-sql"></a>IHpublishercolumnindexes (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **IHpublishercolumnindexes** системная таблица сопоставляет столбцы публикации SQL Server в [IHpublishercolumns](../../relational-databases/system-tables/ihpublishercolumns-transact-sql.md) с индексами в системной таблицы [IHpublisherindexes](../../relational-databases/system-tables/ihpublisherindexes-transact-sql.md)системная таблица. Эта таблица хранится в базе данных распространителя.  
  
## <a name="definition"></a>Определение  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**publishercolumn_id**|**int**|Указывает столбец из [IHpublishercolumns](../../relational-databases/system-tables/ihpublishercolumns-transact-sql.md) со связанным индексом.|  
|**publisherindex_id**|**int**|Определяет индекс [IHpublisherindexes](../../relational-databases/system-tables/ihpublisherindexes-transact-sql.md) таблицы, связанной со столбцом.|  
|**Если столбец indid равен**|**int**|Указывает местоположение столбца в опубликованной таблице.|  
  
## <a name="see-also"></a>См. также  
 [Разнородная репликация базы данных](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [Таблицы репликации &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
