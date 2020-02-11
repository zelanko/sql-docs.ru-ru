---
title: Мсдинамикснапшотвиевс (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSdynamicsnapshotviews_TSQL
- MSdynamicsnapshotviews
dev_langs:
- TSQL
helpviewer_keywords:
- MSdynamicsnapshotviews system table
ms.assetid: 4fc1822a-5d6e-4034-a2e2-363210232d3b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8de7dd1571f7b9082144e97c8b35d9a39d6cabe8
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67907321"
---
# <a name="msdynamicsnapshotviews-transact-sql"></a>MSdynamicsnapshotviews (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Таблица **мсдинамикснапшотвиевс** отслеживает все временные представления моментальных снимков отфильтрованных данных, созданные агентом моментальных снимков, и используется системой для очистки представлений в случае аварийного завершения работы агент SQL Server или агент моментальных снимков. Эта таблица хранится в базах данных публикации и подписки.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**dynamic_snapshot_view_name**|**имеет sysname**|Имя временного представления моментального снимка отфильтрованных данных.|  
  
## <a name="see-also"></a>См. также:  
 [Таблицы репликации &#40;&#41;Transact-SQL](../../relational-databases/system-tables/replication-tables-transact-sql.md)  
  
  
