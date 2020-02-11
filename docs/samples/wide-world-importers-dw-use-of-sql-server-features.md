---
title: Основные возможности базы данных хранилища WideWorldImporters
ms.prod: sql
ms.prod_service: sql
ms.technology: samples
ms.date: 08/04/2018
ms.reviewer: ''
ms.topic: conceptual
author: MashaMSFT
ms.author: mathoma
monikerRange: '>=sql-server-2016||>=sql-server-linux-2017||=azure-sqldw-latest||>=aps-pdw-2016||=sqlallproducts-allversions||=azuresqldb-mi-current'
ms.custom: seo-lt-2019
ms.openlocfilehash: dfce2ce4a6f13a25687d668268f532893c1404e0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "74056292"
---
# <a name="wideworldimportersdw-use-of-sql-server-features-and-capabilities"></a>WideWorldImportersDW использование функций и возможностей SQL Server
[!INCLUDE[appliesto-ss-xxxx-asdw-pdw-md](../includes/appliesto-ss-xxxx-asdw-pdw-md.md)]
WideWorldImportersDW предназначен для демонстрации многих ключевых функций SQL Server, которые подходят для хранения и аналитики данных. Ниже приведен список функций и возможностей SQL Server, а также описание их использования в WideWorldImportersDW.

## <a name="polybase"></a>PolyBase

[Применяется к SQL Server (2016 и более поздние версии)]

Polybase используется для объединения данных о продажах из WideWorldImportersDW с общедоступным набором данных по демографическим данным, чтобы понять, какие города могут быть интересны для дальнейшего расширения продаж.

Чтобы включить использование Polybase в образце базы данных, убедитесь, что она установлена, и выполните следующую хранимую процедуру в базе данных:

    EXEC [Application].[Configuration_ApplyPolyBase]

При этом будет создана внешняя таблица `dbo.CityPopulationStatistics` , которая ссылается на общедоступный набор данных, содержащий данные о населении для городов в США, размещенном в хранилище BLOB-объектов Azure. Рекомендуется проверить код в хранимой процедуре, чтобы понять процесс настройки. Если вы хотите разместить собственные данные в хранилище BLOB-объектов Azure и защитить их от общего доступа, вам потребуется выполнить дополнительные действия по настройке. Следующий запрос возвращает данные из этого набора внешних данных:

    SELECT CityID, StateProvinceCode, CityName, YearNumber, LatestRecordedPopulation FROM dbo.CityPopulationStatistics;

Чтобы понять, какие города могут быть интересны для дальнейшего расширения, следующий запрос просматривает темп роста в городах и возвращает первые 100 самых крупных городов с значительным ростом, а также о том, где широкие средства импорта не имеют присутствия по продажам. Запрос включает соединение между удаленной таблицей `dbo.CityPopulationStatistics` и локальной таблицей `Dimension.City`, а также фильтр, включающий локальную таблицу. `Fact.Sales`

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

(Полная версия примера)

Кластеризованные индексы columnstore (CCI) используются со всеми таблицами фактов для уменьшения объема хранилища и повышения производительности запросов. Используя CCI, в базовом хранилище для таблиц фактов используется сжатие столбцов.

Некластеризованные индексы используются поверх кластеризованного индекса columnstore, чтобы упростить ограничения первичного и внешнего ключей. Эти ограничения были добавлены из множество, что в процессе ETL источники данных из базы данных WideWorldImporters, которые имеют ограничения для обеспечения целостности. Удаление первичных и внешних ограничений, а также их вспомогательных индексов приведет к уменьшению объема хранилища таблиц фактов.

**Размер данных**

Образец базы данных имеет ограниченный размер данных, чтобы упростить загрузку и установку образца. Однако, чтобы увидеть реальные преимущества производительности индексов columnstore, необходимо использовать больший набор данных.

Можно выполнить следующую инструкцию, чтобы увеличить размер `Fact.Sales` таблицы, вставив еще 12 000 000 строк образца данных. Эти строки вставлены в год 2012, что не связано с процессом ETL.

    EXECUTE [Application].[Configuration_PopulateLargeSaleTable]

Выполнение этой инструкции займет около 5 минут. Чтобы вставить более 12 000 000 строк, передайте нужное количество строк в качестве параметра в эту хранимую процедуру.

Для сравнения производительности запросов с и без columnstore можно удалить или повторно создать кластеризованный индекс columnstore.

Чтобы удалить индекс, выполните следующие действия.

    DROP INDEX [CCX_Fact_Order] ON [Fact].[Order]

Для повторного создания:

    CREATE CLUSTERED COLUMNSTORE INDEX [CCX_Fact_Order] ON [Fact].[Order]

## <a name="partitioning"></a>Секционирование

(Полная версия примера)

Размер данных в хранилище данных может увеличиваться очень большим. Поэтому рекомендуется использовать секционирование для управления хранением больших таблиц в базе данных.

Все большие таблицы фактов секционированы по годам. Единственным исключением является `Fact.Stock Holdings`, которое не основано на дате и имеет ограниченный размер данных по сравнению с другими таблицами фактов.

Функция секционирования, используемая для всех секционированных `PF_Date`таблиц, —, а используемая схема `PS_Date`секционирования —.

## <a name="in-memory-oltp"></a>Выполняющаяся в памяти OLTP

(Полная версия примера)

WideWorldImportersDW использует SCHEMA_ONLY оптимизированные для памяти таблицы для промежуточных таблиц. `Integration.` * Все `_Staging` таблицы SCHEMA_ONLY оптимизированные для памяти таблицы.

Преимуществом SCHEMA_ONLY таблиц является то, что они не записываются в журнал и не нуждаются в доступе к диску. Это повышает производительность процесса ETL. Поскольку эти таблицы не регистрируются, их содержимое теряется в случае сбоя. Однако источник данных по-прежнему доступен, поэтому процесс ETL можно просто перезапустить в случае сбоя.
