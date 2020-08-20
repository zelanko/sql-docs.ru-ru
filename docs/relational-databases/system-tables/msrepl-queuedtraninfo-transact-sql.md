---
description: MSrepl_queuedtraninfo (Transact-SQL)
title: MSrepl_queuedtraninfo (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSrepl_queuedtraninfo_TSQL
- MSrepl_queuedtraninfo
dev_langs:
- TSQL
helpviewer_keywords:
- MSrepl_queuedtraninfo system table
ms.assetid: af7a5baf-32ea-475f-b6b9-68c557b4980c
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: e95ac3bb96d726b1b02d0258f9364cc48a3af09d
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88480740"
---
# <a name="msrepl_queuedtraninfo-transact-sql"></a>MSrepl_queuedtraninfo (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Таблица **MSreplication_queuedtraninfo** используется процессом репликации для хранения сведений о командах в очереди, выданных всеми подписками, обновляемыми посредством очередей и использующих обновление посредством очередей на основе SQL. Эта таблица хранится в базе данных подписки.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**publisher**|**sysname**|Имя издателя.|  
|**publisher_db**|**sysname**|Имя базы данных публикации.|  
|**публикации**|**sysname**|Имя публикации.|  
|**транид**|**sysname**|Идентификатор транзакции, в которой была выполнена команда из очереди.|  
|**maxorderkey**|**bigint**|Только для внутреннего использования.|  
|**commandcount**|**bigint**|Только для внутреннего использования.|  
  
## <a name="see-also"></a>См. также  
 [Таблицы репликации &#40;&#41;Transact-SQL ](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
