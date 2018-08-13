---
title: Каталог базы данных WideWorldImporters OLAP - SQL | Документация Майкрософт
ms.prod: sql
ms.prod_service: sql
ms.technology: samples
ms.custom: ''
ms.date: 08/04/2018
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: '>=sql-server-2016||>=sql-server-linux-2017||=azure-sqldw-latest||>=aps-pdw-2016||=sqlallproducts-allversions'
ms.openlocfilehash: 757820680533cfa2eaff8403e2056f0a4d3b1a96
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/06/2018
ms.locfileid: "39556954"
---
# <a name="wideworldimportersdw-database-catalog"></a>Каталог базы данных WideWorldImportersDW
[!INCLUDE[appliesto-ss-xxxx-asdw-pdw-md](../includes/appliesto-ss-xxxx-asdw-pdw-md.md)]
Пояснения для схемы, таблицы и хранимые процедуры в базе данных WideWorldImportersDW. 

База данных WideWorldImportersDW используется для хранения данных и аналитической обработки. Транзакционные данные о продажах и покупки создается в базе данных WideWorldImporters и загружаются в базу данных WideWorldImportersDW при помощи **ежедневно выполняемый процесс ETL**.

Данные в WideWorldImportersDW таким образом отражает данные в WideWorldImporters, но таблицы поделены по-разному. Хотя WideWorldImporters имеет традиционных нормализованных схем, использует WideWorldImportersDW [схемой "звезда"](https://wikipedia.org/wiki/Star_schema) подход по ее разработке таблиц. Помимо таблиц фактов и измерений база данных включает несколько промежуточных таблиц, которые используются в процессе ETL.

## <a name="schemas"></a>Схемы

Разные типы таблиц организованы в три схемы.

|Схема|Описание|
|-----------------------------|---------------------|
|Измерение|Таблицы измерений.|
|Факт|Таблицы фактов.|  
|Интеграция|Промежуточные таблицы и другие объекты, необходимые для Извлечения.|  

## <a name="tables"></a>Таблицы

Ниже перечислены таблицы фактов и измерений. Таблицы в схеме интеграции используются только для процесса ETL и не указываются.

### <a name="dimension-tables"></a>Таблицы измерений

WideWorldImportersDW имеет следующими таблицами измерений. Описание содержит связь с исходных таблиц в базе данных WideWorldImporters.

|Таблица|Исходные таблицы|
|-----------------------------|---------------------|
|Город|`Application.Cities`, `Application.StateProvinces`, `Application.Countries`.|
|Customer|`Sales.Customers`, `Sales.BuyingGroups`, `Sales.CustomerCategories`.|
|Дата|Новую таблицу с информацией о дате, включая м финансовом году (1 ноября на основе запуск за финансовый год).|
|Сотрудник|`Application.People`.|
|StockItem|`Warehouse.StockItems`, `Warehouse.Colors`, `Warehouse.PackageType`.|
|Поставщик|`Purchasing.Suppliers`, `Purchasing.SupplierCategories`.|
|PaymentMethod|`Application.PaymentMethods`.|
|TransactionType|`Application.TransactionTypes`.|

### <a name="fact-tables"></a>Таблицы фактов

WideWorldImportersDW имеет в следующих таблицах фактов. Описание содержит связь с исходных таблиц в базе данных WideWorldImporters, а также классы запросов, аналитики и отчетов, которые каждая таблица фактов обычно используется с.

|Таблица|Исходные таблицы|Пример аналитики|
|-----------------------------|---------------------|---------------------|
|Порядок|`Sales.Orders` и `Sales.OrderLines`|Продажи людях, средство выбора/packer производительности и на времени для подбора заказов. Кроме того низкой акций ситуаций, что приводит к невыполненные заказы.|
|Продажи|`Sales.Invoices` и `Sales.InvoiceLines`|Дат продаж, даты доставки, рентабельность со временем, прибыльность по продажам.|
|Покупки|`Purchasing.PurchaseOrderLines`|Ожидаемые и фактические время|
|Transaction|`Sales.CustomerTransactions` и `Purchasing.SupplierTransactions`|Измерение даты завершения vs даты проблема и суммы.|
|Перемещение|`Warehouse.StockTransactions`|Перемещений со временем.|
|Продажа|`Warehouse.StockItemHoldings`|На нижнем уровне запасов и значение.|

## <a name="stored-procedures"></a>Хранимые процедуры

Хранимые процедуры используются в основном для процесса ETL, а также для целей конфигурации.

Любые расширения примера, рекомендуется использовать `Reports` схемы для отчетов служб Reporting Services и `PowerBI` схемы для доступа к Power BI.

### <a name="application-schema"></a>Схема приложения

Эти процедуры используются для настройки примера. Они используются для применения функции выпуска enterprise до версии выпуска standard edition образца, добавьте PolyBase и повторной установки начальных значений ETL.

|Процедура|Назначение|
|-----------------------------|---------------------|
|Configuration_ApplyPartitionedColumnstoreIndexing|Применяет как секционирования и индексов columnstore для таблиц фактов.|
|Configuration_ConfigureForEnterpriseEdition|Применяется секционирование, columnstore индексирования и в памяти.|
|Configuration_EnableInMemory|Заменяет интеграции промежуточных таблиц с оптимизированной для памяти таблиц SCHEMA_ONLY, чтобы повысить производительность ETL.|
|Configuration_ApplyPolybase|Настраивает внешний источник данных, формат файла и таблицы.|
|Configuration_PopulateLargeSaleTable|Применяет изменения enterprise edition, а затем заполняет больший объем данных для календарного года 2012 как дополнительные данные журнала.|
|Configuration_ReseedETL|Удаляет существующие данные и перезапускает ETL начальные значения. Это позволяет при повторном заполнении базы данных OLAP в соответствии с обновленных строк в базе данных OLTP.|

### <a name="integration-schema"></a>Интеграция схемы

Процедуры, используемые в процессе ETL попадают в этих категориях:
- Вспомогательные процедуры для пакета ETL - все Get * процедуры.
- Процедур переноса с помощью пакета ETL промежуточные данные в таблицы хранилища данных — все процедуры миграции *.
- `PopulateDateDimensionForYear` — Принимает года и гарантирует, что все даты за этот год будут заполнены в `Dimension.Date` таблицы.

### <a name="sequences-schema"></a>Схемы последовательностей

Процедуры настройки последовательности в базе данных.

|Процедура|Назначение|
|-----------------------------|---------------------|
|ReseedAllSequences|Вызывает процедуру `ReseedSequenceBeyondTableValue` для всех последовательностей.|
|ReseedSequenceBeyondTableValue|Используется для изменения положения следующего значения из последовательности за пределами значения в таблице, которая использует ту же последовательность. (Например `DBCC CHECKIDENT` для идентификаторов столбцов эквивалент для последовательностей, но для потенциально нескольких таблиц.)|
