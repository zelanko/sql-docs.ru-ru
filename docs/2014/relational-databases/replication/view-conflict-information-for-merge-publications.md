---
title: Просмотр сведений о конфликтах для публикаций слиянием (Программирование репликации Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- merge replication conflict resolution [SQL Server replication], viewing conflicts
- sp_helpmergeconflictrows
- viewing conflict information
- conflict resolution [SQL Server replication], merge replication
- sp_helpmergearticleconflicts
ms.assetid: 4907fe35-10ee-4f81-b924-fc419b1864d2
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: f1b7e1e49f6291063996f7d7b7b966da6a716c16
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2018
ms.locfileid: "52794206"
---
# <a name="view-conflict-information-for-merge-publications-replication-transact-sql-programming"></a>просмотреть сведения о конфликтах для публикаций слиянием (программирование репликации на языке Transact-SQL)
  Если конфликт разрешается в репликации слиянием, данные из проигравшей строки записываются в таблицу конфликтов. Эти данные конфликта можно просмотреть программно с помощью хранимых процедур репликации. Дополнительные сведения см. в разделе [Advanced Merge Replication Conflict Detection and Resolution](merge/advanced-merge-replication-conflict-detection-and-resolution.md).  
  
### <a name="to-view-conflict-information-and-losing-row-data-for-all-types-of-conflicts"></a>Просмотр сведений о конфликте и данных проигравшей строки для всех типов конфликта  
  
1.  Выполните процедуру [sp_helpmergepublication](/sql/relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql)на издателе в базе данных публикации. Запомните значения следующих столбцов в результирующем наборе.  
  
    -   **centralized_conflicts** — значение 1 показывает, что конфликтующие строки хранятся на издателе, а значение 0 показывает, что на издателе не хранятся конфликтующие строки.  
  
    -   **decentralized_conflicts** — значение 1 показывает, что конфликтующие строки хранятся на подписчике, а значение 0 показывает, что на подписчике не хранятся конфликтующие строки.  
  
        > [!NOTE]  
        >  Способ регистрации конфликта в публикации слиянием устанавливается с помощью параметра **@conflict_logging** хранимой процедуры [sp_addmergepublication](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql). Использование параметра **@centralized_conflicts** является устаревшей возможностью.  
  
     В следующей таблице приводятся значения этих столбцов в зависимости от значений, указанных в параметре **@conflict_logging**.  
  
    |Значение @conflict_logging|centralized_conflicts|decentralized_conflicts|  
    |------------------------------|----------------------------|------------------------------|  
    |`publisher`|1|0|  
    |`subscriber`|0|1|  
    |`both`|1|1|  
  
2.  Выполните процедуру [sp_helpmergearticleconflicts](/sql/relational-databases/system-stored-procedures/sp-helpmergearticleconflicts-transact-sql)на издателе в базе данных публикации или на подписчике в базе данных подписки. Укажите значение в параметре **@publication** , чтобы возвратить только сведения о конфликте статей, принадлежащих конкретной публикации. Таким образом будут получены сведения о конфликтах для статей, содержащих конфликты. Запомните значение **conflict_table** для всех интересующих статей. Если параметр **conflict_table** для статьи имеет значение NULL, удалите только конфликты, которые возникли в этой статье.  
  
3.  (Необязательно) Просмотрите строки конфликта для интересующих статей. В зависимости от значений параметров **centralized_conflicts** и **decentralized_conflicts** , полученных на шаге 1, выполните одно из следующих действий.  
  
    -   На издателе в базе данных публикации выполните хранимую процедуру [sp_helpmergeconflictrows](/sql/relational-databases/system-stored-procedures/sp-helpmergeconflictrows-transact-sql). Укажите таблицу конфликтов для статьи (из шага 1) в параметре **@conflict_table**. Задайте значение **@publication** , чтобы ограничить возвращаемые сведения о конфликтах до конфликтов выбранной публикацией (необязательно). В результате будут возвращены данные для потерянной строки и другие сведения.  
  
    -   На подписчике в базе данных подписки выполните хранимую процедуру [sp_helpmergeconflictrows](/sql/relational-databases/system-stored-procedures/sp-helpmergeconflictrows-transact-sql). Укажите таблицу конфликтов для статьи (из шага 1) в параметре **@conflict_table**. В результате будут возвращены данные для потерянной строки и другие сведения.  
  
### <a name="to-view-information-only-on-conflicts-where-the-delete-failed"></a>Просмотр только сведений о конфликтах, в которых операция удаления завершилась ошибкой  
  
1.  Выполните процедуру [sp_helpmergepublication](/sql/relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql)на издателе в базе данных публикации. Запомните значения следующих столбцов в результирующем наборе.  
  
    -   **centralized_conflicts** — значение 1 показывает, что конфликтующие строки хранятся на издателе, а значение 0 показывает, что на издателе не хранятся конфликтующие строки.  
  
    -   **decentralized_conflicts** — значение 1 показывает, что конфликтующие строки хранятся на подписчике, а значение 0 показывает, что на подписчике не хранятся конфликтующие строки.  
  
        > [!NOTE]  
        >  Способ регистрации конфликта в публикации слиянием устанавливается с помощью параметра **@conflict_logging** хранимой процедуры [sp_addmergepublication](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql). Использование параметра **@centralized_conflicts** является устаревшей возможностью.  
  
2.  Выполните процедуру [sp_helpmergearticleconflicts](/sql/relational-databases/system-stored-procedures/sp-helpmergearticleconflicts-transact-sql)на издателе в базе данных публикации или на подписчике в базе данных подписки. Укажите значение в параметре **@publication** , чтобы возвратить только сведения о таблице конфликтов для статей, принадлежащих конкретной публикации. Таким образом будут получены сведения о конфликтах для статей, содержащих конфликты. Запомните значение **source_object** для всех интересующих статей. Если параметр **conflict_table** для статьи имеет значение NULL, удалите только конфликты, которые возникли в этой статье.  
  
3.  (Необязательно) Просмотрите информацию о конфликтах удаления. В зависимости от значений параметров **centralized_conflicts** и **decentralized_conflicts** , полученных на шаге 1, выполните одно из следующих действий.  
  
    -   На издателе в базе данных публикации выполните хранимую процедуру [sp_helpmergedeleteconflictrows](/sql/relational-databases/system-stored-procedures/sp-helpmergedeleteconflictrows-transact-sql). Укажите в параметре **@source_object**. Задайте значение **@publication** , чтобы ограничить возвращаемые сведения о конфликтах до конфликтов выбранной публикацией (необязательно). Таким образом возвращаются сведения о конфликте операций удаления, хранящиеся на издателе.  
  
    -   На подписчике в базе данных подписки выполните хранимую процедуру [sp_helpmergedeleteconflictrows](/sql/relational-databases/system-stored-procedures/sp-helpmergedeleteconflictrows-transact-sql). Укажите в параметре **@source_object**. Задайте значение **@publication** , чтобы ограничить возвращаемые сведения о конфликтах до конфликтов выбранной публикацией (необязательно). Таким образом возвращаются сведения о конфликте операций удаления, сохраненные на подписчике.  
  
## <a name="see-also"></a>См. также  
 [Advanced Merge Replication Conflict Detection and Resolution](merge/advanced-merge-replication-conflict-detection-and-resolution.md)  
  
  
