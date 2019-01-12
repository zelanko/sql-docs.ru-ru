---
title: Просмотр реплицированных команд и другие сведения в базе данных распространителя (Программирование репликации Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- sp_browsereplcmds
- transactional replication, monitoring
- distribution databases [SQL Server replication], viewing replicated commands
- viewing replicated commands
ms.assetid: 9c20acec-8fab-4483-b9c1-dfe3768f85dd
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 2bff82764256eebb02141bf2e1fafd86dce026e4
ms.sourcegitcommit: 7aa6beaaf64daf01b0e98e6c63cc22906a77ed04
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/09/2019
ms.locfileid: "54125774"
---
# <a name="view-replicated-commands-and-other-information-in-the-distribution-database-replication-transact-sql-programming"></a>Просмотр реплицированных команд и другой информации в базе данных распространителя (программирование репликации на языке Transact-SQL)
  Если используется репликация транзакций, команды транзакций хранятся в базе данных распространителя, пока агент распространителя не передаст их всем подписчикам или пока агент распространителя на подписчике не получит изменения по запросу. Эти ждущие команды в базе данных распространителя можно просматривать программным способом с помощью хранимых процедур репликации. Дополнительные сведения см. в статье [Хранимые процедуры репликации (Transact-SQL)](/sql/relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql).  
  
### <a name="to-view-replicated-commands-from-all-transactional-publications-in-the-distribution-database"></a>Просмотр реплицируемых команд из всех публикаций транзакций в базе данных распространителя  
  
1.  В базе данных на распространителе выполните процедуру [sp_browsereplcmds](/sql/relational-databases/system-stored-procedures/sp-browsemergesnapshotfolder-transact-sql).  
  
### <a name="to-view-replicated-commands-in-the-distribution-database-from-a-specific-article-or-from-a-specific-database-published-using-transactional-replication"></a>Просмотр реплицируемых команд в базе данных распространителя из определенной статьи или определенной базы данных, опубликованной с помощью репликации транзакций  
  
1.  В базе данных публикации на издателе выполните процедуру [sp_helparticle](/sql/relational-databases/system-stored-procedures/sp-helparticle-transact-sql)(необязательно). Задайте параметры **@publication** и **@article**. Запомните значение параметра **article id** в результирующем наборе.  
  
2.  В базе данных на распространителе выполните процедуру [sp_browsereplcmds](/sql/relational-databases/system-stored-procedures/sp-browsemergesnapshotfolder-transact-sql). Укажите идентификатор статьи из шага 2 в параметре **@article_id**. Укажите идентификатор базы данных публикации в параметре **@publisher_database_id**. Этот идентификатор можно получить в столбце **database_id** представления каталога [sys.databases](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) (необязательно).  
  
## <a name="see-also"></a>См. также  
 [Наблюдение за репликацией программным образом](../monitoring-replication.md)  
  
  
