---
title: "Синхронизация подписок (репликация) | Microsoft Docs"
ms.custom: ""
ms.date: "03/07/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "синхронизация [репликация SQL Server], подписки"
  - "подписки [репликация SQL Server], синхронизация"
  - "репликация [SQL Server], синхронизация"
ms.assetid: cbe13120-8dd9-4309-88dd-07a801c68f5f
caps.latest.revision: 35
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 35
---
# Синхронизация подписок (репликация)
  Подписки синхронизируются агентами репликации. Агент распространителя синхронизирует подписки на публикации моментальных снимков и транзакций, а агент слияния синхронизирует подписки на публикации слиянием. Для синхронизации подписок и управления поведением синхронизации можно использовать среду [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], хранимые процедуры репликации и объекты RMO. В следующих разделах описывается синхронизация подписок и способы указания параметров синхронизации.  
  
## В этом разделе  
  
-   [Создание и применение исходного моментального снимка](../../relational-databases/replication/create-and-apply-the-initial-snapshot.md)  
  
-   [Создание моментального снимка для публикации слиянием с параметризованными фильтрами](../../relational-databases/replication/create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md)  
  
-   [Включение инициализации с помощью резервной копии для публикаций транзакций и #40; SQL Server Management Studio & #41;](../../relational-databases/replication/enable initialization with backup for transactional publications.md)  
  
-   [Инициализация подписки на публикацию транзакций из резервной копии и #40; Программирование репликации Transact-SQL и #41;](../../relational-databases/replication/initialize a transactional subscription from a backup.md)  
  
-   [Инициализация подписки вручную](../../relational-databases/replication/initialize-a-subscription-manually.md)  
  
-   [Синхронизация подписки по запросу](../../relational-databases/replication/synchronize-a-pull-subscription.md)  
  
-   [Синхронизация принудительной подписки](../../relational-databases/replication/synchronize-a-push-subscription.md)  
  
-   [Повторная инициализация подписки](../../relational-databases/replication/reinitialize-a-subscription.md)  
  
-   [Выполнение скриптов до и после применения моментального снимка & #40; SQL Server Management Studio & #41;](../../relational-databases/replication/execute scripts before and after a snapshot is applied.md)  
  
-   [Выполнение сценариев во время синхронизации & #40; Программирование репликации Transact-SQL и #41;](../../relational-databases/replication/execute-scripts-during-synchronization-replication-transact-sql-programming.md)  
  
-   [Просмотр и разрешение конфликтов данных для публикаций слиянием & #40; SQL Server Management Studio & #41;](../../relational-databases/replication/view and resolve data conflicts for merge publications.md)  
  
-   [Просмотреть конфликты данных для публикаций транзакций и #40; SQL Server Management Studio & #41;](../../relational-databases/replication/view-data-conflicts-for-transactional-publications-sql-server-management-studio.md)  
  
-   [Синхронизировать подписку с помощью диспетчера синхронизации Windows & #40; Диспетчер синхронизации Windows & #41;](../../relational-databases/replication/synchronize a subscription using windows synchronization manager.md)  
  
-   [Реализация обработчика бизнес-логики для статьи публикации слиянием](../../relational-databases/replication/implement-a-business-logic-handler-for-a-merge-article.md)  
  
-   [Отладка обработчика бизнес-логики & #40; Программирование репликации на & #41;](../../relational-databases/replication/debug-a-business-logic-handler-replication-programming.md)  
  
-   [Управлять поведением триггеров и ограничений во время синхронизации & #40; Программирование репликации Transact-SQL и #41;](../../relational-databases/replication/control behavior of triggers and constraints in synchronization.md)  
  
-   [Implement a Custom Conflict Resolver for a Merge Article](../../relational-databases/replication/implement-a-custom-conflict-resolver-for-a-merge-article.md)  
  
## См. также:  
 [Синхронизация данных](../../relational-databases/replication/synchronize-data.md)  
  
  