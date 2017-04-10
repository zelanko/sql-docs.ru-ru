---
title: "очистить метаданные слияния (программирование репликации на языке Transact-SQL) | Microsoft Docs"
ms.custom: ""
ms.date: "03/03/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "TSQL"
helpviewer_keywords: 
  - "метаданные [репликация SQL Server]"
  - "sp_mergemetadataretentioncleanup"
ms.assetid: 9b88baea-b7c6-4e5d-88f9-93d6a0ff0368
caps.latest.revision: 33
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 33
---
# очистить метаданные слияния (программирование репликации на языке Transact-SQL)
  Агент слияния периодически чистит метаданные репликации слиянием в зависимости от заданного срока хранения публикации. Это происходит на издателе и подписчике в [MSmerge_genhistory](../../../relational-databases/system-tables/msmerge-genhistory-transact-sql.md), [MSmerge_contents](../../../relational-databases/system-tables/msmerge-contents-transact-sql.md), [MSmerge_tombstone](../../../relational-databases/system-tables/msmerge-tombstone-transact-sql.md), [MSmerge_past_partition_mappings](../../../relational-databases/system-tables/msmerge-past-partition-mappings-transact-sql.md), и [MSmerge_current_partition_mappings](../../../relational-databases/system-tables/msmerge-current-partition-mappings.md) системных таблиц. Данные в этих таблицах могут чиститься и программным путем с помощью хранимых процедур репликации.  
  
### Очистка метаданных слияния вручную  
  
1.  На издателе в базе данных публикации выполните хранимую процедуру [sp_mergemetadataretentioncleanup](../../../relational-databases/system-stored-procedures/sp-mergemetadataretentioncleanup-transact-sql.md).  
  
2.  (Необязательно) Обратите внимание, количество строк, удаляемых в шаге 1 из [MSmerge_genhistory](../../../relational-databases/system-tables/msmerge-genhistory-transact-sql.md), [MSmerge_contents](../../../relational-databases/system-tables/msmerge-contents-transact-sql.md), и [MSmerge_tombstone](../../../relational-databases/system-tables/msmerge-tombstone-transact-sql.md) системные таблицы, возвращаемые соответственно в **@num_genhistory_rows**, **@num_contents_rows**, и **@num_tombstone_rows** Выходные параметры.  
  
3.  Повторите шаги 1 и 2 на подписчике для очистки метаданных в базе данных подписки.  
  
## См. также:  
 [Окончание срока действия и отключение подписки](../../../relational-databases/replication/subscription-expiration-and-deactivation.md)  
  
  