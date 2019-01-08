---
title: MSpublicationthresholds (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- mspublicationthresholds
- mspublicationthresholds_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSpublicationthresholds system table
ms.assetid: 9da3879f-b1f4-4ab4-abd4-a9a8ac395eba
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: cec59e0b5cb933822790a1f2497ca1bd5a3cbb2e
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2018
ms.locfileid: "52794169"
---
# <a name="mspublicationthresholds-transact-sql"></a>MSpublicationthresholds (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSpublicationthresholds** таблица используется для отслеживания метрик производительности репликации для публикации, по одной строке для каждого пороговому значению. Эта таблица хранится в базе данных распространителя.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**publication_id**|**int**|Указывает публикацию, для которой было установлено пороговое значение.|  
|**metric_id**|**int**|Определяет метрику производительности репликации отслеживаемых, как определено в [MSreplmonthresholdmetrics](../../relational-databases/system-tables/msreplmonthresholdmetrics-transact-sql.md) системная таблица.|  
|**value**|**sql_variant**|Пороговое значение измеряемой величины.|  
|**shouldalert**|**bit**|Значение **1** указывает, что должны создаваться оповещение, когда метрика превышает указанный порог.|  
|**IsEnabled**|**bit**|Значение **1** указывает, что наблюдение включено для этой метрики производительности репликации.|  
  
## <a name="see-also"></a>См. также  
 [Таблицы репликации &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
