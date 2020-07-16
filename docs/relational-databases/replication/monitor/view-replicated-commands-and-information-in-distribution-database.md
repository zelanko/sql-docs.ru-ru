---
title: Просмотр реплицированных команд и данных в базе данных распространителя
description: Узнайте, как посматривать реплицированные команды и другую информацию о репликации в базе данных распространителя для SQL Server.
ms.custom: seo-lt-2019
ms.date: 03/09/2017
ms.prod: sql
ms.prod_service: database-engine
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
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: 12407e91cf4a4607d2b6ca2c7a195ba1104930dd
ms.sourcegitcommit: 21c14308b1531e19b95c811ed11b37b9cf696d19
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/09/2020
ms.locfileid: "86159582"
---
# <a name="view-replicated-commands-and-information-in-distribution-database"></a>Просмотр реплицированных команд и данных в базе данных распространителя
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../../includes/applies-to-version/sql-asdbmi.md)]
  Если используется репликация транзакций, команды транзакций хранятся в базе данных распространителя, пока агент распространителя не передаст их всем подписчикам или пока агент распространителя на подписчике не получит изменения по запросу. Эти ждущие команды в базе данных распространителя можно просматривать программным способом с помощью хранимых процедур репликации. Дополнительные сведения см. в статье [Хранимые процедуры репликации (Transact-SQL)](../../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md).  
  
### <a name="to-view-replicated-commands-from-all-transactional-publications-in-the-distribution-database"></a>Просмотр реплицируемых команд из всех публикаций транзакций в базе данных распространителя  
  
1.  В базе данных на распространителе выполните процедуру [sp_browsereplcmds](../../../relational-databases/system-stored-procedures/sp-browsereplcmds-transact-sql.md).  
  
### <a name="to-view-replicated-commands-in-the-distribution-database-from-a-specific-article-or-from-a-specific-database-published-using-transactional-replication"></a>Просмотр реплицируемых команд в базе данных распространителя из определенной статьи или определенной базы данных, опубликованной с помощью репликации транзакций  
  
1.  В базе данных публикации на издателе выполните процедуру [sp_helparticle](../../../relational-databases/system-stored-procedures/sp-helparticle-transact-sql.md)(необязательно). Укажите параметры `@publication` и `@article`. Запомните значение параметра **article id** в результирующем наборе.  
  
2.  В базе данных на распространителе выполните процедуру [sp_browsereplcmds](../../../relational-databases/system-stored-procedures/sp-browsereplcmds-transact-sql.md). (Необязательно) Укажите идентификатор статьи из шага 2 в параметре `@article_id`. (Необязательно) Укажите идентификатор базы данных публикации в параметре `@publisher_database_id`. Этот идентификатор можно получить в столбце **database_id** представления каталога [sys.databases](../../../relational-databases/system-catalog-views/sys-databases-transact-sql.md).  
  
## <a name="see-also"></a>См. также:  
 [Наблюдение за репликацией программным образом](../../../relational-databases/replication/monitor/programmatically-monitor-replication.md)  
  
  
