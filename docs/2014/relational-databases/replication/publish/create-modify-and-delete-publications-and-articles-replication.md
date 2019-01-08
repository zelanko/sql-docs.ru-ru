---
title: Создание, изменение и удаление публикаций и статей (репликация) | Документация Майкрософт
ms.custom: ''
ms.date: 06/30/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- publications [SQL Server replication], creating
- articles [SQL Server replication], defining
ms.assetid: e66d06ec-a12b-444d-875b-77f958af2f21
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 3849273ee37db2780e53d28933ad7f1ffd89f056
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2018
ms.locfileid: "52794436"
---
# <a name="create-modify-and-delete-publications-and-articles-replication"></a>Создание, изменение и удаление публикаций и статей (репликация)
  Этот раздел документации содержит сведения о процедурах для задач, связанных с созданием публикаций и определением статей.  
  
## <a name="in-this-section"></a>в этом разделе  
  
-   [Create a Publication](create-a-publication.md)  
  
-   [Определение статьи](define-an-article.md)  
  
-   [Просмотр и изменение свойств публикации](view-and-modify-publication-properties.md)  
  
-   [View and Modify Article Properties (Просмотр и изменение свойств статьи)](view-and-modify-article-properties.md)  
  
-   [Delete a Publication (Удаление публикации)](delete-a-publication.md)  
  
-   [Delete an Article (Удаление статьи)](delete-an-article.md)  
  
-   [Создание публикации из базы данных Oracle](create-a-publication-from-an-oracle-database.md)  
  
-   [Set the Expiration Period for Subscriptions](set-the-expiration-period-for-subscriptions.md) (Установка срока действия подписок)  
  
-   [Specify Schema Options (Указание параметров схемы)](specify-schema-options.md)  
  
-   [Replicate Schema Changes (Репликация изменений схемы)](replicate-schema-changes.md)  
  
-   [Manage Identity Columns (Управление столбцами идентификаторов)](manage-identity-columns.md)  
  
-   [Set the Compatibility Level for Merge Publications](set-the-compatibility-level-for-merge-publications.md) (Задание уровня совместимости для публикаций слиянием)  
  
## <a name="snapshot-options"></a>Параметры моментального снимка  
  
-   [Указание формата моментальных снимков (среда SQL Server Management Studio)](specify-snapshot-format-sql-server-management-studio.md)  
  
-   [Изменение местоположения папки моментальных снимков (среда SQL Server Management Studio)](specify-an-alternate-snapshot-folder-location-sql-server-management-studio.md)  
  
-   [Сжатие файлов моментальных снимков (среда SQL Server Management Studio)](compress-snapshot-files-sql-server-management-studio.md)  
  
-   [Настройка свойств моментального снимка (программирование репликации на языке Transact-SQL)](configure-snapshot-properties-replication-transact-sql-programming.md)  
  
-   [Выполнение скриптов до и после применения моментального снимка (SQL Server Management Studio)](../execute-scripts-before-and-after-a-snapshot-is-applied.md)  
  
-   [Доставка моментального снимка через FTP](deliver-a-snapshot-through-ftp.md)  
  
## <a name="filtering-data"></a>Фильтрация данных  
  
-   [Define and Modify a Column Filter](define-and-modify-a-column-filter.md) (Определение или изменение фильтра столбцов)  
  
-   [Определение и изменение статического строкового фильтра](define-and-modify-a-static-row-filter.md)  
  
-   [Define and Modify a Parameterized Row Filter for a Merge Article](define-and-modify-a-parameterized-row-filter-for-a-merge-article.md)  
  
-   [Optimize Parameterized Row Filters (Оптимизация параметризованных фильтров строк)](../merge/parameterized-filters-parameterized-row-filters.md)  
  
-   [Определение и изменение фильтра соединения между статьями публикации слиянием](define-and-modify-a-join-filter-between-merge-articles.md)  
  
-   [Автоматическое формирование набора фильтров соединения между статьями публикации слиянием (среда SQL Server Management Studio)](automatically-generate-join-filters-between-merge-articles.md)  
  
## <a name="transactional-replication-options"></a>Параметры репликации транзакций  
  
-   [Set the Propagation Method for Data Changes to Transactional Articles](set-the-propagation-method-for-data-changes-to-transactional-articles.md) (Задание метода распространения изменений данных в транзакционные статьи)  
  
-   [Включение обновляемых подписок для публикации транзакций](enable-updating-subscriptions-for-transactional-publications.md)  
  
-   [Настройка параметров разрешения конфликтов для обновления посредством очередей (среда SQL Server Management Studio)](set-queued-updating-conflict-resolution-options-sql-server-management-studio.md)  
  
-   [Публикация выполнения хранимой процедуры в публикации транзакций (среда SQL Server Management Studio)](publish-execution-of-stored-procedure-in-transactional-publication.md)  
  
## <a name="merge-replication-options"></a>Параметры репликации слиянием  
  
-   [Define a Logical Record Relationship Between Merge Table Articles](define-a-logical-record-relationship-between-merge-table-articles.md) (Определение связи логических записей между статьями таблиц слияния)  
  
-   [Specify the Processing Order of Merge Table Articles](specify-the-processing-order-of-merge-table-articles.md) (Определение порядка обработки для статей таблиц слияния)  
  
-   [Specify That a Merge Table Article is Download-Only](specify-that-a-merge-table-article-is-download-only.md) (Указание того, что статья таблицы публикации слиянием предназначена только для загрузки)  
  
-   [Specify That Deletes Should Not Be Tracked For Merge Articles](specify-that-deletes-should-not-be-tracked-for-merge-articles.md) (Отключение отслеживания операций удаления для статей публикации слиянием)  
  
-   [Specify the Conflict Tracking and Resolution Level for Merge Articles](specify-the-conflict-tracking-and-resolution-level-for-merge-articles.md) (Указание уровня отслеживания и разрешения конфликтов для статей публикации слиянием)  
  
-   [Specify a Merge Article Resolver (Определение сопоставителя статей публикации слиянием)](specify-a-merge-article-resolver.md)  
  
-   [Настройка интерактивного устранения конфликтов для статей публикации слиянием](specify-interactive-conflict-resolution-for-merge-articles.md)  
  
## <a name="see-also"></a>См. также  
 [Публикация данных и объектов базы данных](publish-data-and-database-objects.md)  
  
  
