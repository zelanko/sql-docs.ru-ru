---
description: Возможности и ограничения PolyBase
title: Возможности и ограничения PolyBase | Документация Майкрософт
descriptions: This article summarizes PolyBase features available for SQL Server products and services. It lists T-SQL operators supported for pushdown and known limitations.
ms.date: 11/13/2020
ms.prod: sql
ms.technology: polybase
ms.topic: conceptual
ms.assetid: 6591994d-6109-4285-9c5b-ecb355f8a111
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: ''
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 2afdc0e62fdd725584c464bda516fc6284d20f01
ms.sourcegitcommit: 3bd188e652102f3703812af53ba877cce94b44a9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/15/2020
ms.locfileid: "97489994"
---
# <a name="polybase-features-and-limitations"></a>Возможности и ограничения PolyBase

[!INCLUDE[appliesto-ss2016-asdb-asdw-pdw-md](../../includes/tsql-appliesto-ss2016-all-md.md)]

В этой статье приведена сводка функций PolyBase, доступных для продуктов и служб SQL Server.  
  
## <a name="feature-summary-for-product-releases"></a>Сводка функций по выпускам продукта

В следующей таблице перечислены основные функции PolyBase и продукты, в которых они доступны.  

|**Компонент** |**SQL Server** (начиная с версии 2016) |**База данных SQL Azure** |**Azure Synapse Analytics** |**Параллельное хранилище данных** |
|---------|---------|---------|---------|---------|
|Запрос данных Hadoop с помощью [!INCLUDE[tsql](../../includes/tsql-md.md)]|Да|нет|Нет|Да|
|Импорт данных из Hadoop|Да|нет|Нет|Да|
|Экспорт данных в Hadoop  |Да|нет|Нет| Да|
|Запрос, импорт и экспорт данных в Azure HDInsight |нет|нет|нет|нет
|Отправка результатов вычислений запросов в Hadoop|Да|нет|Нет|Да|  
|Импорт данных из хранилища BLOB-объектов Azure|Да|Да<sup>*</sup>|Да|Да|
|Экспорт данных в хранилище BLOB-объектов Azure|Да|Нет|Да|Да|  
|Импорт данных из хранилища Azure Data Lake Store|нет|Нет|Да|нет|
|Экспорт данных в хранилище Azure Data Lake Store|нет|Нет|Да|нет|
|Выполнение запросов PolyBase из средств бизнес-аналитики Майкрософт|Да|Нет|Да|Да|

<sup>*</sup> Появилось в SQL Server 2017; см. статью [Примеры массового доступа к данным в хранилище BLOB-объектов Azure](../import-export/examples-of-bulk-access-to-data-in-azure-blob-storage.md).


## <a name="pushdown-computation-supported-by-t-sql-operators"></a>Поддержка передачи вычислений в операторах T-SQL

В SQL Server и APS лишь некоторые операторы T-SQL поддерживают передачу в кластер Hadoop. В следующей таблице приведены все поддерживаемые операторы и ряд неподдерживаемых.

|**Тип оператора** |**Отправка в Hadoop** |**Отправка в хранилище BLOB-объектов** |
|---------|---------|---------|
|Проекции столбцов|Да|нет|
|Предикаты|Да|Нет|
|Статистические выражения|Частично|нет|
|Соединения между внешними таблицами|нет|нет|
|Соединения между внешними и локальными таблицами|нет|нет|
|Сортировки|нет|нет|

Частичное статистическое вычисление означает, что итоговое вычисление должно выполняться после получения данных в SQL Server. Однако часть статистического вычисления происходит в Hadoop. Это стандартный метод вычисления статистических выражений в системах обработки данных с массовым параллелизмом.  

## <a name="known-limitations"></a>Известные ограничения

PolyBase имеет следующие ограничения.

- Чтобы использовать PolyBase, необходимо иметь роль системного администратора или разрешения на управление сервером базы данных.

- Максимальный размер строки, включая полную длину столбцов переменной длины, не может превышать 32 КБ в SQL Server или 1 МБ в Azure Synapse Analytics.

- При экспорте данных в файл формата ORC из SQL Server или Azure Synapse Analytics число столбцов с большим количеством текста может быть ограничено. Их число может даже не превышать 50, что связано с сообщениями об ошибках нехватки памяти Java. Чтобы обойти эту проблему, экспортируйте подмножество столбцов.

- PolyBase не может подключиться к экземпляру Hortonworks, если включена поддержка Knox.

- Если вы используете таблицы Hive с параметром transactional = true, то PolyBase не может обратиться к данным в каталоге таблицы Hive.

<!--SQL Server 2016-->
::: moniker range="= sql-server-2016 "

- [PolyBase не устанавливается при добавлении узла в отказоустойчивый кластер SQL Server 2016](https://support.microsoft.com/help/3173087/fix-polybase-feature-doesn-t-install-when-you-add-a-node-to-a-sql-server-2016-failover-cluster).

::: moniker-end

## <a name="next-steps"></a>Дальнейшие действия

Дополнительные сведения о PolyBase см. в [этом руководстве](polybase-guide.md).
