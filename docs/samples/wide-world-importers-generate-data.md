---
title: WideWorldImporters создания данных - образца базы данных SQL | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2018
ms.reviewer: ''
ms.prod: sql
ms.prod_service: sql
ms.technology: samples
ms.topic: conceptual
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: b0fd90b553aaefad61d9285f8630650b2b38763d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47810542"
---
# <a name="wideworldimporters-data-generation"></a>Создание данных WideWorldImporters
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
Выпущенные версии баз данных WideWorldImporters и WideWorldImportersDW имеются данные от 1 января 2013 г. до дня, созданных в базе данных.

Если вы используете эти образцы баз данных, вам может потребоваться включить более новый образец данных.

## <a name="data-generation-in-wideworldimporters"></a>Создание данных WideWorldImporters

Чтобы создать демонстрационные данные до текущей даты:

1. Если вы этого еще не сделали, установите чистую версию базы данных WideWorldImporters. Инструкции по установке см. в разделе [установки и настройки](wide-world-importers-oltp-install-configure.md).
2. Выполните следующую инструкцию в базе данных:

    ```
        EXECUTE DataLoadSimulation.PopulateDataToCurrentDate
            @AverageNumberOfCustomerOrdersPerDay = 60,
            @SaturdayPercentageOfNormalWorkDay = 50,
            @SundayPercentageOfNormalWorkDay = 0,
            @IsSilentMode = 1,
            @AreDatesPrinted = 1;
    ```

    Эта инструкция добавляет пример продажи и покупки данных в базу данных до текущей даты. Он отображает ход выполнения создания данных по дням. Создание данных может занять около 10 минут для каждого года, к которой ему требуются данные. Из-за случайного фактора в создания данных существуют некоторые различия в данных, который создается между запусками.

    Чтобы увеличить или уменьшить объем данных, созданный для заказов в день, измените значение параметра `@AverageNumberOfCustomerOrdersPerDay`. Можно использовать параметры `@SaturdayPercentageOfNormalWorkDay` и `@SundayPercentageOfNormalWorkDay` для определения порядка тома для выходных дней.

## <a name="import-generated-data-in-wideworldimportersdw"></a>Данные импорта в WideWorldImportersDW

Чтобы импортировать демонстрационные данные до текущей даты в базе данных WideWorldImportersDW OLAP:

1. Выполните логика создания данных в базе данных WideWorldImporters OLTP, следуя инструкциям, приведенным в предыдущем разделе.
2. Если вы еще не сделали, установите чистую версию базы данных WideWorldImportersDW. Инструкции по установке см. в разделе [установки и настройки](wide-world-importers-oltp-install-configure.md).
3. Повторной установки начальных значений базы данных OLAP, выполнив следующую инструкцию в базе данных:

    ```sql
    EXECUTE [Application].Configuration_ReseedETL
    ```

4. Запустите *ежедневного ETL.ispac* пакета SQL Server Integration Services для импорта данных в базу данных OLAP. Сведения о запуске задания ETL, см. в разделе [рабочий процесс WideWorldImporters ETL](wide-world-importers-perform-etl.md).

## <a name="generate-data-in-wideworldimportersdw-for-performance-testing"></a>Создание данных в WideWorldImportersDW для тестирования производительности

WideWorldImportersDW произвольно можно увеличить размер данных для тестирования производительности. Например его можно увеличить размер данных для использования с индексированием кластеризованный индекс columnstore.

Одной из проблем является небольшой размер загрузки достаточно загрузить легко, но большие достаточно, чтобы продемонстрировать возможности для повышения производительности SQL Server. К примеру только в том случае, при работе с большим количеством строк, достигаются значительные преимущества для индексов columnstore. 

Можно использовать `Application.Configuration_PopulateLargeSaleTable` процедуру, чтобы увеличить количество строк в `Fact.Sale` таблицы. Строки будут вставлены в 2012 календарного года, чтобы избежать конфликтов с существующими данными World Wide Importers, который начинается 1 января 2013 г.

### <a name="procedure-details"></a>Сведения о процедуре

#### <a name="name"></a>Имя

    Application.Configuration_PopulateLargeSaleTable

#### <a name="parameters"></a>Параметры

  `@EstimatedRowsFor2012` **bigint** (значение по умолчанию 12000000)

#### <a name="result"></a>Результат

Приблизительно необходимое количество строк вставляются в `Fact.Sale` таблицу в 2012 года. Процедура искусственно ограничивает количество строк для 50 000 в день. Вы можете изменить это ограничение, но ограничение позволяет избежать случайного overinflations таблицы.

Эта процедура также применима кластеризованный индекс columnstore, индексирования, если он уже не был применен.
