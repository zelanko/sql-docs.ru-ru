---
title: MSmerge_metadataaction_request (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSmerge_metadataaction_request
- MSmerge_metadataaction_request_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_metadataaction_request system table
ms.assetid: cd31a114-900a-4218-ab58-d959e547c647
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: aee900d9f34fb1e8f64db3687d6121a72a9e3b96
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85889731"
---
# <a name="msmerge_metadataaction_request-transact-sql"></a>MSmerge_metadataaction_request (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  В **MSmerge_metadataaction_request** таблице хранится по одной строке для каждого из необходимых компенсирующих действий. При использовании веб-синхронизации, если возникает ошибка и требуется повторная попытка синхронизации, выполняется запись в **MSmerge_metadataaction_request**. Во время фазы передачи последующего слияния из этой таблицы извлекаются и выгружаются запросы для всех статей, принадлежащих синхронизируемой публикации. После успешного завершения синхронизации соответствующая строка в **MSmerge_metadataaction_request** таблице удаляется. Эта таблица сохраняется на издателе в базе данных публикации и на подписчике в базе данных подписки.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**tablenick**|**int**|Псевдоним опубликованной таблицы.|  
|**rowguid**|**uniqueidentifier**|Идентификатор данной строки.|  
|**action**|**tinyint**|Идентифицирует необходимое действие по исправлению ошибок.|  
|**поколения**|**bigint**|Значение поколения, для которого нужно действие по исправлению ошибок.|  
|**изменившиеся**|**int**|Только для внутреннего использования.|  
  
## <a name="see-also"></a>См. также  
 [Таблицы репликации &#40;&#41;Transact-SQL](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации &#40;&#41;Transact-SQL](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [Web Synchronization for Merge Replication](../../relational-databases/replication/web-synchronization-for-merge-replication.md)  
  
  
