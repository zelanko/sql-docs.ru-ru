---
title: Мспубликатионсрешолдс (Transact-SQL) | Документация Майкрософт
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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 7b5ab784ea0c8cc34068773739c2a818a11aa5f1
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85751613"
---
# <a name="mspublicationthresholds-transact-sql"></a>MSpublicationthresholds (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Таблица **мспубликатионсрешолдс** используется для отслеживания метрик производительности репликации для публикации с одной строкой для каждого наблюдаемого порогового значения. Эта таблица хранится в базе данных распространителя.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**publication_id**|**int**|Указывает публикацию, для которой было установлено пороговое значение.|  
|**metric_id**|**int**|Определяет метрику производительности репликации, которая отслеживается в соответствии с определением в системной таблице [мсреплмонсрешолдметрикс](../../relational-databases/system-tables/msreplmonthresholdmetrics-transact-sql.md) .|  
|**value**|**sql_variant**|Пороговое значение измеряемой величины.|  
|**shouldalert**|**bit**|Значение **1** указывает, что предупреждение должно быть создано, если метрика превышает заданное пороговое значение.|  
|**IsEnabled**|**bit**|Значение **1** указывает, что мониторинг включен для этой метрики производительности репликации.|  
  
## <a name="see-also"></a>См. также  
 [Таблицы репликации &#40;&#41;Transact-SQL](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
