---
title: "просмотреть сведения о конфликтах для публикаций слиянием (программирование репликации на языке Transact-SQL) | Microsoft Docs"
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
  - "разрешение конфликтов при репликации слиянием [репликация SQL Server], просмотр конфликтов"
  - "sp_helpmergeconflictrows, хранимая процедура"
  - "просмотр сведений о конфликтах"
  - "разрешение конфликтов [репликация SQL Server], репликация слиянием"
  - "sp_helpmergearticleconflicts"
ms.assetid: 4907fe35-10ee-4f81-b924-fc419b1864d2
caps.latest.revision: 22
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# просмотреть сведения о конфликтах для публикаций слиянием (программирование репликации на языке Transact-SQL)
  Если конфликт разрешается в репликации слиянием, данные из проигравшей строки записываются в таблицу конфликтов. Эти данные конфликта можно просмотреть программно с помощью хранимых процедур репликации. Дополнительные сведения см. в статье [Advanced Merge Replication Conflict Detection and Resolution](../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md).  
  
### Просмотр сведений о конфликте и данных проигравшей строки для всех типов конфликта  
  
1.  На издателе в базе данных публикации выполните хранимую процедуру [sp_helpmergepublication](../../relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql.md). Запомните значения следующих столбцов в результирующем наборе.  
  
    -   **centralized_conflicts** -1 означает, что конфликтующие строки хранятся на издателе и 0 указывает, что конфликтующие строки не хранятся на издателе.  
  
    -   **decentralized_conflicts** -1 указывает, что конфликтующие строки хранятся на подписчике, а 0 означает, что на подписчике не хранятся конфликтующие строки.  
  
        > [!NOTE]  
        >  Способ регистрации конфликта в публикации слиянием устанавливается с помощью **@conflict_logging** параметр [sp_addmergepublication](../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md). Использование **@centralized_conflicts** параметр является устаревшим.  
  
     В следующей таблице описаны значения этих столбцов в зависимости от значений, указанных для **@conflict_logging**.  
  
    |Значение @conflict_logging|centralized_conflicts|decentralized_conflicts|  
    |------------------------------|----------------------------|------------------------------|  
    |**publisher**|1|0|  
    |**подписчик**|0|1|  
    |**both**|1|1|  
  
2.  На издателе в базе данных публикации или на подписчике в базе данных подписки выполните [sp_helpmergearticleconflicts](../../relational-databases/system-stored-procedures/sp-helpmergearticleconflicts-transact-sql.md). Укажите значение в параметре **@publication** , чтобы возвратить только сведения о конфликте статей, принадлежащих конкретной публикации. Таким образом будут получены сведения о конфликтах для статей, содержащих конфликты. Обратите внимание на значение **conflict_table** для всех интересующих статей. Если значение **conflict_table** для статьи имеет значение NULL, удалите только конфликты, произошедшие в этой статье.  
  
3.  (Необязательно) Просмотрите строки конфликта для интересующих статей. В зависимости от значения **centralized_conflicts** и **decentralized_conflicts** из шага 1, выполните одно из следующих действий:  
  
    -   На издателе в базе данных публикации выполните хранимую процедуру [sp_helpmergeconflictrows](../../relational-databases/system-stored-procedures/sp-helpmergeconflictrows-transact-sql.md). Укажите таблицу конфликтов для статьи (из шага 1) для **@conflict_table**. (Необязательно) Укажите значение **@publication** ограничить возвращаемые сведения о конфликтах для конкретной публикации. В результате будут возвращены данные для потерянной строки и другие сведения.  
  
    -   На подписчике в базе данных подписки выполните хранимую процедуру [sp_helpmergeconflictrows](../../relational-databases/system-stored-procedures/sp-helpmergeconflictrows-transact-sql.md). Укажите таблицу конфликтов для статьи (из шага 1) для **@conflict_table**. В результате будут возвращены данные для потерянной строки и другие сведения.  
  
### Просмотр только сведений о конфликтах, в которых операция удаления завершилась ошибкой  
  
1.  На издателе в базе данных публикации выполните хранимую процедуру [sp_helpmergepublication](../../relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql.md). Запомните значения следующих столбцов в результирующем наборе.  
  
    -   **centralized_conflicts** -1 означает, что конфликтующие строки хранятся на издателе и 0 указывает, что конфликтующие строки не хранятся на издателе.  
  
    -   **decentralized_conflicts** -1 указывает, что конфликтующие строки хранятся на подписчике, а 0 означает, что на подписчике не хранятся конфликтующие строки.  
  
        > [!NOTE]  
        >  Способ регистрации конфликта в публикации слиянием устанавливается с помощью **@conflict_logging** параметр [sp_addmergepublication](../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md). Использование **@centralized_conflicts** параметр является устаревшим.  
  
2.  На издателе в базе данных публикации или на подписчике в базе данных подписки выполните [sp_helpmergearticleconflicts](../../relational-databases/system-stored-procedures/sp-helpmergearticleconflicts-transact-sql.md). Укажите значение в параметре **@publication** , чтобы возвратить только сведения о таблице конфликтов для статей, принадлежащих конкретной публикации. Таким образом будут получены сведения о конфликтах для статей, содержащих конфликты. Обратите внимание на значение **source_object** для всех интересующих статей. Если значение **conflict_table** для статьи имеет значение NULL, удалите только конфликты, произошедшие в этой статье.  
  
3.  (Необязательно) Просмотрите информацию о конфликтах удаления. В зависимости от значения **centralized_conflicts** и **decentralized_conflicts** из шага 1, выполните одно из следующих действий:  
  
    -   На издателе в базе данных публикации выполните хранимую процедуру [sp_helpmergedeleteconflictrows](../../relational-databases/system-stored-procedures/sp-helpmergedeleteconflictrows-transact-sql.md). Укажите имя исходной таблицы (из шага 1), на котором возник конфликт для **@source_object**. (Необязательно) Укажите значение **@publication** ограничить возвращаемые сведения о конфликтах для конкретной публикации. Таким образом возвращаются сведения о конфликте операций удаления, хранящиеся на издателе.  
  
    -   На подписчике в базе данных подписки выполните хранимую процедуру [sp_helpmergedeleteconflictrows](../../relational-databases/system-stored-procedures/sp-helpmergedeleteconflictrows-transact-sql.md). Укажите имя исходной таблицы (из шага 1), на котором возник конфликт для **@source_object**. (Необязательно) Укажите значение **@publication** ограничить возвращаемые сведения о конфликтах для конкретной публикации. Таким образом возвращаются сведения о конфликте операций удаления, сохраненные на подписчике.  
  
## См. также:  
 [Расширенное обнаружение и разрешение конфликтов репликации слиянием](../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md)  
  
  