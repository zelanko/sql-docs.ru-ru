---
title: Руководство разработчика. Инструкции (репликация) | Документация Майкрософт
ms.custom: ''
ms.date: 06/30/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- docset-sql-devref
- replication
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: c6c15ae6-da52-4638-93d3-61c7242e8a0b
caps.latest.revision: 12
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: fc3eeb21918886c1b738891b7b0453cbc5712212
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37285130"
---
# <a name="developer39s-guide-how-to-topics-replication"></a>Руководство разработчика. Инструкции (репликация)
  В этом разделе предоставлены ссылки на сведения о том, как выполнять программным путем задачи, связанные с репликацией.  
  
## <a name="securing-a-replication-topology"></a>Защита топологии репликации  
  
-   [Просмотр и изменение параметров безопасности репликации](security/view-and-modify-replication-security-settings.md)  
  
-   [Управление именами для входа в списке доступа к публикации](security/manage-logins-in-the-publication-access-list.md)  
  
## <a name="configuring-modifying-and-disabling-publishing-and-distribution-replication"></a>Настройка, изменение и отключение публикации и распространения (репликация)  
  
-   [Настройка публикации и распространения](configure-publishing-and-distribution.md)  
  
-   [Просмотр и изменение свойств публикации](publish/view-and-modify-publication-properties.md)  
  
-   [Disable Publishing and Distribution](disable-publishing-and-distribution.md) (Отключение публикации и распространения)  
  
## <a name="creating-modifying-and-deleting-publications-and-articles"></a>Создание, изменение и удаление публикаций и статей  
  
-   [Create a Publication](publish/create-a-publication.md)  
  
-   [Определение статьи](publish/define-an-article.md)  
  
-   [Просмотр и изменение свойств публикации](publish/view-and-modify-publication-properties.md)  
  
-   [View and Modify Article Properties (Просмотр и изменение свойств статьи)](publish/view-and-modify-article-properties.md)  
  
-   [Delete a Publication (Удаление публикации)](publish/delete-a-publication.md)  
  
-   [Delete an Article (Удаление статьи)](publish/delete-an-article.md)  
  
-   [Создание публикации из базы данных Oracle](publish/create-a-publication-from-an-oracle-database.md)  
  
-   [Set the Expiration Period for Subscriptions](publish/set-the-expiration-period-for-subscriptions.md) (Установка срока действия подписок)  
  
-   [Specify Schema Options (Указание параметров схемы)](publish/specify-schema-options.md)  
  
-   [Replicate Schema Changes (Репликация изменений схемы)](publish/replicate-schema-changes.md)  
  
-   [Manage Identity Columns (Управление столбцами идентификаторов)](publish/manage-identity-columns.md)  
  
-   [Set the Compatibility Level for Merge Publications](publish/set-the-compatibility-level-for-merge-publications.md) (Задание уровня совместимости для публикаций слиянием)  
  
### <a name="snapshot-options"></a>Параметры моментального снимка  
  
-   [Configure Snapshot Properties (Replication Transact-SQL Programming)](publish/configure-snapshot-properties-replication-transact-sql-programming.md) (Настройка свойств моментального снимка (программирование репликации на языке Transact-SQL))  
  
-   [Deliver a Snapshot Through FTP](publish/deliver-a-snapshot-through-ftp.md) (Доставка моментального снимка через FTP)  
  
### <a name="filtering-data"></a>Фильтрация данных  
  
-   [Define and Modify a Column Filter](publish/define-and-modify-a-column-filter.md) (Определение или изменение фильтра столбцов)  
  
-   [Определение и изменение статического строкового фильтра](publish/define-and-modify-a-static-row-filter.md)  
  
-   [Определение и изменение параметризованного фильтра строк для статьи публикации слиянием](publish/define-and-modify-a-parameterized-row-filter-for-a-merge-article.md)  
  
-   [Optimize Parameterized Row Filters (Оптимизация параметризованных фильтров строк)](merge/parameterized-filters-parameterized-row-filters.md)  
  
-   [Define and Modify a Join Filter Between Merge Articles](publish/define-and-modify-a-join-filter-between-merge-articles.md) (Определение и изменение фильтра соединения между статьями публикации слиянием)  
  
### <a name="transactional-replication-options"></a>Параметры репликации транзакций  
  
-   [Set the Propagation Method for Data Changes to Transactional Articles](publish/set-the-propagation-method-for-data-changes-to-transactional-articles.md) (Задание метода распространения изменений данных в транзакционные статьи)  
  
-   [Enable Updating Subscriptions for Transactional Publications](publish/enable-updating-subscriptions-for-transactional-publications.md) (Включение обновляемых подписок для публикаций транзакций)  
  
### <a name="merge-replication-options"></a>Параметры репликации слиянием  
  
-   [Define a Logical Record Relationship Between Merge Table Articles](publish/define-a-logical-record-relationship-between-merge-table-articles.md) (Определение связи логических записей между статьями таблиц слияния)  
  
-   [Specify the Processing Order of Merge Table Articles](publish/specify-the-processing-order-of-merge-table-articles.md) (Определение порядка обработки для статей таблиц слияния)  
  
-   [Specify That a Merge Table Article is Download-Only](publish/specify-that-a-merge-table-article-is-download-only.md) (Указание того, что статья таблицы публикации слиянием предназначена только для загрузки)  
  
-   [Specify That Deletes Should Not Be Tracked For Merge Articles](publish/specify-that-deletes-should-not-be-tracked-for-merge-articles.md) (Отключение отслеживания операций удаления для статей публикации слиянием)  
  
-   [Specify the Conflict Tracking and Resolution Level for Merge Articles](publish/specify-the-conflict-tracking-and-resolution-level-for-merge-articles.md) (Указание уровня отслеживания и разрешения конфликтов для статей публикации слиянием)  
  
-   [Specify a Merge Article Resolver (Определение сопоставителя статей публикации слиянием)](publish/specify-a-merge-article-resolver.md)  
  
-   [Specify Interactive Conflict Resolution for Merge Articles](publish/specify-interactive-conflict-resolution-for-merge-articles.md) (Указание интерактивного устранения конфликтов для статей публикации слиянием)  
  
## <a name="creating-modifying-and-deleting-subscriptions"></a>Создание, изменение и удаление подписок  
  
-   [Создание подписки по запросу](create-a-pull-subscription.md)  
  
-   [Просмотр и изменение свойств подписки по запросу](view-and-modify-pull-subscription-properties.md)  
  
-   [Удаление подписки по запросу](delete-a-pull-subscription.md)  
  
-   [Create a Push Subscription](create-a-push-subscription.md) (Создание принудительной подписки)  
  
-   [Просмотр и изменение свойств принудительной подписки](view-and-modify-push-subscription-properties.md)  
  
-   [Delete a Push Subscription](delete-a-push-subscription.md) (Удаление принудительной подписки)  
  
-   [Specify Synchronization Schedules](specify-synchronization-schedules.md) (Указание расписаний синхронизации)  
  
-   [Создание обновляемой подписки для публикации транзакций](create-updatable-subscription-transactional-publication-transact-sql.md)  
  
-   [Create a Subscription for a Non-SQL Server Subscriber](create-a-subscription-for-a-non-sql-server-subscriber.md) (Создание подписки для подписчика, отличного от подписчика SQL Server)  
  
## <a name="synchronizing-subscriptions"></a>Синхронизация подписок  
  
-   [Create and Apply the Initial Snapshot](create-and-apply-the-initial-snapshot.md) (Создание и применение исходного моментального снимка)  
  
-   [Создание моментального снимка для публикации слиянием с параметризованными фильтрами](create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md)  
  
-   [Инициализация транзакционной подписки из резервной копии](initialize-a-transactional-subscription-from-a-backup.md)  
  
-   [Initialize a Subscription Manually](initialize-a-subscription-manually.md) (Инициализация подписки вручную)  
  
-   [Синхронизация подписки по запросу](synchronize-a-pull-subscription.md)  
  
-   [Синхронизация принудительной подписки](synchronize-a-push-subscription.md)  
  
-   [Повторная инициализация подписки](reinitialize-a-subscription.md)  
  
-   [Выполнение скриптов во время синхронизации (программирование репликации на языке Transact-SQL)](execute-scripts-during-synchronization-replication-transact-sql-programming.md)  
  
-   [Реализация обработчика бизнес-логики для статьи публикации слиянием](implement-a-business-logic-handler-for-a-merge-article.md)  
  
-   [Отладка обработчика бизнес-логики (программирование репликации)](debug-a-business-logic-handler-replication-programming.md)  
  
-   [Control Behavior of Triggers and Constraints in Synchronization](control-behavior-of-triggers-and-constraints-in-synchronization.md) (Управление поведением триггеров и ограничений в синхронизации)  
  
-   [Реализация пользовательского арбитра конфликтов для статьи публикации слиянием](implement-a-custom-conflict-resolver-for-a-merge-article.md)  
  
## <a name="administering-a-replication-topology"></a>Администрирование топологии репликации  
  
-   [Работа с профилями агента репликации](agents/replication-agent-profiles.md)  
  
-   [Проверка данных на подписчике](validate-data-at-the-subscriber.md)  
  
-   [Управление секциями для публикации слиянием с параметризованными фильтрами](publish/manage-partitions-for-a-merge-publication-with-parameterized-filters.md)  
  
-   [Bulk-Load Data into Tables in a Merge Publication](bulk-load-data-into-tables-in-a-merge-publication.md) (Массовая загрузка данных в таблицы при публикации слиянием)  
  
-   [Clean Up Merge Metadata (Replication Transact-SQL Programming)](administration/clean-up-merge-metadata-replication-transact-sql-programming.md) (Очистка метаданных слияния (программирование репликации на языке Transact-SQL))  
  
-   [Perform a Dummy Update for a Merge Article (Replication Transact-SQL Programming)](administration/perform-a-dummy-update-for-a-merge-article-replication-transact-sql-programming.md) (Фиктивное обновление для статьи репликации слиянием (программирование репликации на языке Transact-SQL))  
  
-   [View Replicated Commands and Information in Distribution Database](monitor/view-replicated-commands-and-information-in-distribution-database.md) (Просмотр реплицированных команд и другой информации в базе данных распространителя)  
  
-   [Enable Coordinated Backups for Transactional Replication](administration/enable-coordinated-backups-for-transactional-replication.md) (Включение скоординированной архивации для репликации транзакций)  
  
-   [Администрирование одноранговой топологии (программирование репликации на языке Transact-SQL)](administration/administer-a-peer-to-peer-topology-replication-transact-sql-programming.md)  
  
-   [Quiesce a Replication Topology (Replication Transact-SQL Programming)](administration/quiesce-a-replication-topology-replication-transact-sql-programming.md) (Заморозка топологии репликации (программирование репликации на языке Transact-SQL))  
  
-   [Configure the Transaction Set Job for an Oracle Publisher](administration/configure-the-transaction-set-job-for-an-oracle-publisher.md) (Настройка задания для набора транзакции в издателе Oracle)  
  
-   [Обновление скриптов репликации (программирование репликации на языке Transact-SQL)](administration/upgrade-replication-scripts-replication-transact-sql-programming.md)  
  
## <a name="monitoring-a-replication-topology"></a>Текущее наблюдение за топологией репликации  
  
-   [Allow Non-Administrators to Use Replication Monitor](monitor/allow-non-administrators-to-use-replication-monitor.md) (Предоставление пользователям без прав администратора разрешения на использование монитора репликации)  
  
-   [Наблюдение за репликацией программным образом](monitor/monitoring-replication-overview.md)  
  
-   [View Replicated Commands and Information in Distribution Database](monitor/view-replicated-commands-and-information-in-distribution-database.md) (Просмотр реплицированных команд и другой информации в базе данных распространителя)  
  
-   [View Conflict Information for Merge Publications](view-conflict-information-for-merge-publications.md) (Просмотр сведений о конфликтах для публикаций слиянием)  
  
-   [Измерение задержки и проверка правильности соединений для репликации транзакций](monitor/measure-latency-and-validate-connections-for-transactional-replication.md)  
  
  
