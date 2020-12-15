---
title: Каталог базы данных OLAP WideWorldImporters-SQL | Документация Майкрософт
description: Сведения о схемах, таблицах и хранимых процедурах, используемых для хранения данных и аналитической обработки в базе данных WideWorldImportersDW.
ms.prod: sql
ms.prod_service: sql
ms.technology: samples
ms.custom: ''
ms.date: 08/04/2018
ms.reviewer: ''
ms.topic: conceptual
author: MashaMSFT
ms.author: mathoma
monikerRange: '>=sql-server-2016||>=sql-server-linux-2017||=azure-sqldw-latest||>=aps-pdw-2016||=azuresqldb-mi-current'
ms.openlocfilehash: e246d516d3c05b9a2c6725f7fd3e3f787066b8aa
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2020
ms.locfileid: "97461405"
---
# <a name="wideworldimportersdw-database-catalog"></a>Каталог базы данных WideWorldImportersDW
[!INCLUDE[appliesto-ss-xxxx-asdw-pdw-md](../includes/appliesto-ss-xxxx-asdw-pdw-md.md)]
Пояснения к схемам, таблицам и хранимым процедурам в базе данных WideWorldImportersDW. 

База данных WideWorldImportersDW используется для хранения данных и аналитической обработки. Данные о транзакциях по продажам и покупкам создаются в базе данных WideWorldImporters и загружаются в базу данных WideWorldImportersDW с помощью **ежедневного ETL-процесса**.

Поэтому данные в WideWorldImportersDW представляют данные в WideWorldImporters, но таблицы организованы по-разному. Хотя WideWorldImporters имеет традиционную нормализованную схему, WideWorldImportersDW использует подход « [звезда](https://wikipedia.org/wiki/Star_schema) » для создания таблицы. Помимо таблиц фактов и измерений, база данных включает в себя ряд промежуточных таблиц, используемых в процессе ETL.

## <a name="schemas"></a>Схемы

Различные типы таблиц организованы в три схемы.

|схема|Описание|
|-----------------------------|---------------------|
|Измерение|Таблицы измерений.|
|Факты| Таблицы фактов.|  
|Интеграция|Промежуточные таблицы и другие объекты, необходимые для ETL.|  

## <a name="tables"></a>Таблицы

Ниже перечислены измерения и таблицы фактов. Таблицы в схеме интеграции используются только для процесса ETL и не перечислены в списке.

### <a name="dimension-tables"></a>Таблицы измерений

WideWorldImportersDW содержит следующие таблицы измерений. Описание включает связь с исходными таблицами в базе данных WideWorldImporters.

|Таблица|Исходные таблицы|
|-----------------------------|---------------------|
|City|`Application.Cities`, `Application.StateProvinces`, `Application.Countries`.|
|Customer|`Sales.Customers`, `Sales.BuyingGroups`, `Sales.CustomerCategories`.|
|Дата|Новая таблица со сведениями о датах, включая финансовый год (на основе 1 ноября начала финансового года).|
|Сотрудник|`Application.People`.|
|стоккитем|`Warehouse.StockItems`, `Warehouse.Colors`, `Warehouse.PackageType`.|
|Поставщик|`Purchasing.Suppliers`, `Purchasing.SupplierCategories`.|
|PaymentMethod|`Application.PaymentMethods`.|
|TransactionType|`Application.TransactionTypes`.|

### <a name="fact-tables"></a>Таблицы фактов

WideWorldImportersDW имеет следующие таблицы фактов. Описание включает связь с исходными таблицами в базе данных WideWorldImporters, а также классы запросов аналитики и отчетности, которые обычно используются в каждой таблице фактов.

|Таблица|Исходные таблицы|Образец аналитики|
|-----------------------------|---------------------|---------------------|
|Порядок|`Sales.Orders` и `Sales.OrderLines`|Продажи продавцов, средств выбора и упаковки и времени на выбор заказов. Кроме того, в небольших складских ситуациях, ведущих к обратным заказам.|
|Sale|`Sales.Invoices` и `Sales.InvoiceLines`|Даты продаж, даты доставки, рентабельность с течением времени, рентабельность по менеджеру по продажам.|
|Purchase|`Purchasing.PurchaseOrderLines`|Ожидаемое и фактическое время опережения|
|Транзакция|`Sales.CustomerTransactions` и `Purchasing.SupplierTransactions`|Измерение дат проблем и дат финализации и сумм.|
|Перемещение|`Warehouse.StockTransactions`|Перемещения с течением времени.|
|Удерживаемые акции|`Warehouse.StockItemHoldings`|Уровни и стоимость запасов в наличии.|

## <a name="stored-procedures"></a>Хранимые процедуры

Хранимые процедуры используются в основном для процесса ETL и для целей настройки.

Все расширения образца рекомендуется использовать `Reports` для Reporting Services отчетов и `PowerBI` схемы для доступа к Power BI.

### <a name="application-schema"></a>Схема приложения

Эти процедуры используются для настройки образца. Они используются для применения функций Enterprise Edition к стандартной версии примера, добавления Polybase и повторного заполнения ETL.

|Процедура|Назначение|
|-----------------------------|---------------------|
|Configuration_ApplyPartitionedColumnstoreIndexing|Применяет секционирование и индексы columnstore для таблиц фактов.|
|Configuration_ConfigureForEnterpriseEdition|Применяет секционирование, индексацию columnstore и в памяти.|
|Configuration_EnableInMemory|Заменяет промежуточные таблицы интеграции на SCHEMA_ONLY таблиц, оптимизированных для памяти, для повышения производительности ETL.|
|Configuration_ApplyPolyBase|Настраивает внешний источник данных, формат файла и таблицу.|
|Configuration_PopulateLargeSaleTable|Применяет изменения Enterprise Edition, а затем заполняет больший объем данных для 2012 календарного года в качестве дополнительного журнала.|
|Configuration_ReseedETL|Удаляет существующие данные и перезапускает начальные значения ETL. Это позволяет повторно заполнить базу данных OLAP в соответствии с обновленными строками в базе данных OLTP.|

### <a name="integration-schema"></a>Схема интеграции

Процедуры, используемые в процессе ETL, попадают в следующие категории:
- Вспомогательные процедуры для пакета ETL — все процедуры Get *.
- Процедуры, используемые пакетом ETL для переноса промежуточных данных в таблицы DW — все процедуры миграции *.
- `PopulateDateDimensionForYear` — Принимает год и гарантирует, что все даты в этом году будут заполнены в `Dimension.Date` таблице.

### <a name="sequences-schema"></a>Схема последовательностей

Процедуры для настройки последовательностей в базе данных.

|Процедура|Назначение|
|-----------------------------|---------------------|
|ресидаллсекуенцес|Вызывает процедуру `ReseedSequenceBeyondTableValue` для всех последовательностей.|
|ресидсекуенцебэйондтаблевалуе|Используется для перемещения следующего значения последовательности после значения в любой таблице, использующей ту же последовательность. (Например, `DBCC CHECKIDENT` для столбцов идентификаторов, эквивалентных для последовательностей, но в потенциально нескольких таблицах.)|
