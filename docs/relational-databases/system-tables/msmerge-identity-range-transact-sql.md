---
description: MSmerge_identity_range (Transact-SQL)
title: MSmerge_identity_range (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSmerge_identity_range_TSQL
- MSmerge_identity_range
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_identity_range system table
ms.assetid: 493a2028-88a0-4e83-ad89-ae5661d9f477
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 4011fcc653e72327fbbd20b3b7d8ec1da135f4f9
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88463958"
---
# <a name="msmerge_identity_range-transact-sql"></a>MSmerge_identity_range (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Таблица **MSmerge_identity_range** используется для контроля числовых диапазонов, назначенных столбцам идентификаторов для подписок на публикации, для которых репликация автоматически управляет этими назначениями диапазонов. Эта таблица хранится в базах данных публикации и подписки.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**subid**|**uniqueidentifier**|Уникальный идентификатор данной подписки.|  
|**artid**|**uniqueidentifier**|Уникальный идентификационный номер данной статьи.|  
|**range_begin**|**numeric (38)**|Значение идентификатора в начале текущего диапазона.|  
|**range_end**|**numeric (38)**|Значение идентификатора в конце текущего диапазона.|  
|**next_range_begin**|**numeric (38)**|Значение идентификатора в начале следующего назначенного диапазона.|  
|**next_range_end**|**numeric (38)**|Значение идентификатора в конце следующего назначенного диапазона.|  
|**is_pub_range**|**bit**|Значение **1** , если диапазон идентификаторов назначен публикации.|  
|**max_used**|**numeric (38)**|Максимальное значение идентификатора, которое может быть назначено.|  
  
## <a name="see-also"></a>См. также  
 [Таблицы репликации &#40;&#41;Transact-SQL ](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
