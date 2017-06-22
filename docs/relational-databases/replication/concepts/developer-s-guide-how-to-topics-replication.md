---
title: "Руководство разработчика. Инструкции (репликация) | Документация Майкрософт"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
ms.assetid: c6c15ae6-da52-4638-93d3-61c7242e8a0b
caps.latest.revision: 12
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 288ed137e701d6cfb416d12b6ff2176c59ec0278
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="developer39s-guide-how-to-topics-replication"></a>Руководство разработчика. Инструкции (репликация)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  В этом разделе предоставлены ссылки на сведения о том, как выполнять программным путем задачи, связанные с репликацией.  
  
## <a name="securing-a-replication-topology"></a>Защита топологии репликации  
  
-   [Просмотр и изменение параметров безопасности репликации](../../../relational-databases/replication/security/view-and-modify-replication-security-settings.md)  
  
-   [Управление именами для входа в списке доступа к публикации](../../../relational-databases/replication/security/manage-logins-in-the-publication-access-list.md)  
  
## <a name="configuring-modifying-and-disabling-publishing-and-distribution-replication"></a>Настройка, изменение и отключение публикации и распространения (репликация)  
  
-   [Настройка публикации и распространения](../../../relational-databases/replication/configure-publishing-and-distribution.md)  
  
-   [Просмотр и изменение свойств публикации](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md)  
  
-   [Disable Publishing and Distribution](../../../relational-databases/replication/disable-publishing-and-distribution.md) (Отключение публикации и распространения)  
  
## <a name="creating-modifying-and-deleting-publications-and-articles"></a>Создание, изменение и удаление публикаций и статей  
  
-   [Create a Publication](../../../relational-databases/replication/publish/create-a-publication.md)  
  
-   [Определение статьи](../../../relational-databases/replication/publish/define-an-article.md)  
  
-   [Просмотр и изменение свойств публикации](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md)  
  
-   [View and Modify Article Properties](../../../relational-databases/replication/publish/view-and-modify-article-properties.md) (Просмотр и изменение свойств статьи)  
  
-   [Delete a Publication](../../../relational-databases/replication/publish/delete-a-publication.md) (Удаление публикации)  
  
-   [Delete an Article](../../../relational-databases/replication/publish/delete-an-article.md) (Удаление статьи)  
  
-   [Создание публикации из базы данных Oracle](../../../relational-databases/replication/publish/create-a-publication-from-an-oracle-database.md)  
  
-   [Set the Expiration Period for Subscriptions](../../../relational-databases/replication/publish/set-the-expiration-period-for-subscriptions.md) (Установка срока действия подписок)  
  
-   [Specify Schema Options](../../../relational-databases/replication/publish/specify-schema-options.md) (Указание параметров схемы)  
  
-   [Replicate Schema Changes](../../../relational-databases/replication/publish/replicate-schema-changes.md) (Репликация изменений схемы)  
  
-   [Manage Identity Columns](../../../relational-databases/replication/publish/manage-identity-columns.md) (Управление столбцами идентификаторов)  
  
-   [Set the Compatibility Level for Merge Publications](../../../relational-databases/replication/publish/set-the-compatibility-level-for-merge-publications.md) (Задание уровня совместимости для публикаций слиянием)  
  
### <a name="snapshot-options"></a>Параметры моментального снимка  
  
-   [Configure Snapshot Properties (Replication Transact-SQL Programming)](../../../relational-databases/replication/publish/configure-snapshot-properties-replication-transact-sql-programming.md) (Настройка свойств моментального снимка (программирование репликации на языке Transact-SQL))  
  
-   [Deliver a Snapshot Through FTP](../../../relational-databases/replication/publish/deliver-a-snapshot-through-ftp.md) (Доставка моментального снимка через FTP)  
  
### <a name="filtering-data"></a>Фильтрация данных  
  
-   [Define and Modify a Column Filter](../../../relational-databases/replication/publish/define-and-modify-a-column-filter.md) (Определение или изменение фильтра столбцов)  
  
-   [Определение и изменение статического строкового фильтра](../../../relational-databases/replication/publish/define-and-modify-a-static-row-filter.md)  
  
-   [Определение и изменение параметризованного фильтра строк для статьи публикации слиянием](../../../relational-databases/replication/publish/define-and-modify-a-parameterized-row-filter-for-a-merge-article.md)  
  
-   [Optimize Parameterized Row Filters](../../../relational-databases/replication/publish/optimize-parameterized-row-filters.md) (Оптимизация параметризованных фильтров строк)  
  
-   [Define and Modify a Join Filter Between Merge Articles](../../../relational-databases/replication/publish/define-and-modify-a-join-filter-between-merge-articles.md) (Определение и изменение фильтра соединения между статьями публикации слиянием)  
  
### <a name="transactional-replication-options"></a>Параметры репликации транзакций  
  
-   [Set the Propagation Method for Data Changes to Transactional Articles](../../../relational-databases/replication/publish/set-the-propagation-method-for-data-changes-to-transactional-articles.md) (Задание метода распространения изменений данных в транзакционные статьи)  
  
-   [Enable Updating Subscriptions for Transactional Publications](../../../relational-databases/replication/publish/enable-updating-subscriptions-for-transactional-publications.md) (Включение обновляемых подписок для публикаций транзакций)  
  
### <a name="merge-replication-options"></a>Параметры репликации слиянием  
  
-   [Define a Logical Record Relationship Between Merge Table Articles](../../../relational-databases/replication/publish/define-a-logical-record-relationship-between-merge-table-articles.md) (Определение связи логических записей между статьями таблиц слияния)  
  
-   [Specify the Processing Order of Merge Table Articles](../../../relational-databases/replication/publish/specify-the-processing-order-of-merge-table-articles.md) (Определение порядка обработки для статей таблиц слияния)  
  
-   [Specify That a Merge Table Article is Download-Only](../../../relational-databases/replication/publish/specify-that-a-merge-table-article-is-download-only.md) (Указание того, что статья таблицы публикации слиянием предназначена только для загрузки)  
  
-   [Specify That Deletes Should Not Be Tracked For Merge Articles](../../../relational-databases/replication/publish/specify-that-deletes-should-not-be-tracked-for-merge-articles.md) (Отключение отслеживания операций удаления для статей публикации слиянием)  
  
-   [Specify the Conflict Tracking and Resolution Level for Merge Articles](../../../relational-databases/replication/publish/specify-the-conflict-tracking-and-resolution-level-for-merge-articles.md) (Указание уровня отслеживания и разрешения конфликтов для статей публикации слиянием)  
  
-   [Specify a Merge Article Resolver](../../../relational-databases/replication/publish/specify-a-merge-article-resolver.md) (Определение сопоставителя статей публикации слиянием)  
  
-   [Specify Interactive Conflict Resolution for Merge Articles](../../../relational-databases/replication/publish/specify-interactive-conflict-resolution-for-merge-articles.md) (Указание интерактивного устранения конфликтов для статей публикации слиянием)  
  
## <a name="creating-modifying-and-deleting-subscriptions"></a>Создание, изменение и удаление подписок  
  
-   [Создание подписки по запросу](../../../relational-databases/replication/create-a-pull-subscription.md)  
  
-   [Просмотр и изменение свойств подписки по запросу](../../../relational-databases/replication/view-and-modify-pull-subscription-properties.md)  
  
-   [Удаление подписки по запросу](../../../relational-databases/replication/delete-a-pull-subscription.md)  
  
-   [Create a Push Subscription](../../../relational-databases/replication/create-a-push-subscription.md) (Создание принудительной подписки)  
  
-   [Просмотр и изменение свойств принудительной подписки](../../../relational-databases/replication/view-and-modify-push-subscription-properties.md)  
  
-   [Delete a Push Subscription](../../../relational-databases/replication/delete-a-push-subscription.md) (Удаление принудительной подписки)  
  
-   [Specify Synchronization Schedules](../../../relational-databases/replication/specify-synchronization-schedules.md) (Указание расписаний синхронизации)  
  
-   [Создание обновляемой подписки для публикации транзакций](../../../relational-databases/replication/publish/create-updatable-subscription-to-transactional-publication.md)
  
-   [Create a Subscription for a Non-SQL Server Subscriber](../../../relational-databases/replication/create-a-subscription-for-a-non-sql-server-subscriber.md) (Создание подписки для подписчика, отличного от подписчика SQL Server)  
  
## <a name="synchronizing-subscriptions"></a>Синхронизация подписок  
  
-   [Create and Apply the Initial Snapshot](../../../relational-databases/replication/create-and-apply-the-initial-snapshot.md) (Создание и применение исходного моментального снимка)  
  
-   [Создание моментального снимка для публикации слиянием с параметризованными фильтрами](../../../relational-databases/replication/create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md)  
  
-   [Инициализация транзакционной подписки из резервной копии](../../../relational-databases/replication/initialize-a-transactional-subscription-from-a-backup.md)  
  
-   [Initialize a Subscription Manually](../../../relational-databases/replication/initialize-a-subscription-manually.md) (Инициализация подписки вручную)  
  
-   [Синхронизация подписки по запросу](../../../relational-databases/replication/synchronize-a-pull-subscription.md)  
  
-   [Синхронизация принудительной подписки](../../../relational-databases/replication/synchronize-a-push-subscription.md)  
  
-   [Повторная инициализация подписки](../../../relational-databases/replication/reinitialize-a-subscription.md)  
  
-   [Выполнение скриптов во время синхронизации (программирование репликации на языке Transact-SQL)](../../../relational-databases/replication/execute-scripts-during-synchronization-replication-transact-sql-programming.md)  
  
-   [Реализация обработчика бизнес-логики для статьи публикации слиянием](../../../relational-databases/replication/implement-a-business-logic-handler-for-a-merge-article.md)  
  
-   [Отладка обработчика бизнес-логики (программирование репликации)](../../../relational-databases/replication/debug-a-business-logic-handler-replication-programming.md)  
  
-   [Control Behavior of Triggers and Constraints in Synchronization](../../../relational-databases/replication/control-behavior-of-triggers-and-constraints-in-synchronization.md) (Управление поведением триггеров и ограничений в синхронизации)  
  
-   [Реализация пользовательского арбитра конфликтов для статьи публикации слиянием](../../../relational-databases/replication/implement-a-custom-conflict-resolver-for-a-merge-article.md)  
  
## <a name="administering-a-replication-topology"></a>Администрирование топологии репликации  
  
-   [Работа с профилями агента репликации](../../../relational-databases/replication/agents/work-with-replication-agent-profiles.md)  
  
-   [Проверка данных на подписчике](../../../relational-databases/replication/validate-data-at-the-subscriber.md)  
  
-   [Управление секциями для публикации слиянием с параметризованными фильтрами](../../../relational-databases/replication/publish/manage-partitions-for-a-merge-publication-with-parameterized-filters.md)  
  
-   [Bulk-Load Data into Tables in a Merge Publication](../../../relational-databases/replication/bulk-load-data-into-tables-in-a-merge-publication.md) (Массовая загрузка данных в таблицы при публикации слиянием)  
  
-   [Clean Up Merge Metadata (Replication Transact-SQL Programming)](../../../relational-databases/replication/administration/clean-up-merge-metadata-replication-transact-sql-programming.md) (Очистка метаданных слияния (программирование репликации на языке Transact-SQL))  
  
-   [Perform a Dummy Update for a Merge Article (Replication Transact-SQL Programming)](../../../relational-databases/replication/administration/perform-a-dummy-update-for-a-merge-article-replication-transact-sql-programming.md) (Фиктивное обновление для статьи репликации слиянием (программирование репликации на языке Transact-SQL))  
  
-   [View Replicated Commands and Information in Distribution Database](../../../relational-databases/replication/monitor/view-replicated-commands-and-information-in-distribution-database.md) (Просмотр реплицированных команд и другой информации в базе данных распространителя)  
  
-   [Enable Coordinated Backups for Transactional Replication](../../../relational-databases/replication/administration/enable-coordinated-backups-for-transactional-replication.md) (Включение скоординированной архивации для репликации транзакций)  
  
-   [Администрирование одноранговой топологии (программирование репликации на языке Transact-SQL)](../../../relational-databases/replication/administration/administer-a-peer-to-peer-topology-replication-transact-sql-programming.md)  
  
-   [Quiesce a Replication Topology (Replication Transact-SQL Programming)](../../../relational-databases/replication/administration/quiesce-a-replication-topology-replication-transact-sql-programming.md) (Заморозка топологии репликации (программирование репликации на языке Transact-SQL))  
  
-   [Configure the Transaction Set Job for an Oracle Publisher](../../../relational-databases/replication/administration/configure-the-transaction-set-job-for-an-oracle-publisher.md) (Настройка задания для набора транзакции в издателе Oracle)  
  
-   [Обновление скриптов репликации (программирование репликации на языке Transact-SQL)](../../../relational-databases/replication/administration/upgrade-replication-scripts-replication-transact-sql-programming.md)  
  
## <a name="monitoring-a-replication-topology"></a>Текущее наблюдение за топологией репликации  
  
-   [Allow Non-Administrators to Use Replication Monitor](../../../relational-databases/replication/monitor/allow-non-administrators-to-use-replication-monitor.md) (Предоставление пользователям без прав администратора разрешения на использование монитора репликации)  
  
-   [Наблюдение за репликацией программным образом](../../../relational-databases/replication/monitor/programmatically-monitor-replication.md)  
  
-   [View Replicated Commands and Information in Distribution Database](../../../relational-databases/replication/monitor/view-replicated-commands-and-information-in-distribution-database.md) (Просмотр реплицированных команд и другой информации в базе данных распространителя)  
  
-   [View Conflict Information for Merge Publications](../../../relational-databases/replication/view-conflict-information-for-merge-publications.md) (Просмотр сведений о конфликтах для публикаций слиянием)  
  
-   [Измерение задержки и проверка правильности соединений для репликации транзакций](../../../relational-databases/replication/monitor/measure-latency-and-validate-connections-for-transactional-replication.md)  
  
  
