---
title: База данных WideWorldImporters OLAP — использование SQL Server | Документация Майкрософт
ms.prod: sql
ms.prod_service: sql
ms.technology: samples
ms.custom: ''
ms.date: 08/04/2018
ms.reviewer: ''
ms.topic: conceptual
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: '>=sql-server-2016||>=sql-server-linux-2017||=azure-sqldw-latest||>=aps-pdw-2016||=sqlallproducts-allversions||=azuresqldb-mi-current'
ms.openlocfilehash: 57936009880849b3ca1e566110e688b699f6835b
ms.sourcegitcommit: a2be75158491535c9a59583c51890e3457dc75d6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/07/2018
ms.locfileid: "51269738"
---
# <a name="wideworldimportersdw-use-of-sql-server-features-and-capabilities"></a>Использование функции SQL Server и возможности WideWorldImportersDW
[!INCLUDE[appliesto-ss-xxxx-asdw-pdw-md](../includes/appliesto-ss-xxxx-asdw-pdw-md.md)]
WideWorldImportersDW разработано для демонстрации многие из ключевых особенностей SQL Server, которые подходят для хранения данных и аналитики. Ниже приведен список компонентов SQL Server и возможности и описание их использования в WideWorldImportersDW.

## <a name="polybase"></a>PolyBase

[Применимо к SQL Server (2016 и более поздние версии)]

PolyBase используется для объединения сведения о продажах из WideWorldImportersDW с общедоступного набора данных о демографические данные, чтобы понять, какие городов может представлять интерес для дальнейшее расширение продаж.

Чтобы включить использование PolyBase в образце базы данных, убедитесь, что он установлен и выполните следующую хранимую процедуру в базе данных:

    EXEC [Application].[Configuration_ApplyPolyBase]

Это создаст внешнюю таблицу `dbo.CityPopulationStatistics` , ссылающийся на открытый набор данных, содержащий данные о населении для городов в Соединенных Штатах, размещенных в хранилище больших двоичных объектов. Вы, рекомендуется проверить код в хранимую процедуру, чтобы понять процесс настройки. Если вы хотите разместить данные в хранилище больших двоичных объектов и защиту от общий доступ, необходимо предпринять дополнительные действия по настройке. Следующий запрос возвращает данные из этого внешнего набора данных:

    SELECT CityID, StateProvinceCode, CityName, YearNumber, LatestRecordedPopulation FROM dbo.CityPopulationStatistics;

Чтобы понять, какие городов может представлять интерес для дальнейшее расширение, следующий запрос просматривает показатель увеличения городов и возвращает первые 100 крупнейших городов с значительный рост и где Wide World Importers нет продаж присутствия. Запрос соединяет между удаленной таблицы `dbo.CityPopulationStatistics` и локальной таблицы `Dimension.City`и фильтр, обращенных к локальной таблице `Fact.Sales`.

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

Кластеризованные индексы Columnstore (CCI) используются с таблицами фактов для сокращения объема хранилища и повысить производительность запросов. При использовании CCI базового хранилища для таблиц фактов использует сжатие столбцов.

Некластеризованные индексы используются поверх кластеризованного индекса, для упрощения первичный ключ и ограничения внешнего ключа. Эти ограничения были добавлены из множество осторожность — процесс ETL источники данных из базы данных WideWorldImporters, который имеет ограничения для обеспечения целостности. Удаление ограничения первичного и внешнего ключа и их вспомогательные индексов бы уменьшить занимаемое место хранения таблиц фактов.

**Размер данных**

Образец базы данных имеет ограниченный размер данных, чтобы упростить процесс загрузки и установки примера. Тем не менее чтобы просмотреть реальные преимущества от индексов columnstore, вам следует использовать большего набора данных.

Можно выполнить следующую инструкцию, чтобы увеличить размер `Fact.Sales` таблицы путем вставки другой 12 миллионов строк данных выборки. Эти строки все вставляются в год 2012, таким образом, чтобы исключить конфликты с процессом ETL.

    EXECUTE [Application].[Configuration_PopulateLargeSaleTable]

Эта инструкция займет примерно через 5 минут для выполнения. Чтобы вставить более чем 12 миллионов строк, передайте нужное число строк, которые вставляются в качестве параметра в хранимую процедуру.

Чтобы сравнить производительность запросов с и без columnstore, можно удалить или повторно создать кластеризованный индекс columnstore.

Чтобы удалить индекс:

    DROP INDEX [CCX_Fact_Order] ON [Fact].[Order]

Для повторного создания:

    CREATE CLUSTERED COLUMNSTORE INDEX [CCX_Fact_Order] ON [Fact].[Order]

## <a name="partitioning"></a>Секционирование

(Полная версия образца)

Размер данных в хранилище данных может стать очень большим. Поэтому рекомендуется использовать секционирование для управления хранением больших таблиц в базе данных.

Все таблицы фактов большего размера секционируются по годам. Единственным исключением является `Fact.Stock Holdings`, который не основанное на дате и имеет лишь ограниченный объем данных по сравнению с другими таблицами фактов.

Функции секционирования, используемого для всех секционированных таблиц является `PF_Date`, и используется схема секционирования используется `PS_Date`.

## <a name="in-memory-oltp"></a>In-Memory OLTP

(Полная версия образца)

WideWorldImportersDW использует оптимизированные для памяти таблицы SCHEMA_ONLY для промежуточных таблиц. Все `Integration.` * `_Staging` таблиц, оптимизированных для памяти таблицы SCHEMA_ONLY.

Таблиц SCHEMA_ONLY удобен тем, что они не регистрируются и не требуют любой доступ к диску. Это повышает производительность процесса ETL. Так как эти таблицы не регистрируются, их содержимое будут утеряны, если возникает сбой. Тем не менее источник данных доступен, поэтому процесс ETL можно просто перезапустить, если происходит сбой.
