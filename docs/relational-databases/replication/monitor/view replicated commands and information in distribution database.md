---
title: "Просмотр реплицированных команд и другой информации в базе данных распространителя (программирование репликации на языке Transact-SQL) | Microsoft Docs"
ms.custom: ""
ms.date: "03/23/2017"
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
  - "sp_browsereplcmds"
  - "репликация транзакций, мониторинг"
  - "базы данных распространителя [репликация SQL Server], просмотр реплицированных команд"
  - "просмотр реплицированных команд"
ms.assetid: 9c20acec-8fab-4483-b9c1-dfe3768f85dd
caps.latest.revision: 31
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# Просмотр реплицированных команд и другой информации в базе данных распространителя (программирование репликации на языке Transact-SQL)
  Если используется репликация транзакций, команды транзакций хранятся в базе данных распространителя, пока агент распространителя не передаст их всем подписчикам или пока агент распространителя на подписчике не получит изменения по запросу. Эти ждущие команды в базе данных распространителя можно просматривать программным способом с помощью хранимых процедур репликации. Дополнительные сведения см. в разделе [хранимых процедур репликации и #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md).  
  
### Просмотр реплицируемых команд из всех публикаций транзакций в базе данных распространителя  
  
1.  На распространителе в базе данных распространителя, выполните [sp_browsereplcmds](../../../relational-databases/system-stored-procedures/sp-browsereplcmds-transact-sql.md).  
  
### Просмотр реплицируемых команд в базе данных распространителя из определенной статьи или определенной базы данных, опубликованной с помощью репликации транзакций  
  
1.  (Необязательно) На издателе в базе данных публикации выполните хранимую процедуру [sp_helparticle](../../../relational-databases/system-stored-procedures/sp-helparticle-transact-sql.md). Задайте параметры **@publication** и **@article**. Запомните значение параметра **article id** в результирующем наборе.  
  
2.  На распространителе в базе данных распространителя, выполните [sp_browsereplcmds](../../../relational-databases/system-stored-procedures/sp-browsereplcmds-transact-sql.md). (Необязательно) Укажите идентификатор статьи из шага 2 для **@article_id**. (Необязательно) Укажите идентификатор базы данных публикации для **@publisher_database_id**, который можно получить из **database_id** столбца в [sys.databases](../../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) представления каталога.  
  
## См. также:  
 [Наблюдение за репликацией программным образом](../../../relational-databases/replication/monitor/programmatically-monitor-replication.md)  
  
  