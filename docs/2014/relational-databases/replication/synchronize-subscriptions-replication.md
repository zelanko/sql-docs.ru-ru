---
title: Синхронизация подписок (репликация) | Документация Майкрософт
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- replication
ms.topic: conceptual
helpviewer_keywords:
- synchronization [SQL Server replication], subscriptions
- subscriptions [SQL Server replication], synchronizing
- replication [SQL Server], synchronization
ms.assetid: cbe13120-8dd9-4309-88dd-07a801c68f5f
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 5efa0a0e46362fa94805a1eb9487fbe186d3176d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48123764"
---
# <a name="synchronize-subscriptions-replication"></a>Синхронизация подписок (репликация)
  Подписки синхронизируются агентами репликации. Агент распространителя синхронизирует подписки на публикации моментальных снимков и транзакций, а агент слияния синхронизирует подписки на публикации слиянием. Для синхронизации подписок и управления поведением синхронизации можно использовать среду [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], хранимые процедуры репликации и объекты RMO. В следующих разделах описывается синхронизация подписок и способы указания параметров синхронизации.  
  
## <a name="in-this-section"></a>в этом разделе  
  
-   [Создание и применение исходного моментального снимка](create-and-apply-the-initial-snapshot.md)  
  
-   [Создание моментального снимка для публикации слиянием с параметризованными фильтрами](create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md)  
  
-   [Включение инициализации из резервной копии для публикаций транзакций (SQL Server Management Studio)](enable-initialization-with-backup-for-transactional-publications.md)  
  
-   [Инициализация транзакционной подписки из резервной копии (программирование репликации на языке Transact-SQL)](initialize-a-transactional-subscription-from-a-backup.md)  
  
-   [Initialize a Subscription Manually](initialize-a-subscription-manually.md) (Инициализация подписки вручную)  
  
-   [Синхронизация подписки по запросу](synchronize-a-pull-subscription.md)  
  
-   [Синхронизация принудительной подписки](synchronize-a-push-subscription.md)  
  
-   [Повторная инициализация подписки](reinitialize-a-subscription.md)  
  
-   [Выполнение скриптов до и после применения моментального снимка (SQL Server Management Studio)](execute-scripts-before-and-after-a-snapshot-is-applied.md)  
  
-   [Выполнение скриптов во время синхронизации (программирование репликации на языке Transact-SQL)](execute-scripts-during-synchronization-replication-transact-sql-programming.md)  
  
-   [Просмотр и разрешение конфликтов данных для публикации слиянием (SQL Server Management Studio)](view-and-resolve-data-conflicts-for-merge-publications.md)  
  
-   [Просмотр конфликтов данных для публикаций транзакций (среда SQL Server Management Studio)](view-data-conflicts-for-transactional-publications-sql-server-management-studio.md)  
  
-   [Синхронизация подписки с помощью диспетчера синхронизации Windows (Windows Synchronization Manager)](synchronize-a-subscription-using-windows-synchronization-manager.md)  
  
-   [Реализация обработчика бизнес-логики для статьи публикации слиянием](implement-a-business-logic-handler-for-a-merge-article.md)  
  
-   [Отладка обработчика бизнес-логики (программирование репликации)](debug-a-business-logic-handler-replication-programming.md)  
  
-   [Control Behavior of Triggers and Constraints in Synchronization](control-behavior-of-triggers-and-constraints-in-synchronization.md) (Управление поведением триггеров и ограничений в синхронизации)  
  
-   [Реализация пользовательского арбитра конфликтов для статьи слияния](implement-a-custom-conflict-resolver-for-a-merge-article.md)  
  
## <a name="see-also"></a>См. также  
 [Синхронизация данных](synchronize-data.md)  
  
  
