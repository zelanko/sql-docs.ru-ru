---
title: Урок 3. Синхронизация подписки на публикацию слиянием | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], tutorials
ms.assetid: 49008384-2c55-4080-a890-9bceb40e4d6d
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: 847b833d793d3b572b44bcb77903c534300109b7
ms.sourcegitcommit: 7aa6beaaf64daf01b0e98e6c63cc22906a77ed04
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/09/2019
ms.locfileid: "54128474"
---
# <a name="lesson-3-synchronizing-the-subscription-to-the-merge-publication"></a>Урок 3. Синхронизация подписки на публикацию слиянием
  На этом занятии будет запущен агент слияния для инициализации подписки с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Эта процедура также используется для синхронизации с издателем. Это занятие требует, что выполнены предыдущем занятии [занятии 2: Создание подписки на публикацию слиянием](lesson-2-creating-a-subscription-to-the-merge-publication.md).  
  
### <a name="to-start-synchronization-and-initialize-the-subscription"></a>Запуск синхронизации и инициализация подписки  
  
1.  Подключитесь к подписчику в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], раскройте узел сервера, а затем папку **Репликация** .  
  
2.  В папке **Локальные подписки** щелкните правой кнопкой мыши подписку в базе данных **SalesOrdersReplica** и выберите пункт **Просмотр состояния синхронизации**.  
  
3.  Нажмите кнопку **Пуск** , чтобы инициализировать подписку.  
  
## <a name="next-steps"></a>Следующие шаги  
 Был запущен агент слияния для синхронизации и инициализации подписки. Можно вставить, обновить или удалить данные из таблицы **SalesOrderHeader** или **SalesOrderDetail** на стороне издателя или подписчика, повторить эту процедуру, когда доступно соединение сети, для синхронизации данных между издателем и подписчиком, после чего выполнить запросы к таблице **SalesOrderHeader** или **SalesOrderDetail** на другом сервере, чтобы просмотреть реплицированные изменения.  
  
 На этом раздел «Репликация данных с мобильными клиентами» завершается. Похожий учебник, использующий репликацию транзакций, см. в разделе [руководства: Репликация данных между постоянно соединенными серверами](tutorial-replicating-data-between-continuously-connected-servers.md).  
  
## <a name="see-also"></a>См. также  
 [Инициализация подписки с помощью моментального снимка](initialize-a-subscription-with-a-snapshot.md)   
 [Синхронизация данных](synchronize-data.md)   
 [Синхронизация подписки по запросу](synchronize-a-pull-subscription.md)  
  
  
