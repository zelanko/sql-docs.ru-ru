---
title: WideWorldImporters создания данных - образца базы данных SQL | Документы Microsoft
ms.custom: ''
ms.date: 04/04/2018
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: ''
ms.component: samples
ms.technology:
- " database-engine "
ms.topic: article
author: BarbKess
ms.author: barbkess
manager: craigg
robots: noindex,nofollow
ms.workload: Inactive
ms.openlocfilehash: d99cdfacbe08cd3b81fb46bb61b49cab290780f4
ms.sourcegitcommit: d6b1695c8cbc70279b7d85ec4dfb66a4271cdb10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2018
---
# <a name="wideworldimporters-data-generation"></a>Создание данных WideWorldImporters
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
Выпущенные версии базы данных WideWorldImporters и WideWorldImportersDW содержит данные, начиная с 1 января 2013, вплоть до в день создания этих баз данных.

При использовании образцов баз данных, может быть полезно включить более новые образцы данных.

## <a name="data-generation-in-wideworldimporters"></a>Создание данных в WideWorldImporters

Чтобы создать демонстрационные данные до текущей даты, выполните следующие действия.

1. Если еще не сделано, установите версию очистки базы данных WideWorldImporters. Инструкции по установке **WideWorldImporters установку и настройку**.
2. Выполните следующую инструкцию в базе данных:

```
    EXECUTE DataLoadSimulation.PopulateDataToCurrentDate
        @AverageNumberOfCustomerOrdersPerDay = 60,
        @SaturdayPercentageOfNormalWorkDay = 50,
        @SundayPercentageOfNormalWorkDay = 0,
        @IsSilentMode = 1,
        @AreDatesPrinted = 1;
```

Эта инструкция добавляет образец продажи и покупки данные в базе данных до текущей даты. Он выводит ход выполнения данных поколения день. Занимает около 10 минут для каждого года, требуются данные. Существуют некоторые отличия в формируемые между запусками, так как нет случайного фактора поколения данных.

Чтобы увеличить или уменьшить объем данных, созданных с точки зрения заказов для каждого дня, измените значение параметра `@AverageNumberOfCustomerOrdersPerDay`. Параметры `@SaturdayPercentageOfNormalWorkDay` и `@SundayPercentageOfNormalWorkDay` используются для определения порядка тома для выходных дней.

## <a name="importing-generated-data-in-wideworldimportersdw"></a>Импорт данных, созданный в WideWorldImportersDW

Чтобы импортировать образец данных до текущей даты в базе данных OLAP WideWorldImportersDW, выполните следующие действия.

1. Логика создания данных выполняются в базе данных WideWorldImporters OLTP, используя описанные выше шаги.
2. Если еще не сделано, установите версию чистой WideWorldImportersDW базы данных. Инструкции по установке **WideWorldImporters установку и настройку**.
3. Повторно задать базу данных OLAP, выполнив следующую инструкцию в базе данных:

    ```sql
    EXECUTE [Application].Configuration_ReseedETL
    ```

4. Запустить пакет служб SSIS **ежедневно ETL.ispac** для импорта данных в базу данных OLAP. Инструкции по запуску задания ETL см. в разделе **рабочего процесса ETL WideWorldImporters**.

## <a name="generating-data-in-wideworldimportersdw-for-performance-testing"></a>Создание данных в WideWorldImportersDW для тестирования производительности

WideWorldImportersDW имеет возможность произвольным образом увеличить размер данных, с целью тестирования, например с кластеризованном производительности.

Одна из сложностей является сохранение объем загружаемых данных достаточно мал, чтобы загрузить легко, но большой достаточно для демонстрации возможностей производительности SQL Server. Например значительные преимущества для индексов columnstore происходить только при работе с большим количеством строк. 

Процедура `Application.Configuration_PopulateLargeSaleTable` позволяет значительно увеличить число строк в `Fact.Sale` таблицы. Обратите внимание, что строки вставляются в календарном году 2012, чтобы избежать несовместимости с существующими данными World Wide Importers, начиная с 1 января 2013.

### <a name="procedure-details"></a>Сведения о процедуре

#### <a name="name"></a>Имя: 

    Application.Configuration_PopulateLargeSaleTable

#### <a name="parameters"></a>Параметры:

  `@EstimatedRowsFor2012` **bigint** (значение по умолчанию 12000000)

#### <a name="result"></a>Результат:

Приблизительно необходимое количество строк вставляются в `Fact.Sale` таблицу в 2012 году. Процедура искусственно ограничивает количество строк в день 50000. Это ограничение может быть изменен, но существует во избежание случайного overinflations таблицы.

Кроме того, процедура применяется кластеризованном индексирования, если он уже не применены.
