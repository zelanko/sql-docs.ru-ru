---
title: Просмотр и устранение конфликтов данных (слияние)
description: Узнайте, как просматривать и разрешать конфликты данных для публикаций слиянием для SQL Server.
ms.custom: seo-lt-2019
ms.date: 11/20/2018
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- merge replication conflict resolution [SQL Server replication], viewing conflicts
- viewing conflict information
- conflict resolution [SQL Server replication], merge replication
ms.assetid: aeee9546-4480-49f9-8b1e-c71da1f056c7
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 79dc4b26ee543aa99b9fc90e29f7bb6c7d571555
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "75321891"
---
# <a name="conflict-resolution-for-merge-replication"></a>Разрешение конфликтов при репликации слиянием
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  В репликации слиянием конфликты разрешаются на основе сопоставителя, указанного для каждой статьи. По умолчанию для разрешения конфликтов не требуется вмешательство пользователя. Однако просмотреть конфликты и изменить результат разрешения конфликта можно в средстве просмотра конфликтов репликации [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 Данные конфликтов доступны в средстве просмотра конфликтов репликации в течение времени, указанном для срока хранения конфликтов (по умолчанию это время равно 14 дням). Чтобы установить срок хранения конфликтов, выполните любое из указанных ниже действий:  
  
-   Укажите значение срока хранения в параметре `@conflict_retention` хранимой процедуры [sp_addmergepublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md).  
  
-   Задайте значение **conflict_retention** для параметра `@property` и значение срока хранения для параметра `@value` хранимой процедуры [sp_changemergepublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md).  
  
 По умолчанию сведения о конфликтах сохраняются:    
-   На издателе и подписчике, если уровень совместимости публикации 90RTM или выше.   
-   На издателе, если уровень совместимости публикации ниже, чем 80RTM.   
-   На издателе, если подписчики используют [!INCLUDE[ssEW](../../includes/ssew-md.md)]. Данные о конфликтах не могут храниться на подписчиках, использующих [!INCLUDE[ssEW](../../includes/ssew-md.md)] .  
  
 Хранение информации о конфликте управляется с помощью свойства публикации **conflict_logging** . Дополнительные сведения см. в статьях [sp_addmergepublication (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md) и [sp_changemergepublication (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md).  
  
 Возможно также разрешение конфликтов в интерактивном режиме во время синхронизации с помощью интерактивного сопоставителя [!INCLUDE[msCoName](../../includes/msconame-md.md)] . Интерактивный сопоставитель доступен через диспетчер синхронизации [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows. Дополнительные сведения см. в статье [Синхронизация подписки с помощью диспетчера синхронизации Windows (диспетчер синхронизации Windows)](../../relational-databases/replication/synchronize-a-subscription-using-windows-synchronization-manager.md).  
  
## <a name="resolve-conflicts"></a>Устранение конфликтов  
  
1.  Подключитесь к издателю (или подписчику, если это уместно) в среде [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], а затем раскройте узел сервера.  
  
2.  Раскройте папку **Репликация** , а затем папку **Локальные публикации** .  
  
3.  Щелкните правой кнопкой мыши публикацию, для которой требуется просмотреть конфликты, а затем щелкните **Просмотреть конфликты**.  
  
    > [!NOTE]  
    >  Если для свойства **conflict_logging** задано значение **'subscriber'** , пункт меню **Просмотреть конфликты** будет недоступен. Чтобы просмотреть конфликты, запустите в командной строке программу ConflictViewer.exe. По умолчанию программа ConflictViewer.exe находится в следующем каталоге: Microsoft SQL Server\100\Tools\Binn\VSShell\Common7\IDE. Чтобы вывести список допустимых параметров запуска, выполните команду ConflictViewer.exe -?.  
  
4.  В диалоговом окне **Выбор таблицы с конфликтами** выберите базу данных, публикацию и таблицу, для которой необходимо просмотреть конфликты.  
  
5.  В средстве просмотра конфликтов репликации можно выполнить следующие действия:  
  
    -   Отфильтровать строки с помощью кнопок, расположенных справа от верхней сетки.  
  
    -   Выбрать строку в верхней сетке для отображения информации об этой строке в нижней сетке.  
  
    -   Выберите одну или более строк в верхней сетке, щелкните **Удалить**, что эквивалентно нажатию кнопки **Отправить выигравший** (без внесения каких-либо изменений в данные).  
  
    -   Нажать кнопку свойств ( **...** ) для просмотра дополнительной информации о столбце, вовлеченном в конфликт.  
  
    -   Измените данные в столбце **Выигравший вариант** или **Проигравший вариант** до отправки данных (данные доступны только для чтения, если столбец окрашен в серый цвет).  
  
    -   Щелкните **Отправить выигравший** , чтобы принять строку, определенную как победитель в конфликте.  
  
    -   Щелкните **Отправить проигравший** , чтобы переопределить разрешение конфликта и передать значение, определенное как проигравший в конфликте на все узлы в топологии.  
  
    -   Выбрать **Записать подробности этого конфликта** , чтобы записать данные конфликта в файл. Для указания размещения файла наведите указатель на меню **Просмотр** и щелкните **Параметры**. Введите значение или нажмите кнопку обзора ( **...** ), а затем перейдите к необходимому файлу. Нажмите кнопку **ОК** для выхода из диалогового окна **Параметры** .  
  
6.  Закройте средство просмотра конфликтов репликации.  

## <a name="view-conflict-information"></a>Просмотр сведений о конфликтах
Если конфликт разрешается в репликации слиянием, данные из проигравшей строки записываются в таблицу конфликтов. Эти данные конфликта можно просмотреть программно с помощью хранимых процедур репликации. Дополнительные сведения см. в разделе [Advanced Merge Replication Conflict Detection and Resolution](../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md).  
  
1.  Выполните процедуру [sp_helpmergepublication](../../relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql.md)на издателе в базе данных публикации. Запомните значения следующих столбцов в результирующем наборе.  
  
    -   **centralized_conflicts** — значение 1 показывает, что конфликтующие строки хранятся на издателе, а значение 0 показывает, что на издателе не хранятся конфликтующие строки.  
  
    -   **decentralized_conflicts** — значение 1 показывает, что конфликтующие строки хранятся на подписчике, а значение 0 показывает, что на подписчике не хранятся конфликтующие строки.  
  
        > [!NOTE]  
        >  Способ регистрации конфликта в публикации слиянием устанавливается с помощью параметра `@conflict_logging` процедуры [sp_addmergepublication](../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md). Использовать параметр `@centralized_conflicts` не рекомендуется.  
  
     В таблице ниже приводятся значения этих столбцов в зависимости от значений, указанных в параметре `@conflict_logging`.  
  
    |Значение @conflict_logging|centralized_conflicts|decentralized_conflicts|  
    |------------------------------|----------------------------|------------------------------|  
    |**publisher**|1|0|  
    |**подписчик**|0|1|  
    |**оба**|1|1|  
  
2.  Выполните процедуру [sp_helpmergearticleconflicts](../../relational-databases/system-stored-procedures/sp-helpmergearticleconflicts-transact-sql.md)на издателе в базе данных публикации или на подписчике в базе данных подписки. Укажите значение в параметре `@publication`, чтобы получить сведения о конфликтах только для статей, принадлежащих конкретной публикации. Таким образом будут получены сведения о конфликтах для статей, содержащих конфликты. Запомните значение **conflict_table** для всех интересующих статей. Если параметр **conflict_table** для статьи имеет значение NULL, удалите только конфликты, которые возникли в этой статье.  
  
3.  (Необязательно) Просмотрите строки конфликта для интересующих статей. В зависимости от значений параметров **centralized_conflicts** и **decentralized_conflicts** , полученных на шаге 1, выполните одно из следующих действий.  
  
    -   На издателе в базе данных публикации выполните хранимую процедуру [sp_helpmergeconflictrows](../../relational-databases/system-stored-procedures/sp-helpmergeconflictrows-transact-sql.md). Укажите таблицу конфликтов для статьи (из шага 1) в параметре `@conflict_table`. (Необязательно) Задайте значение `@publication`, чтобы ограничить возвращаемые сведения о конфликтах сведениями для определенной публикации. В результате будут возвращены данные для потерянной строки и другие сведения.  
  
    -   На подписчике в базе данных подписки выполните хранимую процедуру [sp_helpmergeconflictrows](../../relational-databases/system-stored-procedures/sp-helpmergeconflictrows-transact-sql.md). Укажите таблицу конфликтов для статьи (из шага 1) в параметре `@conflict_table`. В результате будут возвращены данные для потерянной строки и другие сведения.  
  
## <a name="conflict-where-delete-failed"></a>Конфликт со сбоем удаления   
  
1.  Выполните процедуру [sp_helpmergepublication](../../relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql.md)на издателе в базе данных публикации. Запомните значения следующих столбцов в результирующем наборе.  
  
    -   **centralized_conflicts** — значение 1 показывает, что конфликтующие строки хранятся на издателе, а значение 0 показывает, что на издателе не хранятся конфликтующие строки.  
  
    -   **decentralized_conflicts** — значение 1 показывает, что конфликтующие строки хранятся на подписчике, а значение 0 показывает, что на подписчике не хранятся конфликтующие строки.  
  
        > [!NOTE]  
        >  Способ регистрации конфликта в публикации слиянием устанавливается с помощью параметра `@conflict_logging` хранимой процедуры [sp_addmergepublication](../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md). Использовать параметр `@centralized_conflicts` не рекомендуется.  
  
2.  Выполните процедуру [sp_helpmergearticleconflicts](../../relational-databases/system-stored-procedures/sp-helpmergearticleconflicts-transact-sql.md)на издателе в базе данных публикации или на подписчике в базе данных подписки. Укажите значение в параметре `@publication`, чтобы получить сведения о таблице конфликтов только для статей, принадлежащих конкретной публикации. Таким образом будут получены сведения о конфликтах для статей, содержащих конфликты. Запомните значение **source_object** для всех интересующих статей. Если параметр **conflict_table** для статьи имеет значение NULL, удалите только конфликты, которые возникли в этой статье.  
  
3.  (Необязательно) Просмотрите информацию о конфликтах удаления. В зависимости от значений параметров **centralized_conflicts** и **decentralized_conflicts** , полученных на шаге 1, выполните одно из следующих действий.  
  
    -   На издателе в базе данных публикации выполните хранимую процедуру [sp_helpmergedeleteconflictrows](../../relational-databases/system-stored-procedures/sp-helpmergedeleteconflictrows-transact-sql.md). Укажите в параметре `@source_object` имя исходной таблицы (из шага 1), в которой произошел конфликт. (Необязательно) Задайте значение `@publication`, чтобы ограничить возвращаемые сведения о конфликтах сведениями для определенной публикации. Таким образом возвращаются сведения о конфликте операций удаления, хранящиеся на издателе.  
  
    -   На подписчике в базе данных подписки выполните хранимую процедуру [sp_helpmergedeleteconflictrows](../../relational-databases/system-stored-procedures/sp-helpmergedeleteconflictrows-transact-sql.md). Укажите в параметре `@source_object` имя исходной таблицы (из шага 1), в которой произошел конфликт. (Необязательно) Задайте значение `@publication`, чтобы ограничить возвращаемые сведения о конфликтах сведениями для определенной публикации. Таким образом возвращаются сведения о конфликте операций удаления, сохраненные на подписчике.  
  
## <a name="see-also"></a>См. также:  
 [Advanced Merge Replication Conflict Detection and Resolution](../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md)   
 [Определение арбитра для статей публикации слиянием](../../relational-databases/replication/publish/specify-a-merge-article-resolver.md)  
  
  
