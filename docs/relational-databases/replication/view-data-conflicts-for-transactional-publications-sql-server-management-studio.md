---
title: "Просмотр конфликтов данных для публикаций транзакций (среда SQL Server Management Studio) | Документация Майкрософт"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- conflict resolution [SQL Server replication], queued updating subscriptions
- queued updating subscriptions [SQL Server replication]
- viewing conflict information
ms.assetid: 9977dd75-b0de-4376-9c13-86d80567d8aa
caps.latest.revision: "36"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 3997eab4594c4c44b2366bdfa8b9c2e0bd3ec42d
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="view-data-conflicts-for-transactional-publications-sql-server-management-studio"></a>просмотреть конфликты данных для публикаций транзакций (среда SQL Server Management Studio)
  В средстве просмотра конфликтов репликации [!INCLUDE[msCoName](../../includes/msconame-md.md)] можно просматривать конфликты одноранговой репликации транзакций и репликации транзакций с подписками, обновляемыми посредством очередей. Сведения о том, как обнаруживать и разрешать конфликты, см. в статьях [Обнаружение конфликтов в одноранговой репликации](../../relational-databases/replication/transactional/peer-to-peer-conflict-detection-in-peer-to-peer-replication.md) и [Настройка параметров разрешения конфликтов для обновления посредством очередей (среда SQL Server Management Studio)](../../relational-databases/replication/publish/set-queued-updating-conflict-resolution-options-sql-server-management-studio.md).  
  
 Доступность данных конфликта зависит от типа репликации и срока хранения конфликта.  
  
-   При одноранговой репликации агент распространителя при обнаружении конфликта завершается ошибкой. Эта ошибка заносится в журнал, но данные конфликта не записываются в таблицу конфликтов и поэтому недоступны для просмотра. Если агенту распространителя разрешено продолжение работы, то конфликт заносится в локальный журнал на каждом из узлов, где он обнаружен. Дополнительные сведения см. в подразделе «Обработка конфликтов» раздела [Conflict Detection in Peer-to-Peer Replication](../../relational-databases/replication/transactional/peer-to-peer-conflict-detection-in-peer-to-peer-replication.md).  
  
-   В подписках, обновляемых посредством очередей, доступны данные любого конфликта. Данные конфликтов доступны в средстве просмотра конфликтов репликации в течение времени, указанного для срока хранения конфликтов (по умолчанию это время равно 14 дням). Чтобы настроить срок хранения конфликтов, выполните одно из следующих действий.  
  
    -   Укажите значение срока хранения для параметра @conflict_retention хранимой процедуры [sp_addpublication](../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md).  
  
    -   Задайте значение **'conflict_retention'** для параметра @property и значение срока хранения для параметра @value хранимой процедуры [sp_changepublication](../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md).  
  
### <a name="to-view-conflicts"></a>Просмотр конфликтов  
  
1.  Подключитесь к соответствующему серверу в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], затем раскройте узел сервера.  
  
    -   Для одноранговой репликации это узел, на котором произошел конфликт.  
  
    -   Для подписок, обновляемых посредством очередей, это издатель.  
  
2.  Раскройте папку **Репликация** , а затем папку **Локальные публикации** .  
  
3.  Щелкните правой кнопкой мыши публикацию, для которой требуется просмотреть конфликты, а затем щелкните **Просмотреть конфликты**.  
  
4.  В диалоговом окне **Выбор таблицы с конфликтами** выберите базу данных, публикацию и таблицу, для которой необходимо просмотреть конфликты.  
  
5.  В средстве просмотра конфликтов репликации можно выполнить следующие действия:  
  
    -   Отфильтровать строки с помощью кнопок, расположенных справа от верхней сетки.  
  
    -   Выбрать строку в верхней сетке для отображения информации об этой строке в нижней сетке.  
  
    -   Выбрать одну или несколько строк в верхней сетке, а затем щелкнуть **Удалить**, чтобы удалить строку из таблицы метаданных конфликтов.  
  
    -   Нажать кнопку свойств**…**) для просмотра дополнительной информации о столбце, вовлеченном в конфликт.  
  
    -   Выбрать **Записать подробности этого конфликта** , чтобы записать данные конфликта в файл. Для указания размещения файла наведите указатель на меню **Просмотр** и щелкните **Параметры**. Введите значение или нажмите кнопку обзора (**...**), а затем перейдите к необходимому файлу. Нажмите **OK** , чтобы закрыть диалоговое окно **Параметры** .  
  
6.  Закройте средство просмотра конфликтов репликации.  
  
## <a name="see-also"></a>См. также:  
 [Одноранговая репликация транзакций](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md)   
 [Queued Updating Conflict Detection and Resolution](../../relational-databases/replication/transactional/updatable-subscriptions-queued-updating-conflict-resolution.md)  
  
  
