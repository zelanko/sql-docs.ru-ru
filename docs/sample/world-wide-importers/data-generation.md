---
title: "Создание данных | Документы Microsoft"
ms.custom: 
ms.date: 01/30/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.prod: sql-non-specified
ms.technology:
- " database-engine "
ms.topic: article
ms.assetid: f387273b-8b5f-4687-b033-09499ea2d68f
caps.latest.revision: 4
author: BarbKess
ms.author: barbkess
manager: jhubbard
robots: noindex,nofollow
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: c17ad40220d46ab6e19054818ce2abfdce7251f4
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="wideworldimporters-data-generation"></a>Создание данных WideWorldImporters
Выпущенные версии базы данных WideWorldImporters и WideWorldImportersDW содержит данные, начиная с 1-го января 2013, вплоть до в день создания этих баз данных.

Если впоследствии в целях демонстрации или рисунке используются образцы баз данных может быть полезно включить более новые образцы данных в базе данных.

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

Эта инструкция добавляет образец продажи и покупки данные в базе данных до текущей даты. Он выводит ход выполнения данных поколения день. Rougly может занять 10 минут для каждого года, требуются данные. Обратите внимание, что некоторые отличия в формируемые между запусками, так как нет случайного фактора поколения данных.

Чтобы увеличить или уменьшить объем данных, созданных с точки зрения заказов для каждого дня, измените значение параметра `@AverageNumberOfCustomerOrdersPerDay`. Параметры `@SaturdayPercentageOfNormalWorkDay` и `@SundayPercentageOfNormalWorkDay` используются для определения порядка тома для выходных дней.

## <a name="importing-generated-data-in-wideworldimportersdw"></a>Импорт данных, созданный в WideWorldImportersDW

Чтобы импортировать образец данных до текущей даты в базе данных OLAP WideWorldImportersDW, выполните следующие действия.

1. Логика создания данных выполняются в базе данных WideWorldImporters OLTP, используя описанные выше шаги.
2. Если еще не сделано, установите версию чистой WideWorldImportersDW базы данных. Инструкции по установке **WideWorldImporters установку и настройку**.
3. Повторно задать базу данных OLAP, выполнив следующую инструкцию в базе данных:

```
    EXECUTE [Application].Configuration_ReseedETL
```

4. Запустить пакет служб SSIS **ежедневно ETL.ispac** для импорта данных в базу данных OLAP. Инструкции по запуску задания ETL см. в разделе **рабочего процесса ETL WideWorldImporters**.

## <a name="generating-data-in-wideworldimportersdw-for-performance-testing"></a>Создание данных в WideWorldImportersDW для тестирования производительности

WideWorldImportersDW имеет возможность произвольным образом увеличить размер данных, с целью тестирования, например с кластеризованном производительности.

Одна из сложностей при отправке образца как World Wide Importers является сохранение объем загружаемых данных недостаточно мал для распространяемого, но достаточно велик, чтобы иметь возможность демонстрации возможностей производительности SQL Server. Сферами, где это определенный запрос — при работе с индексами columnstore. Значительные преимущества поставляются только при работе с большим количеством строк. 

Процедура `Application.Configuration_PopulateLargeSaleTable` позволяет значительно увеличить число строк в `Fact.Sale` таблицы. Обратите внимание, что строки вставляются в календарном году 2012 г. Чтобы избежать несовместимости с существующими данными World Wide Importers, начиная с 1-го января 2013.

### <a name="procedure-details"></a>Сведения о процедуре

#### <a name="name"></a>Имя: 

    Application.Configuration_PopulateLargeSaleTable

#### <a name="parameters"></a>Параметры:

  `@EstimatedRowsFor2012`**bigint** (значение по умолчанию 12000000)

#### <a name="result"></a>Результат:

Приблизительно необходимое количество строк вставляются в `Fact.Sale` таблицу в 2012 году. Процедура искусственно ограничивает количество строк в день 50000. Это может быть изменен, но позволяет избежать accidential overinflations таблицы.

Кроме того, процедура применяется кластеризованном индексирования, если он уже не применены.
