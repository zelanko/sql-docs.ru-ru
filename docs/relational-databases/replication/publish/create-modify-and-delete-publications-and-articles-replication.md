---
title: Создание, изменение и удаление публикаций и статей (репликация) | Документация Майкрософт
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- publications [SQL Server replication], creating
- articles [SQL Server replication], defining
ms.assetid: e66d06ec-a12b-444d-875b-77f958af2f21
caps.latest.revision: 36
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8680a77f6a7ac44c9e3b72636db79f325e4d5db8
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="create-modify-and-delete-publications-and-articles-replication"></a>Создание, изменение и удаление публикаций и статей (репликация)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Этот раздел документации содержит сведения о процедурах для задач, связанных с созданием публикаций и определением статей.  
  
## <a name="in-this-section"></a>в этом разделе  
  
-   [Create a Publication](../../../relational-databases/replication/publish/create-a-publication.md)  
  
-   [Определение статьи](../../../relational-databases/replication/publish/define-an-article.md)  
  
-   [Просмотр и изменение свойств публикации](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md)  
  
-   [View and Modify Article Properties (Просмотр и изменение свойств статьи)](../../../relational-databases/replication/publish/view-and-modify-article-properties.md)  
  
-   [Delete a Publication (Удаление публикации)](../../../relational-databases/replication/publish/delete-a-publication.md)  
  
-   [Delete an Article (Удаление статьи)](../../../relational-databases/replication/publish/delete-an-article.md)  
  
-   [Создание публикации из базы данных Oracle](../../../relational-databases/replication/publish/create-a-publication-from-an-oracle-database.md)  
  
-   [Set the Expiration Period for Subscriptions](../../../relational-databases/replication/publish/set-the-expiration-period-for-subscriptions.md) (Установка срока действия подписок)  
  
-   [Specify Schema Options (Указание параметров схемы)](../../../relational-databases/replication/publish/specify-schema-options.md)  
  
-   [Replicate Schema Changes (Репликация изменений схемы)](../../../relational-databases/replication/publish/replicate-schema-changes.md)  
  
-   [Manage Identity Columns (Управление столбцами идентификаторов)](../../../relational-databases/replication/publish/manage-identity-columns.md)  
  
-   [Set the Compatibility Level for Merge Publications](../../../relational-databases/replication/publish/set-the-compatibility-level-for-merge-publications.md) (Задание уровня совместимости для публикаций слиянием)  
  
## <a name="snapshot-options"></a>Параметры моментального снимка  
  
-   [Указание формата моментальных снимков (среда SQL Server Management Studio)](../../../relational-databases/replication/publish/specify-snapshot-format-sql-server-management-studio.md)  
  
-   [Изменение местоположения папки моментальных снимков (среда SQL Server Management Studio)](../../../relational-databases/replication/publish/specify-an-alternate-snapshot-folder-location-sql-server-management-studio.md)  
  
-   [Сжатие файлов моментальных снимков (среда SQL Server Management Studio)](../../../relational-databases/replication/publish/compress-snapshot-files-sql-server-management-studio.md)  
  
-   [Настройка свойств моментального снимка (программирование репликации на языке Transact-SQL)](../../../relational-databases/replication/publish/configure-snapshot-properties-replication-transact-sql-programming.md)  
  
-   [Выполнение скриптов до и после применения моментального снимка (SQL Server Management Studio)](../../../relational-databases/replication/execute-scripts-before-and-after-a-snapshot-is-applied.md)  
  
-   [Доставка моментального снимка через FTP](../../../relational-databases/replication/publish/deliver-a-snapshot-through-ftp.md)  
  
## <a name="filtering-data"></a>Фильтрация данных  
  
-   [Define and Modify a Column Filter](../../../relational-databases/replication/publish/define-and-modify-a-column-filter.md) (Определение или изменение фильтра столбцов)  
  
-   [Определение и изменение статического строкового фильтра](../../../relational-databases/replication/publish/define-and-modify-a-static-row-filter.md)  
  
-   [Определение и изменение параметризованного фильтра строк для статьи публикации слиянием](../../../relational-databases/replication/publish/define-and-modify-a-parameterized-row-filter-for-a-merge-article.md)  
  
-   [Optimize Parameterized Row Filters (Оптимизация параметризованных фильтров строк)](../../../relational-databases/replication/publish/optimize-parameterized-row-filters.md)  
  
-   [Определение и изменение фильтра соединения между статьями публикации слиянием](../../../relational-databases/replication/publish/define-and-modify-a-join-filter-between-merge-articles.md)  
  
-   [Автоматическое формирование набора фильтров соединения между статьями публикации слиянием (среда SQL Server Management Studio)](../../../relational-databases/replication/publish/automatically-generate-join-filters-between-merge-articles.md)  
  
## <a name="transactional-replication-options"></a>Параметры репликации транзакций  
  
-   [Set the Propagation Method for Data Changes to Transactional Articles](../../../relational-databases/replication/publish/set-the-propagation-method-for-data-changes-to-transactional-articles.md) (Задание метода распространения изменений данных в транзакционные статьи)  
  
-   [Включение обновляемых подписок для публикации транзакций](../../../relational-databases/replication/publish/enable-updating-subscriptions-for-transactional-publications.md)  
  
-   [Настройка параметров разрешения конфликтов для обновления посредством очередей (среда SQL Server Management Studio)](../../../relational-databases/replication/publish/set-queued-updating-conflict-resolution-options-sql-server-management-studio.md)  
  
-   [Публикация выполнения хранимой процедуры в публикации транзакций (среда SQL Server Management Studio)](../../../relational-databases/replication/publish/publish-execution-of-stored-procedure-in-transactional-publication.md)  
  
## <a name="merge-replication-options"></a>Параметры репликации слиянием  
  
-   [Define a Logical Record Relationship Between Merge Table Articles](../../../relational-databases/replication/publish/define-a-logical-record-relationship-between-merge-table-articles.md) (Определение связи логических записей между статьями таблиц слияния)  
  
-   [Specify the Processing Order of Merge Table Articles](../../../relational-databases/replication/publish/specify-the-processing-order-of-merge-table-articles.md) (Определение порядка обработки для статей таблиц слияния)  
  
-   [Specify That a Merge Table Article is Download-Only](../../../relational-databases/replication/publish/specify-that-a-merge-table-article-is-download-only.md) (Указание того, что статья таблицы публикации слиянием предназначена только для загрузки)  
  
-   [Specify That Deletes Should Not Be Tracked For Merge Articles](../../../relational-databases/replication/publish/specify-that-deletes-should-not-be-tracked-for-merge-articles.md) (Отключение отслеживания операций удаления для статей публикации слиянием)  
  
-   [Specify the Conflict Tracking and Resolution Level for Merge Articles](../../../relational-databases/replication/publish/specify-the-conflict-tracking-and-resolution-level-for-merge-articles.md) (Указание уровня отслеживания и разрешения конфликтов для статей публикации слиянием)  
  
-   [Specify a Merge Article Resolver (Определение сопоставителя статей публикации слиянием)](../../../relational-databases/replication/publish/specify-a-merge-article-resolver.md)  
  
-   [Настройка интерактивного устранения конфликтов для статей публикации слиянием](../../../relational-databases/replication/publish/specify-interactive-conflict-resolution-for-merge-articles.md)  
  
## <a name="see-also"></a>См. также:  
 [Публикация данных и объектов базы данных](../../../relational-databases/replication/publish/publish-data-and-database-objects.md)  
  
  
