---
title: "Просмотр сведений о конфликтах для публикаций слиянием | Документация Майкрософт"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: TSQL
helpviewer_keywords:
- merge replication conflict resolution [SQL Server replication], viewing conflicts
- sp_helpmergeconflictrows
- viewing conflict information
- conflict resolution [SQL Server replication], merge replication
- sp_helpmergearticleconflicts
ms.assetid: 4907fe35-10ee-4f81-b924-fc419b1864d2
caps.latest.revision: "22"
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5f126a0cc1066bae07c57bf6dfe093b8d480b9cd
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/18/2018
---
# <a name="view-conflict-information-for-merge-publications"></a>Просмотр сведений о конфликтах для публикаций слиянием
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Если конфликт разрешается в репликации слиянием, данные из проигравшей строки записываются в таблицу конфликтов. Эти данные конфликта можно просмотреть программно с помощью хранимых процедур репликации. Дополнительные сведения см. в статье [Advanced Merge Replication Conflict Detection and Resolution](../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md).  
  
### <a name="to-view-conflict-information-and-losing-row-data-for-all-types-of-conflicts"></a>Просмотр сведений о конфликте и данных проигравшей строки для всех типов конфликта  
  
1.  Выполните процедуру [sp_helpmergepublication](../../relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql.md)на издателе в базе данных публикации. Запомните значения следующих столбцов в результирующем наборе.  
  
    -   **centralized_conflicts** — значение 1 показывает, что конфликтующие строки хранятся на издателе, а значение 0 показывает, что на издателе не хранятся конфликтующие строки.  
  
    -   **decentralized_conflicts** — значение 1 показывает, что конфликтующие строки хранятся на подписчике, а значение 0 показывает, что на подписчике не хранятся конфликтующие строки.  
  
        > [!NOTE]  
        >  Способ регистрации конфликта в публикации слиянием устанавливается с помощью параметра **@conflict_logging** хранимой процедуры [sp_addmergepublication](../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md). Использование параметра **@centralized_conflicts** является устаревшей возможностью.  
  
     В следующей таблице приводятся значения этих столбцов в зависимости от значений, указанных в параметре **@conflict_logging**.  
  
    |Значение @conflict_logging|centralized_conflicts|decentralized_conflicts|  
    |------------------------------|----------------------------|------------------------------|  
    |**издатель**|1|0|  
    |**подписчик**|0|1|  
    |**оба**|1|1|  
  
2.  Выполните процедуру [sp_helpmergearticleconflicts](../../relational-databases/system-stored-procedures/sp-helpmergearticleconflicts-transact-sql.md)на издателе в базе данных публикации или на подписчике в базе данных подписки. Укажите значение в параметре **@publication** , чтобы возвратить только сведения о конфликте статей, принадлежащих конкретной публикации. Таким образом будут получены сведения о конфликтах для статей, содержащих конфликты. Запомните значение **conflict_table** для всех интересующих статей. Если параметр **conflict_table** для статьи имеет значение NULL, удалите только конфликты, которые возникли в этой статье.  
  
3.  (Необязательно) Просмотрите строки конфликта для интересующих статей. В зависимости от значений параметров **centralized_conflicts** и **decentralized_conflicts** , полученных на шаге 1, выполните одно из следующих действий.  
  
    -   На издателе в базе данных публикации выполните хранимую процедуру [sp_helpmergeconflictrows](../../relational-databases/system-stored-procedures/sp-helpmergeconflictrows-transact-sql.md). Укажите таблицу конфликтов для статьи (из шага 1) в параметре **@conflict_table**. Задайте значение **@publication** , чтобы ограничить возвращаемые сведения о конфликтах до конфликтов выбранной публикацией (необязательно). В результате будут возвращены данные для потерянной строки и другие сведения.  
  
    -   На подписчике в базе данных подписки выполните хранимую процедуру [sp_helpmergeconflictrows](../../relational-databases/system-stored-procedures/sp-helpmergeconflictrows-transact-sql.md). Укажите таблицу конфликтов для статьи (из шага 1) в параметре **@conflict_table**. В результате будут возвращены данные для потерянной строки и другие сведения.  
  
### <a name="to-view-information-only-on-conflicts-where-the-delete-failed"></a>Просмотр только сведений о конфликтах, в которых операция удаления завершилась ошибкой  
  
1.  Выполните процедуру [sp_helpmergepublication](../../relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql.md)на издателе в базе данных публикации. Запомните значения следующих столбцов в результирующем наборе.  
  
    -   **centralized_conflicts** — значение 1 показывает, что конфликтующие строки хранятся на издателе, а значение 0 показывает, что на издателе не хранятся конфликтующие строки.  
  
    -   **decentralized_conflicts** — значение 1 показывает, что конфликтующие строки хранятся на подписчике, а значение 0 показывает, что на подписчике не хранятся конфликтующие строки.  
  
        > [!NOTE]  
        >  Способ регистрации конфликта в публикации слиянием устанавливается с помощью параметра **@conflict_logging** хранимой процедуры [sp_addmergepublication](../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md). Использование параметра **@centralized_conflicts** является устаревшей возможностью.  
  
2.  Выполните процедуру [sp_helpmergearticleconflicts](../../relational-databases/system-stored-procedures/sp-helpmergearticleconflicts-transact-sql.md)на издателе в базе данных публикации или на подписчике в базе данных подписки. Укажите значение в параметре **@publication** , чтобы возвратить только сведения о таблице конфликтов для статей, принадлежащих конкретной публикации. Таким образом будут получены сведения о конфликтах для статей, содержащих конфликты. Запомните значение **source_object** для всех интересующих статей. Если параметр **conflict_table** для статьи имеет значение NULL, удалите только конфликты, которые возникли в этой статье.  
  
3.  (Необязательно) Просмотрите информацию о конфликтах удаления. В зависимости от значений параметров **centralized_conflicts** и **decentralized_conflicts** , полученных на шаге 1, выполните одно из следующих действий.  
  
    -   На издателе в базе данных публикации выполните хранимую процедуру [sp_helpmergedeleteconflictrows](../../relational-databases/system-stored-procedures/sp-helpmergedeleteconflictrows-transact-sql.md). Укажите в параметре **@source_object**. Задайте значение **@publication** , чтобы ограничить возвращаемые сведения о конфликтах до конфликтов выбранной публикацией (необязательно). Таким образом возвращаются сведения о конфликте операций удаления, хранящиеся на издателе.  
  
    -   На подписчике в базе данных подписки выполните хранимую процедуру [sp_helpmergedeleteconflictrows](../../relational-databases/system-stored-procedures/sp-helpmergedeleteconflictrows-transact-sql.md). Укажите в параметре **@source_object**. Задайте значение **@publication** , чтобы ограничить возвращаемые сведения о конфликтах до конфликтов выбранной публикацией (необязательно). Таким образом возвращаются сведения о конфликте операций удаления, сохраненные на подписчике.  
  
## <a name="see-also"></a>См. также:  
 [Advanced Merge Replication Conflict Detection and Resolution](../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md)  
  
  
