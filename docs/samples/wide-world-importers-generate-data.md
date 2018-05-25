---
title: WideWorldImporters создания данных - образца базы данных SQL | Документы Microsoft
ms.custom: ''
ms.date: 04/04/2018
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.prod: sql
ms.prod_service: sql
ms.technology: samples
ms.topic: conceptual
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 6ace1f771ef3a77a6f7db0072442affe181d7872
ms.sourcegitcommit: 7019ac41524bdf783ea2c129c17b54581951b515
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2018
---
# <a name="wideworldimporters-data-generation"></a>Создание данных WideWorldImporters
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
Выпущенные версии базы данных WideWorldImporters и WideWorldImportersDW имеются данные от 1 января 2013 г. до дня, созданных в базах данных.

При использовании эти образцы баз данных, может потребоваться включить более новые образцы данных.

## <a name="data-generation-in-wideworldimporters"></a>Создание данных в WideWorldImporters

Чтобы создать демонстрационные данные до текущей даты:

1. Если это не сделано, установите версию очистки базы данных WideWorldImporters. Инструкции по установке см. в разделе [установку и настройку](wide-world-importers-oltp-install-configure.md).
2. Выполните следующую инструкцию в базе данных:

    ```
        EXECUTE DataLoadSimulation.PopulateDataToCurrentDate
            @AverageNumberOfCustomerOrdersPerDay = 60,
            @SaturdayPercentageOfNormalWorkDay = 50,
            @SundayPercentageOfNormalWorkDay = 0,
            @IsSilentMode = 1,
            @AreDatesPrinted = 1;
    ```

    Эта инструкция добавляет образец продажи и покупки данные в базу данных до текущей даты. Отображается ход выполнения создания данных по дням. Создание данных может занять около 10 минут для каждого года, требуются данные. Из-за фактор случайного создания данных существуют некоторые различия в данных, который создается между запусками.

    Чтобы увеличить или уменьшить объем данных, созданных для заказов в день, измените значение параметра `@AverageNumberOfCustomerOrdersPerDay`. Используйте параметры `@SaturdayPercentageOfNormalWorkDay` и `@SundayPercentageOfNormalWorkDay` для определения порядка тома для выходных дней.

## <a name="import-generated-data-in-wideworldimportersdw"></a>Созданный импорта данных в WideWorldImportersDW

Чтобы импортировать образец данных до текущей даты в базе данных WideWorldImportersDW OLAP:

1. Выполнение логики формирования данных в базе данных WideWorldImporters OLTP, следуя инструкциям, приведенным в предыдущем разделе.
2. Если это еще не было сделано, установите версию чистой WideWorldImportersDW базы данных. Инструкции по установке см. в разделе [установку и настройку](wide-world-importers-oltp-install-configure.md).
3. Повторно задать базу данных OLAP, выполнив следующую инструкцию в базе данных:

    ```sql
    EXECUTE [Application].Configuration_ReseedETL
    ```

4. Запустите *ежедневно ETL.ispac* пакета SQL Server Integration Services для импорта данных в базу данных OLAP. Чтобы узнать, как для выполнения задания ETL, см. [рабочего процесса WideWorldImporters ETL](wide-world-importers-perform-etl.md).

## <a name="generate-data-in-wideworldimportersdw-for-performance-testing"></a>Создать данные в WideWorldImportersDW для тестирования производительности

WideWorldImportersDW произвольно можно увеличить размер файла данных для тестирования производительности. Например его можно увеличить размер данных для использования с индексированием кластеризованный индекс columnstore.

Одна из сложностей является сохранение объем загружаемых данных достаточно мал, чтобы загрузить легко, но большой достаточно для демонстрации возможностей производительности SQL Server. Например значительные преимущества для индексов columnstore достигается только при работе с большим количеством строк. 

Можно использовать `Application.Configuration_PopulateLargeSaleTable` процедуру, чтобы увеличить число строк в `Fact.Sale` таблицы. Строки вставлены в календарном году 2012 во избежание несовместимости с существующими данными World Wide Importers, который начинается 1 января 2013 г.

### <a name="procedure-details"></a>Сведения о процедуре

#### <a name="name"></a>Название

    Application.Configuration_PopulateLargeSaleTable

#### <a name="parameters"></a>Параметры

  `@EstimatedRowsFor2012` **bigint** (значение по умолчанию 12000000)

#### <a name="result"></a>Результат

Приблизительно необходимое количество строк вставляются в `Fact.Sale` таблицу в 2012 году. Процедура искусственно ограничивает количество строк для 50 000 в день. Вы можете изменить это ограничение, но ограничение помогает избежать случайного overinflations таблицы.

Процедура также применима кластеризованном индексирования, если он уже не был применен.
