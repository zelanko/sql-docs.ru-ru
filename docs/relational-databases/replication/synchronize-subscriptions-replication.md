---
title: "Синхронизация подписок (репликация) | Документация Майкрософт"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- synchronization [SQL Server replication], subscriptions
- subscriptions [SQL Server replication], synchronizing
- replication [SQL Server], synchronization
ms.assetid: cbe13120-8dd9-4309-88dd-07a801c68f5f
caps.latest.revision: "35"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c03c4e5ac9974003e5be7e7f647d425618d06fd7
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="synchronize-subscriptions-replication"></a>Синхронизация подписок (репликация)
  Подписки синхронизируются агентами репликации. Агент распространителя синхронизирует подписки на публикации моментальных снимков и транзакций, а агент слияния синхронизирует подписки на публикации слиянием. Для синхронизации подписок и управления поведением синхронизации можно использовать среду [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], хранимые процедуры репликации и объекты RMO. В следующих разделах описывается синхронизация подписок и способы указания параметров синхронизации.  
  
## <a name="in-this-section"></a>В этом разделе  
  
-   [Создание и применение исходного моментального снимка](../../relational-databases/replication/create-and-apply-the-initial-snapshot.md)  
  
-   [Создание моментального снимка для публикации слиянием с параметризованными фильтрами](../../relational-databases/replication/create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md)  
  
-   [Включение инициализации из резервной копии для публикаций транзакций (SQL Server Management Studio)](../../relational-databases/replication/enable-initialization-with-backup-for-transactional-publications.md)  
  
-   [Инициализация транзакционной подписки из резервной копии (программирование репликации на языке Transact-SQL)](../../relational-databases/replication/initialize-a-transactional-subscription-from-a-backup.md)  
  
-   [Initialize a Subscription Manually](../../relational-databases/replication/initialize-a-subscription-manually.md) (Инициализация подписки вручную)  
  
-   [Синхронизация подписки по запросу](../../relational-databases/replication/synchronize-a-pull-subscription.md)  
  
-   [Синхронизация принудительной подписки](../../relational-databases/replication/synchronize-a-push-subscription.md)  
  
-   [Повторная инициализация подписки](../../relational-databases/replication/reinitialize-a-subscription.md)  
  
-   [Выполнение скриптов до и после применения моментального снимка (SQL Server Management Studio)](../../relational-databases/replication/execute-scripts-before-and-after-a-snapshot-is-applied.md)  
  
-   [Выполнение скриптов во время синхронизации (программирование репликации на языке Transact-SQL)](../../relational-databases/replication/execute-scripts-during-synchronization-replication-transact-sql-programming.md)  
  
-   [Просмотр и разрешение конфликтов данных для публикации слиянием (SQL Server Management Studio)](../../relational-databases/replication/view-and-resolve-data-conflicts-for-merge-publications.md)  
  
-   [Просмотр конфликтов данных для публикаций транзакций (среда SQL Server Management Studio)](../../relational-databases/replication/view-data-conflicts-for-transactional-publications-sql-server-management-studio.md)  
  
-   [Синхронизация подписки с помощью диспетчера синхронизации Windows (Windows Synchronization Manager)](../../relational-databases/replication/synchronize-a-subscription-using-windows-synchronization-manager.md)  
  
-   [Implement a Business Logic Handler for a Merge Article](../../relational-databases/replication/implement-a-business-logic-handler-for-a-merge-article.md)  
  
-   [Отладка обработчика бизнес-логики (программирование репликации)](../../relational-databases/replication/debug-a-business-logic-handler-replication-programming.md)  
  
-   [Control Behavior of Triggers and Constraints in Synchronization](../../relational-databases/replication/control-behavior-of-triggers-and-constraints-in-synchronization.md) (Управление поведением триггеров и ограничений в синхронизации)  
  
-   [Реализация пользовательского арбитра конфликтов для статьи слияния](../../relational-databases/replication/implement-a-custom-conflict-resolver-for-a-merge-article.md)  
  
## <a name="see-also"></a>См. также:  
 [Синхронизация данных](../../relational-databases/replication/synchronize-data.md)  
  
  
