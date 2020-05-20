---
title: MSmerge_dynamic_snapshots (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSmerge_dynamic_snapshots_TSQL
- MSmerge_dynamic_snapshots
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_dynamic_snapshots system table
ms.assetid: a5592b3c-731b-4fc9-ae4b-2602ed78248e
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 58aa7d6bb0789adcca406ac9733759c4d9762301
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82832306"
---
# <a name="msmerge_dynamic_snapshots-transact-sql"></a>Таблица MSmerge_dynamic_snapshots (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  В **MSmerge_dynamic_snapshots** таблице отслеживается расположение моментального снимка отфильтрованных данных для каждой секции, определенной для публикации слиянием с параметризованными фильтрами строк. Эта таблица хранится в базе данных **публикации** .  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**partition_id**|**int**|Идентификатор секции для слияния.|  
|**dynamic_snapshot_location**|**nvarchar(255)**|Расположение моментального снимка отфильтрованных данных секции.|  
|**last_updated**|**datetime**|Дата последнего обновления моментального снимка отфильтрованных данных.|  
  
## <a name="see-also"></a>См. также  
 [Таблицы репликации (Transact-SQL)](../../relational-databases/system-tables/replication-tables-transact-sql.md)  
  
  
