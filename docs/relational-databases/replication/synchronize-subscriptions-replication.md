---
title: Синхронизация подписок (репликация) | Документация Майкрософт
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- synchronization [SQL Server replication], subscriptions
- subscriptions [SQL Server replication], synchronizing
- replication [SQL Server], synchronization
ms.assetid: cbe13120-8dd9-4309-88dd-07a801c68f5f
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: ed208c81fe7b3459f22e013117ed1f7cf51ec314
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47796562"
---
# <a name="synchronize-subscriptions-replication"></a>Синхронизация подписок (репликация)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Подписки синхронизируются агентами репликации. Агент распространителя синхронизирует подписки на публикации моментальных снимков и транзакций, а агент слияния синхронизирует подписки на публикации слиянием. Для синхронизации подписок и управления поведением синхронизации можно использовать среду [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], хранимые процедуры репликации и объекты RMO. В следующих разделах описывается синхронизация подписок и способы указания параметров синхронизации.  
  
## <a name="in-this-section"></a>в этом разделе  
  
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
  
-   [Реализация обработчика бизнес-логики для статьи публикации слиянием](../../relational-databases/replication/implement-a-business-logic-handler-for-a-merge-article.md)  
  
-   [Отладка обработчика бизнес-логики (программирование репликации)](../../relational-databases/replication/debug-a-business-logic-handler-replication-programming.md)  
  
-   [Control Behavior of Triggers and Constraints in Synchronization](../../relational-databases/replication/control-behavior-of-triggers-and-constraints-in-synchronization.md) (Управление поведением триггеров и ограничений в синхронизации)  
  
-   [Реализация пользовательского арбитра конфликтов для статьи слияния](../../relational-databases/replication/implement-a-custom-conflict-resolver-for-a-merge-article.md)  
  
## <a name="see-also"></a>См. также:  
 [Синхронизация данных](../../relational-databases/replication/synchronize-data.md)  
  
  
