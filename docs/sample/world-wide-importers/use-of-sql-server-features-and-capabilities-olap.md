---
title: Использование SQL Server функций и возможностей | Документы Microsoft
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: ''
ms.component: samples
ms.technology:
- samples
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7cbfb4ef-1e61-4e65-9fe0-ed5adfb43415
caps.latest.revision: 3
author: BarbKess
ms.author: barbkess
manager: craigg
robots: noindex,nofollow
ms.workload: Inactive
ms.openlocfilehash: 4688b3ebaf7f25bf37fb471c698d287f1e9792ed
ms.sourcegitcommit: 094c46e7fa6de44735ed0040c65a40ec3d951b75
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/07/2018
---
# <a name="wideworldimportersdw-use-of-sql-server-features-and-capabilities"></a>Использование WideWorldImportersDW компонентов SQL Server и возможности
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
WideWorldImportersDW предназначен для демонстрации многие ключевые функции SQL Server, которые подходят для хранения данных и аналитики. Ниже приведен список компонентов SQL Server и возможности и как они используются в WideWorldImportersDW описание.

## <a name="polybase"></a>PolyBase

[Применяется к SQL Server (2016 и более поздние версии)]

PolyBase позволяет объединять сведения о продажах из WideWorldImportersDW с открытый набор данных о демографические данные, чтобы понять, какие города может представлять интерес для дальнейшее расширение продаж.

Чтобы включить использование PolyBase в образце базы данных, убедитесь, что она установлена и выполните следующую хранимую процедуру в базе данных:

    EXEC [Application].[Configuration_ApplyPolybase]

Это создаст внешней таблицы `dbo.CityPopulationStatistics` , ссылается на открытый набор данных, содержащий данные для тех городов, в Соединенных Штатах, размещенные в хранилище больших двоичных объектов. Вы, рекомендуется просмотреть код в хранимую процедуру, чтобы понять процесс настройки. Если вы хотите разместить свои собственные данные в хранилище больших двоичных объектов и защиты от общие общего доступа, необходимо предпринять дополнительные действия по настройке. Следующий запрос возвращает данные из внешнего набора данных:

    SELECT CityID, StateProvinceCode, CityName, YearNumber, LatestRecordedPopulation FROM dbo.CityPopulationStatistics;

Чтобы понять, какие города может представлять интерес для дальнейшее расширение, следующий запрос просматривает темп роста городов и возвращает первые 100 крупнейших городов мира значительное увеличение размера, и где Wide World Importers отсутствуют продажи присутствия. Запрос связан с соединением между удаленной таблицы `dbo.CityPopulationStatistics` и локальной таблицы `Dimension.City`и фильтр с использованием локальной таблицы `Fact.Sales`.

    WITH PotentialCities
    AS
    (
        SELECT cps.CityName,
               cps.StateProvinceCode,
               MAX(cps.LatestRecordedPopulation) AS PopulationIn2016,
               (MAX(cps.LatestRecordedPopulation) - MIN(cps.LatestRecordedPopulation)) * 100.0
                   / MIN(cps.LatestRecordedPopulation) AS GrowthRate
        FROM dbo.CityPopulationStatistics AS cps
        WHERE cps.LatestRecordedPopulation IS NOT NULL
        AND cps.LatestRecordedPopulation <> 0
        GROUP BY cps.CityName, cps.StateProvinceCode
    ),
    InterestingCities
    AS
    (
        SELECT DISTINCT pc.CityName,
                        pc.StateProvinceCode,
                        pc.PopulationIn2016,
                        FLOOR(pc.GrowthRate) AS GrowthRate
        FROM PotentialCities AS pc
        INNER JOIN Dimension.City AS c
        ON pc.CityName = c.City
        WHERE GrowthRate > 2.0
        AND NOT EXISTS (SELECT 1 FROM Fact.Sale AS s WHERE s.[City Key] = c.[City Key])
    )
    SELECT TOP(100) CityName, StateProvinceCode, PopulationIn2016, GrowthRate
    FROM InterestingCities
    ORDER BY PopulationIn2016 DESC;

## <a name="clustered-columnstore-indexes"></a>Кластеризованные индексы columnstore

(Полная версия образца)

Кластеризованные индексы Columnstore (CCI) используются в таблицах фактов сокращает занимаемое место в хранилище и повысить производительность запросов. С помощью CCI базового хранилища для таблиц фактов использует сжатие столбцов.

Некластеризованные индексы используются поверх кластеризованный индекс, для упрощения первичный ключ и ограничения внешнего ключа. Эти ограничения были добавлены из очень осторожны — процесс ETL источники данных из базы данных WideWorldImporters, имеющей ограничения, обеспечивающие целостность. Удаление ограничения первичного и внешнего ключа и их вспомогательные индексов будет уменьшить занимаемое место хранения таблиц фактов.

**Размер данных**

Образец базы данных имеет ограниченный размер данных, чтобы упростить процесс загрузки и установки образца. Тем не менее чтобы преимущества фактической производительности индексов columnstore, может потребоваться использовать более крупных наборов данных.

Можно выполнить следующую инструкцию, чтобы увеличить размер `Fact.Sales` таблицы путем вставки другой 12 миллионов строк данных выборки. Эти строки все вставляются год 2012 г. таким образом, чтобы исключить конфликты с процессом ETL.

    EXECUTE [Application].[Configuration_PopulateLargeSaleTable]

Для выполнения этой инструкции займет около 5 минут. Чтобы вставить более 12 миллионов строк, передайте требуемое число строк, вставляемых в качестве параметра для этой хранимой процедуры.

Чтобы сравнить производительность запросов с и без columnstore, можно удалить и повторно создать кластеризованный индекс.

Чтобы удалить индекс:

    DROP INDEX [CCX_Fact_Order] ON [Fact].[Order]

Для повторного создания:

    CREATE CLUSTERED COLUMNSTORE INDEX [CCX_Fact_Order] ON [Fact].[Order]

## <a name="partitioning"></a>Секционирование

(Полная версия образца)

Размер данных в хранилище данных может стать очень большим. Поэтому рекомендуется использовать секционирование для управления хранилищами больших таблиц в базе данных.

Все таблицы фактов большего секционируются по годам. Единственным исключением является `Fact.Stock Holdings`, который не на основе даты и имеет ограниченный объем по сравнению с другими таблицами фактов.

Функции секционирования, используемого для всех секционированных таблиц — `PF_Date`, и схему секционирования, используемый `PS_Date`.

## <a name="in-memory-oltp"></a>In-Memory OLTP

(Полная версия образца)

WideWorldImportersDW использует оптимизированных для памяти таблиц SCHEMA_ONLY для промежуточных таблиц. Все `Integration.` * `_Staging` таблиц, оптимизированных для памяти таблиц SCHEMA_ONLY.

Преимущество таблицы SCHEMA_ONLY — они не регистрируются и не требуют любой доступ к диску. Это повышает производительность процесса ETL. Так как эти таблицы не регистрируются, их содержимое будут потеряны, если происходит сбой. Тем не менее источник данных доступен, поэтому просто можно перезапустить процесс ETL, если происходит сбой.
