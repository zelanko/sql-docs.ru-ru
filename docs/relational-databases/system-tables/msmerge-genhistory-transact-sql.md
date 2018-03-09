---
title: "MSmerge_genhistory (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/04/2017
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
- MSmerge_genhistory_TSQL
- MSmerge_genhistory
dev_langs: TSQL
helpviewer_keywords: MSmerge_genhistory system table
ms.assetid: 475d08ae-eb8b-49de-afd6-33c96ab8004d
caps.latest.revision: "28"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 0408dd3ecc87598117466c03d7b474c23f1ce514
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="msmergegenhistory-transact-sql"></a>MSmerge_genhistory (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSmerge_genhistory** содержит по одной строке для каждого поколения, известны подписчика (в пределах срока хранения). Она используется, чтобы избежать отправки общих поколений при обменах и для повторной синхронизации подписчиков, восстановленных из резервных копий. Эта таблица хранится в базах данных публикации и подписки.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**guidsrc**|**uniqueidentifier**|Глобальный идентификатор изменений, связанных с поколением на подписчике.|  
|**pubid**|**uniqueidentifier**|Идентификатор публикации.|  
|**Создание**|**bigint**|Номер поколения.|  
|**art_nick**|**int**|Псевдоним статьи.|  
|**псевдонимы**|**varbinary(1001)**|Список псевдонимов других подписчиков, о которых известно, что они уже содержат это поколение. Используется, чтобы избежать отправки поколения подписчику, который уже получил изменения, содержащиеся в нем. Псевдонимы в списке псевдонимов хранятся в порядке сортировки для повышения эффективности поиска. Если существует больше псевдонимов, чем может поместиться в это поле, они не получат пользы от этой оптимизации.|  
|**colDate**|**datetime**|Дата, когда текущее поколение было добавлено в таблицу.|  
|**genstatus**|**tinyint**|Состояние поколения может быть:<br /><br /> **0** = открыто.<br /><br /> **1** = закрыто.<br /><br /> **2** = закрыто и порождено на другом подписчике.|  
|**changecount**|**int**|Количество изменений, отраженных в данном поколении|  
  
## <a name="see-also"></a>См. также:  
 [Таблицы репликации &#40; Transact-SQL &#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
