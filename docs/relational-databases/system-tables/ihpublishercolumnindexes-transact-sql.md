---
description: IHpublishercolumnindexes (Transact-SQL)
title: Ихпублишерколумниндексес (Transact-SQL) | Документация Майкрософт
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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 0efc9145416e468756bbe861e2e3d36631cd25bb
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88446598"
---
# <a name="ihpublishercolumnindexes-transact-sql"></a>IHpublishercolumnindexes (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Системная таблица **ихпублишерколумниндексес** сопоставляет столбцы публикации, отличной от SQL Server, в системной таблице [ихпублишерколумнс](../../relational-databases/system-tables/ihpublishercolumns-transact-sql.md) с индексами в системной таблице [ихпублишериндексес](../../relational-databases/system-tables/ihpublisherindexes-transact-sql.md) . Эта таблица хранится в базе данных распространителя.  
  
## <a name="definition"></a>Определение  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**publishercolumn_id**|**int**|Определяет столбец из [ихпублишерколумнс](../../relational-databases/system-tables/ihpublishercolumns-transact-sql.md) со связанным индексом.|  
|**publisherindex_id**|**int**|Определяет индекс из таблицы [ихпублишериндексес](../../relational-databases/system-tables/ihpublisherindexes-transact-sql.md) , связанной со столбцом.|  
|**столбец indid**|**int**|Указывает местоположение столбца в опубликованной таблице.|  
  
## <a name="see-also"></a>См. также:  
 [Разнородная репликация базы данных](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [Таблицы репликации &#40;&#41;Transact-SQL ](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
