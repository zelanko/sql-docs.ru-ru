---
title: База данных каталога | Документы Microsoft
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: ''
ms.component: samples
ms.technology:
- samples
ms.custom: ''
ms.date: 10/31/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5ed65e42-527a-45e7-9a91-7179e892652e
caps.latest.revision: 2
author: BarbKess
ms.author: barbkess
manager: craigg
robots: noindex,nofollow
ms.workload: On Demand
ms.openlocfilehash: 8d3957abef7fb70698c04fd22d390d96ac4cd17b
ms.sourcegitcommit: 094c46e7fa6de44735ed0040c65a40ec3d951b75
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/07/2018
---
# <a name="wideworldimportersdw-database-catalog"></a>Каталог базы данных WideWorldImportersDW
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
Описания для схем, таблиц и хранимых процедур в базе данных WideWorldImportersDW. 

WideWorldImportersDW базы данных используется для хранения данных и аналитической обработки. Транзакционные данные о продажах и покупки создается в базе данных WideWorldImporters и загружается в WideWorldImportersDW базы данных с помощью **ежедневно выполняемый процесс ETL**.

Таким образом, данные в WideWorldImportersDW отражает данные в WideWorldImporters, но таблицах организованы по-разному. Хотя WideWorldImporters имеет традиционных нормализованную схему, использует WideWorldImportersDW [схемы типа «звезда»](https://wikipedia.org/wiki/Star_schema) подход для своего проекта таблицы. Помимо таблиц фактов и измерений база данных включает несколько промежуточных таблиц, которые используются в процессе ETL.

## <a name="schemas"></a>Схемы

Различные типы таблиц организованы в три схемы.

|Схема|Описание|
|-----------------------------|---------------------|
|Измерение|Таблицы измерений.|
|Факт|Таблицы фактов.|  
|Интеграция|Промежуточные таблицы и другие объекты, необходимые для ETL.|  

## <a name="tables"></a>Таблицы

Ниже перечислены таблиц фактов и измерений. Таблицы в схеме интеграции используются только для процесса ETL, а не указываются.

### <a name="dimension-tables"></a>Таблицы измерений

WideWorldImportersDW имеет следующими таблицами измерений. Описание содержит связь с исходных таблиц в базе данных WideWorldImporters.

|Таблица|Исходные таблицы|
|-----------------------------|---------------------|
|Город|`Application.Cities`, `Application.StateProvinces`, `Application.Countries`.|
|Customer|`Sales.Customers`, `Sales.BuyingGroups`, `Sales.CustomerCategories`.|
|Дата|Новая таблица с сведения о дате, включая финансовом году (1 ноября на основе запуск за финансовый год).|
|Сотрудник|`Application.People`.|
|StockItem|`Warehouse.StockItems`, `Warehouse.Colors`, `Warehouse.PackageType`.|
|Поставщик|`Purchasing.Suppliers`, `Purchasing.SupplierCategories`.|
|PaymentMethod|`Application.PaymentMethods`.|
|TransactionType|`Application.TransactionTypes`.|

### <a name="fact-tables"></a>Таблицы фактов

WideWorldImportersDW имеет следующие таблицы фактов. Описание содержит связь с исходных таблиц в базе данных WideWorldImporters, а также классы аналитики и отчетности запросов, каждая таблица фактов обычно используется с.

|Таблица|Исходные таблицы|Образец аналитика|
|-----------------------------|---------------------|---------------------|
|Порядок|`Sales.Orders`и`Sales.OrderLines`|Продажи людях, выбора и packer производительности и на время для выбора заказов. Кроме того низкий стандартных ситуациях приведет к невыполненные заказы.|
|Продажи|`Sales.Invoices`и`Sales.InvoiceLines`|Продажи даты, даты доставки, рентабельности со временем, рентабельности по менеджерам по продажам.|
|Покупки|`Purchasing.PurchaseOrderLines`|Фактический период ожидаемого vs|
|Transaction|`Sales.CustomerTransactions`и`Purchasing.SupplierTransactions`|Измерение даты завершения vs дат проблему и суммы.|
|Перемещение|`Warehouse.StockTransactions`|Перемещений со временем.|
|Холдинг акций|`Warehouse.StockItemHoldings`|Уровни запасов в наличии и значение.|

## <a name="stored-procedures"></a>Хранимые процедуры

Хранимые процедуры используются в основном для процесса ETL, а также для целей конфигурации.

Рекомендуется использовать все расширения образца `Reports` схемы для отчетов служб Reporting Services и `PowerBI` схемы для доступа к Power BI.

### <a name="application-schema"></a>Схема приложения

Эти процедуры используются для настройки образца. Они используются для применения функции выпуска enterprise до версии выпуска standard edition образца, добавить PolyBase и повторной установки начальных значений ETL.

|Процедура|Назначение|
|-----------------------------|---------------------|
|Configuration_ApplyPartitionedColumnstoreIndexing|Применяется секционирование и columnstore индексы для таблиц фактов.|
|Configuration_ConfigureForEnterpriseEdition|Применяется секционирование, columnstore индексации и в памяти.|
|Configuration_EnableInMemory|Заменяет интеграции промежуточные таблицы с оптимизированными для памяти таблиц SCHEMA_ONLY, чтобы повысить производительность ETL.|
|Configuration_ApplyPolybase|Настраивает внешний источник данных, формат файла и таблицы.|
|Configuration_PopulateLargeSaleTable|Применяет изменения enterprise edition, а затем заполняет больший объем данных для календарного года 2012 как дополнительные данные журнала.|
|Configuration_ReseedETL|Удаляет существующие данные и перезапускает ETL начальные значения. Это позволяет для повторного заполнения базы данных OLAP, сопоставляемое обновленных строк в базе данных OLTP.|

### <a name="integration-schema"></a>Интеграция схемы

Процедуры, используемые в процессе ETL, попадают в следующие категории:
- Вспомогательные процедуры для пакета ETL - все Get * процедуры.
- Процедуры, используемые ETL-пакета по переносу промежуточные данные в таблицах хранилища данных — все процедуры миграции *.
- `PopulateDateDimensionForYear` — Принимает года и гарантирует, что все даты за этот год, вставляются в `Dimension.Date` таблицу.

### <a name="sequences-schema"></a>Схемы последовательностей

Процедуры для настройки последовательностей в базе данных.

|Процедура|Назначение|
|-----------------------------|---------------------|
|ReseedAllSequences|Вызывает процедуру `ReseedSequenceBeyondTableValue` для всех последовательностей.|
|ReseedSequenceBeyondTableValue|Используется для изменения положения следующего значения из последовательности за значение в таблице, которая использует ту же последовательность. (Такие как `DBCC CHECKIDENT` для идентификации столбцов эквивалент для последовательностей, но потенциально нескольким таблицам.)|
