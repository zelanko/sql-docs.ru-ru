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
ms.openlocfilehash: 09f3fa61a1f79e98b8cd3330a03361b1b6a5c507
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68106368"
---
# <a name="msmerge_metadataaction_request-transact-sql"></a>MSmerge_metadataaction_request (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  В **MSmerge_metadataaction_request** таблице хранится по одной строке для каждого из необходимых компенсирующих действий. При использовании веб-синхронизации, если возникает ошибка и требуется повторная попытка синхронизации, выполняется запись в **MSmerge_metadataaction_request**. Во время фазы передачи последующего слияния из этой таблицы извлекаются и выгружаются запросы для всех статей, принадлежащих синхронизируемой публикации. После успешного завершения синхронизации соответствующая строка в **MSmerge_metadataaction_request** таблице удаляется. Эта таблица сохраняется на издателе в базе данных публикации и на подписчике в базе данных подписки.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**tablenick**|**int**|Псевдоним опубликованной таблицы.|  
|**rowguid**|**UNIQUEIDENTIFIER**|Идентификатор данной строки.|  
|**поддержки**|**tinyint**|Идентифицирует необходимое действие по исправлению ошибок.|  
|**поколения**|**bigint**|Значение поколения, для которого нужно действие по исправлению ошибок.|  
|**изменившиеся**|**int**|Только для внутреннего использования.|  
  
## <a name="see-also"></a>См. также:  
 [Таблицы репликации &#40;&#41;Transact-SQL](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации &#40;&#41;Transact-SQL](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [Веб-синхронизация для репликации слиянием](../../relational-databases/replication/web-synchronization-for-merge-replication.md)  
  
  
