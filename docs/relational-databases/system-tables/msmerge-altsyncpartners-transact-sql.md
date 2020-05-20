---
title: MSmerge_altsyncpartners (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSmerge_altsyncpartners_TSQL
- MSmerge_altsyncpartners
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_altsyncpartners system table
ms.assetid: da51b0f8-5ad0-4aeb-96ed-2b3672a2a6e2
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: f5f46199af13e6ed0ab661c8d19d1a64710ab1d3
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82805534"
---
# <a name="msmerge_altsyncpartners-transact-sql"></a>MSmerge_altsyncpartners (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  В таблице **MSmerge_altsyncpartners** отслеживается Ассоциация того, кто является текущим партнером синхронизации для издателя. Эта таблица хранится в базах данных публикации и подписки.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**subid**|**uniqueidentifier**|Идентификатор изначального издателя.|  
|**alternate_subid**|**uniqueidentifier**|Идентификатор для подписчика, который является альтернативным участником синхронизации.|  
|**nописание**|**nvarchar(255)**|Описание альтернативного участника синхронизации.|  
  
## <a name="see-also"></a>См. также  
 [Таблицы репликации &#40;&#41;Transact-SQL](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
