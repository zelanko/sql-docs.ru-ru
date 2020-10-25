---
title: Создание данных в примерах SQL WideWorldImporters
description: Используйте эти инструкции SQL для создания и импорта демонстрационных данных до текущей даты для образцов баз данных WideWorldImporters.
ms.date: 10/23/2020
ms.reviewer: ''
ms.prod: sql
ms.prod_service: sql
ms.technology: samples
ms.topic: conceptual
author: MashaMSFT
ms.author: mathoma
ms.custom: seo-lt-2019
ms.openlocfilehash: f60ad250ea68f58a98fb93da9f3c5853ad68bd47
ms.sourcegitcommit: 67befbf7435f256e766bbce6c1de57799e1db9ad
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/24/2020
ms.locfileid: "92523939"
---
# <a name="wideworldimporters-data-generation"></a>Создание данных WideWorldImporters
[!INCLUDE [SQL Server Azure SQL Database](../includes/applies-to-version/sql-asdb.md)]
Выпущенные версии баз данных WideWorldImporters и WideWorldImportersDW содержат данные с 1 января 2013 до дня создания баз данных.

При использовании этих образцов баз данных может потребоваться включить более свежие образцы данных.

## <a name="data-generation-in-wideworldimporters"></a>Создание данных в WideWorldImporters

Создание образца данных до текущей даты:

1. Если это еще не сделано, установите чистую версию базы данных WideWorldImporters. Инструкции по установке см. в разделе [Установка и настройка](wide-world-importers-oltp-install-configure.md).
2. Выполните следующую инструкцию в базе данных:

    ```
        EXECUTE DataLoadSimulation.PopulateDataToCurrentDate
            @AverageNumberOfCustomerOrdersPerDay = 60,
            @SaturdayPercentageOfNormalWorkDay = 50,
            @SundayPercentageOfNormalWorkDay = 0,
            @IsSilentMode = 1,
            @AreDatesPrinted = 1;
    ```

    Эта инструкция добавляет пример данных о продажах и покупках в базу данных вплоть до текущей даты. В нем отображается ход создания данных по дням. Из-за случайного коэффициента в создании данных существуют некоторые различия в данных, создаваемых между запусками.

    Чтобы увеличить или уменьшить объем данных, создаваемых для заказов в день, измените значение параметра `@AverageNumberOfCustomerOrdersPerDay` . Используйте параметры `@SaturdayPercentageOfNormalWorkDay` и, `@SundayPercentageOfNormalWorkDay` чтобы определить объем заказа для выходных дней.

> [!TIP]
> Принудительное применение [отложенной устойчивости](../relational-databases/logs/control-transaction-durability.md) к базе данных может повысить скорость создания данных, особенно если журнал транзакций базы данных находится в подсистеме хранения с высокой задержкой. Учитывайте потенциальные последствия [потери данных](../relational-databases/logs/control-transaction-durability.md#bkmk_DataLoss) при использовании отложенной устойчивости и рассмотрите возможность включения отложенной устойчивости на время создания данных.

## <a name="import-generated-data-in-wideworldimportersdw"></a>Импорт созданных данных в WideWorldImportersDW

Чтобы импортировать образец данных вплоть до текущей даты в базе данных WideWorldImportersDW OLAP, выполните следующие действия.

1. Выполните логику создания данных в базе данных OLTP WideWorldImporters, выполнив действия, описанные в предыдущем разделе.
2. Если вы еще не сделали этого, установите чистую версию базы данных WideWorldImportersDW. Инструкции по установке см. в разделе [Установка и настройка](wide-world-importers-oltp-install-configure.md).
3. Выполните повторное заполнение базы данных OLAP, выполнив следующую инструкцию в базе данных:

    ```sql
    EXECUTE [Application].Configuration_ReseedETL
    ```

4. Запустите пакет SQL Server Integration Services *ежедневного ETL. ISPAC* , чтобы импортировать данные в базу данных OLAP. Чтобы узнать, как запустить задание ETL, см. раздел [WIDEWORLDIMPORTERS ETL Workflow](wide-world-importers-perform-etl.md).

## <a name="generate-data-in-wideworldimportersdw-for-performance-testing"></a>Создание данных в WideWorldImportersDW для тестирования производительности

WideWorldImportersDW может произвольно увеличить размер данных для тестирования производительности. Например, он может увеличить размер данных для использования с кластеризованным индексированием columnstore.

Одна из проблем заключается в том, чтобы размер загружаемого файла был достаточно мал для легкого скачивания, но достаточно велик, чтобы продемонстрировать SQL Server функции производительности. Например, значительные преимущества для индексов columnstore достигаются только при работе с большим количеством строк. 

`Application.Configuration_PopulateLargeSaleTable`Для увеличения количества строк в таблице можно использовать процедуру `Fact.Sale` . Строки вставляются в 2012 календарного года, чтобы избежать конфликта с существующими данными в мире импорта, которые начинаются с 1 января 2013.

### <a name="procedure-details"></a>Сведения о процедуре

#### <a name="name"></a>Имя

`Application.Configuration_PopulateLargeSaleTable`

#### <a name="parameters"></a>Параметры

`@EstimatedRowsFor2012`**bigint** (со значением по умолчанию 12000000)

#### <a name="result"></a>Результат

Приблизительное требуемое число строк вставляется в `Fact.Sale` таблицу в 2012 году. Процедура искусственно ограничивает число строк до 50 000 в день. Это ограничение можно изменить, но ограничение помогает избежать случайного перероста таблицы.

Процедура также применяет кластеризованное индексирование columnstore, если оно еще не применено.
