---
title: "Просмотр и разрешение конфликтов данных для публикации слиянием | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- merge replication conflict resolution [SQL Server replication], viewing conflicts
- viewing conflict information
- conflict resolution [SQL Server replication], merge replication
ms.assetid: aeee9546-4480-49f9-8b1e-c71da1f056c7
caps.latest.revision: "41"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 2bc867c7c3c96d0b90793a14edd51313c5aed941
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="view-and-resolve-data-conflicts-for-merge-publications"></a>Просмотр и разрешение конфликтов данных для публикаций слиянием
  В репликации слиянием конфликты разрешаются на основе сопоставителя, указанного для каждой статьи. По умолчанию для разрешения конфликтов не требуется вмешательство пользователя. Однако просмотреть конфликты и изменить результат разрешения конфликта можно в средстве просмотра конфликтов репликации [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 Данные конфликтов доступны в средстве просмотра конфликтов репликации в течение времени, указанном для срока хранения конфликтов (по умолчанию это время равно 14 дням). Чтобы установить срок хранения конфликтов, выполните любое из указанных ниже действий:  
  
-   Укажите значение срока хранения для параметра **@conflict_retention** хранимой процедуры [sp_addmergepublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md).  
  
-   Задайте значение **conflict_retention** для параметра **@property** и значение срока хранения для параметра **@value** хранимой процедуры [sp_changepublication (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md).  
  
 По умолчанию сведения о конфликтах сохраняются:  
  
-   На издателе и подписчике, если уровень совместимости публикации 90RTM или выше.  
  
-   На издателе, если уровень совместимости публикации ниже, чем 80RTM.  
  
-   На издателе, если подписчики используют [!INCLUDE[ssEW](../../includes/ssew-md.md)]. Данные о конфликтах не могут храниться на подписчиках, использующих [!INCLUDE[ssEW](../../includes/ssew-md.md)] .  
  
 Хранение информации о конфликте управляется с помощью свойства публикации **conflict_logging** . Дополнительные сведения см. в статьях [sp_addmergepublication (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md) и [sp_changemergepublication (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md).  
  
 Возможно также разрешение конфликтов в интерактивном режиме во время синхронизации с помощью интерактивного сопоставителя [!INCLUDE[msCoName](../../includes/msconame-md.md)] . Интерактивный сопоставитель доступен через диспетчер синхронизации [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows. Дополнительные сведения см. в статье [Синхронизация подписки с помощью диспетчера синхронизации Windows (диспетчер синхронизации Windows)](../../relational-databases/replication/synchronize-a-subscription-using-windows-synchronization-manager.md).  
  
### <a name="to-view-and-resolve-conflicts-for-merge-publications"></a>Просмотр и разрешение конфликтов для публикаций слиянием  
  
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
  
    -   Нажать кнопку свойств**…**) для просмотра дополнительной информации о столбце, вовлеченном в конфликт.  
  
    -   Измените данные в столбце **Выигравший вариант** или **Проигравший вариант** до отправки данных (данные доступны только для чтения, если столбец окрашен в серый цвет).  
  
    -   Щелкните **Отправить выигравший** , чтобы принять строку, определенную как победитель в конфликте.  
  
    -   Щелкните **Отправить проигравший** , чтобы переопределить разрешение конфликта и передать значение, определенное как проигравший в конфликте на все узлы в топологии.  
  
    -   Выбрать **Записать подробности этого конфликта** , чтобы записать данные конфликта в файл. Для указания размещения файла наведите указатель на меню **Просмотр** и щелкните **Параметры**. Введите значение или нажмите кнопку обзора (**...**), а затем перейдите к необходимому файлу. Нажмите кнопку **ОК** для выхода из диалогового окна **Параметры** .  
  
6.  Закройте средство просмотра конфликтов репликации.  
  
## <a name="see-also"></a>См. также:  
 [Advanced Merge Replication Conflict Detection and Resolution](../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md)   
 [Определение арбитра для статей публикации слиянием](../../relational-databases/replication/publish/specify-a-merge-article-resolver.md)  
  
  
