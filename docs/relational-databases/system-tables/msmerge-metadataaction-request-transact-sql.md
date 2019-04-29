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
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a46570a30254341fede1fb96fd368e94a09e58ea
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62910303"
---
# <a name="msmergemetadataactionrequest-transact-sql"></a>MSmerge_metadataaction_request (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSmerge_metadataaction_request** таблица хранит по одной строке для каждого компенсирующего действия. С помощью веб-синхронизации, если возникает ошибка и синхронизация должна быть повторена, вносится в **MSmerge_metadataaction_request**. Во время фазы передачи последующего слияния из этой таблицы извлекаются и выгружаются запросы для всех статей, принадлежащих синхронизируемой публикации. После успешного завершения синхронизации, соответствующая строка в **MSmerge_metadataaction_request** таблица удаляется. Эта таблица сохраняется на издателе в базе данных публикации и на подписчике в базе данных подписки.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**tablenick**|**int**|Псевдоним опубликованной таблицы.|  
|**столбец ROWGUID**|**uniqueidentifier**|Идентификатор данной строки.|  
|**action**|**tinyint**|Идентифицирует необходимое действие по исправлению ошибок.|  
|**Создание**|**bigint**|Значение поколения, для которого нужно действие по исправлению ошибок.|  
|**изменено**|**int**|Только для внутреннего использования.|  
  
## <a name="see-also"></a>См. также  
 [Таблицы репликации &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [Web Synchronization for Merge Replication](../../relational-databases/replication/web-synchronization-for-merge-replication.md)  
  
  
