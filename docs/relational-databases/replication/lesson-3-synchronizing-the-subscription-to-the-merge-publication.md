---
title: "Занятие 3. Синхронизация подписки на публикацию слиянием | Документация Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016
helpviewer_keywords:
- replication [SQL Server], tutorials
ms.assetid: 49008384-2c55-4080-a890-9bceb40e4d6d
caps.latest.revision: 14
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 2f80d0e6e39bea34899501368e7c7dfb693be1c6
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="lesson-3-synchronizing-the-subscription-to-the-merge-publication"></a>Занятие 3. Синхронизация подписки на публикацию слиянием
На этом занятии будет запущен агент слияния для инициализации подписки с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Эта процедура также используется для синхронизации с издателем. Приступать к этому занятию нужно только по завершении предыдущего: [Занятие 2. Создание подписки на публикацию слиянием](../../relational-databases/replication/lesson-2-creating-a-subscription-to-the-merge-publication.md).  
  
### <a name="to-start-synchronization-and-initialize-the-subscription"></a>Запуск синхронизации и инициализация подписки  
  
1.  Подключитесь к подписчику в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], раскройте узел сервера, а затем папку **Репликация** .  
  
2.  В папке **Локальные подписки** щелкните правой кнопкой мыши подписку в базе данных **SalesOrdersReplica** и выберите пункт **Просмотр состояния синхронизации**.  
  
3.  Нажмите кнопку **Пуск** , чтобы инициализировать подписку.  
  
## <a name="next-steps"></a>Следующие шаги  
Был запущен агент слияния для синхронизации и инициализации подписки. Можно вставить, обновить или удалить данные из таблицы **SalesOrderHeader** или **SalesOrderDetail** на стороне издателя или подписчика, повторить эту процедуру, когда доступно соединение сети, для синхронизации данных между издателем и подписчиком, после чего выполнить запросы к таблице **SalesOrderHeader** или **SalesOrderDetail** на другом сервере, чтобы просмотреть реплицированные изменения.  
  
На этом раздел «Репликация данных с мобильными клиентами» завершается. Похожий учебник, использующий репликацию транзакций, см. в разделе [Tutorial: Replicating Data Between Continuously Connected Servers](../../relational-databases/replication/tutorial-replicating-data-between-continuously-connected-servers.md).  
  
## <a name="see-also"></a>См. также:  
[Инициализация подписки с помощью моментального снимка](../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md)  
[Синхронизация данных](../../relational-databases/replication/synchronize-data.md)  
[Синхронизация подписки по запросу](../../relational-databases/replication/synchronize-a-pull-subscription.md)  
  
  
  

