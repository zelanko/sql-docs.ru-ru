---
description: MSsync_states (Transact-SQL)
title: MSsync_states (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSsync_states
- MSsync_states_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSsync_states system table
ms.assetid: b25e17e1-7718-432e-a442-c4946741d474
author: markingmyname
ms.author: maghan
ms.openlocfilehash: bc3ef439c3d5027e64eb988730c41c3f9bea12d9
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/08/2020
ms.locfileid: "89545494"
---
# <a name="mssync_states-transact-sql"></a>MSsync_states (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  В **MSsync_states** таблице отслеживается, какая публикация все еще находится в режиме параллельного моментального снимка. Эта таблица хранится в базе данных распространителя.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**publisher_id**|**smallint**|Идентификатор издателя.|  
|**publisher_db**|**sysname**|Имя базы данных публикации.|  
|**publication_id**|**int**|Идентификатор публикации.|  
  
## <a name="see-also"></a>См. также:  
 [Сопоставление системных таблиц с системными представлениями &#40;&#41;Transact-SQL ](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [Integration Servicesные таблицы &#40;&#41;Transact-SQL ](../../relational-databases/system-tables/integration-services-tables-transact-sql.md)   
 [Резервное копирование и восстановление таблиц &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backup-and-restore-tables-transact-sql.md)   
 [Таблицы доставки журналов (Transact-SQL)](../../relational-databases/system-tables/log-shipping-tables-transact-sql.md)  
  
  
