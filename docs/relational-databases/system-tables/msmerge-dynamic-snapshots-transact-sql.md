---
title: "MSmerge_dynamic_snapshots (Transact-SQL) | Документы Microsoft"
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
- MSmerge_dynamic_snapshots_TSQL
- MSmerge_dynamic_snapshots
dev_langs: TSQL
helpviewer_keywords: MSmerge_dynamic_snapshots system table
ms.assetid: a5592b3c-731b-4fc9-ae4b-2602ed78248e
caps.latest.revision: "28"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: dacb740cf4eb64bc206bf324ceac81f32f57a860
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="msmergedynamicsnapshots-transact-sql"></a>Таблица MSmerge_dynamic_snapshots (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSmerge_dynamic_snapshots** таблица отслеживает расположение моментального снимка отфильтрованных данных для каждой секции, определенной для публикации слиянием с параметризованными фильтрами строк. Эта таблица хранится в **публикации** базы данных.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**partition_id**|**int**|Идентификатор секции для слияния.|  
|**размещение_динамического_моментального_снимка**|**nvarchar(255)**|Расположение моментального снимка отфильтрованных данных секции.|  
|**last_updated**|**datetime**|Дата последнего обновления моментального снимка отфильтрованных данных.|  
  
## <a name="see-also"></a>См. также:  
 [Таблицы репликации (Transact-SQL)](../../relational-databases/system-tables/replication-tables-transact-sql.md)  
  
  
