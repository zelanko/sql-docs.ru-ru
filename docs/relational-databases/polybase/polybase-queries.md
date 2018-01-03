---
title: "Запросы PolyBase | Документация Майкрософт"
ms.custom: 
ms.date: 12/08/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: polybase
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine-polybase
ms.tgt_pltfrm: 
ms.topic: article
keywords: PolyBase
helpviewer_keywords:
- PolyBase, import and export
- Hadoop, import with PolyBase
- Hadoop, export with PolyBase
- Azure blob storage, import with PolyBase
- Azure blob storage, export with PolyBase
ms.assetid: 2c5aa2bd-af7d-4f57-9a28-9673c2a4c07e
caps.latest.revision: "18"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 0d02b151b9197d2e6cb3f6a58161e84256a9073e
ms.sourcegitcommit: 2208a909ab09af3b79c62e04d3360d4d9ed970a7
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2018
---
# <a name="polybase-queries"></a>PolyBase Queries
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  В этой статье приведены примеры запросов, в которых применяется компонент [Руководство по PolyBase](../../relational-databases/polybase/polybase-guide.md) службы SQL Server 2016. Прежде чем использовать эти запросы, следует ознакомиться с инструкциями T-SQL, необходимыми для настройки PolyBase. (Дополнительные сведения см. в статье [Объекты T-SQL PolyBase](../../relational-databases/polybase/polybase-t-sql-objects.md).)
  
## <a name="queries"></a>Запросы  
 Отправить запрос к внешним таблицам можно с помощью инструкций Transact-SQL или средств бизнес-аналитики.
  
## <a name="select-from-external-table"></a>Выбор данных из внешней таблицы (SELECT)  
 Простой запрос, возвращающий данные из определенной внешней таблицы.  
  
```sql  
SELECT TOP 10 * FROM [dbo].[SensorData];   
```
  
 Простой запрос, включающий предикат.

```
SELECT * FROM [dbo].[SensorData]
WHERE Speed > 65;
```

## <a name="join-external-tables-with-local-tables"></a>Соединение внешних и локальных таблиц (JOIN)

```
SELECT InsuranceCustomers.FirstName,   
                           InsuranceCustomers.LastName,   
                           SensorData.Speed  
FROM InsuranceCustomers INNER JOIN SensorData    
ON InsuranceCustomers.CustomerKey = SensorData.CustomerKey   
WHERE SensorData.Speed > 65   
ORDER BY SensorData.Speed DESC  
  
```  
  
## <a name="pushdown-computation-to-hadoop"></a>Включение вычислений для Hadoop

Варианты включения показаны ниже.

### <a name="pushdown-for-selecting-a-subset-of-rows"></a>Включение выбора подмножества строк

Включение предиката позволяет повысить производительность для запроса, отбирающего подмножество строк из внешней таблицы.

В этом примере SQL Server 2016 инициирует задание map-reduce для получения строк, соответствующих предикату `customer.account_balance < 200000` в Hadoop. Так как запрос можно выполнить и без сканирования всех строк в таблице, в SQL Server копируются только строки, удовлетворяющие условиям предиката. Это существенно экономит время и место для временного хранения данных, если число клиентов с балансом < 200 000 меньше числа клиентов с балансом >= 200 000.

```
SELECT * FROM customer WHERE customer.account_balance < 200000
SELECT * FROM SensorData WHERE Speed > 65;  
```

### <a name="pushdown-for-selecting-a-subset-of-columns"></a>Включение выбора подмножества столбцов

Включение предиката позволяет повысить производительность для запроса, отбирающего подмножество столбцов из внешней таблицы.

В этом запросе SQL Server запускает задание map-reduce, предназначенное для предварительной обработки текстового файла Hadoop, разделенного запятыми, при которой в параллельное хранилище данных SQL Server попадают данные только для двух столбцов — customer.name и customer.zip_code.

```
SELECT customer.name, customer.zip_code FROM customer WHERE customer.account_balance < 200000
```

### <a name="pushdown-for-basic-expressions-and-operators"></a>Включение основных выражений и операторов

SQL Server позволяет использовать для включения предикатов следующие основные выражения и операторы:

+ Операторы двоичного сравнения (\<, >, =,! =, <>, > =, < =) для чисел, дат и значений времени.

+ Арифметические операторы (+, -, *, /, %).

+ Логические операторы (AND, OR).

+ Унарные операторы (NOT, IS NULL, IS NOT NULL).

Операторы BETWEEN, NOT, IN и LIKE можно включить. Фактическое поведение зависит от того, каким образом оптимизатор запросов перезаписывает выражения операторов как последовательности инструкций с использованием основных операторов отношения.

В этом примере запрос содержит несколько предикатов, которые могут быть переданы в Hadoop. SQL Server может отправлять в Hadoop задания map-reduce для выполнения предиката `customer.account_balance <= 200000`. Выражение `BETWEEN 92656 and 92677` также состоит из двоичных и логических операций, которые могут быть переданы в Hadoop. Логический оператор **AND** в столбцах `customer.account_balance and customer.zipcode` является конечным выражением.

С учетом этого сочетания предикатов задания map-reduce могут выполнять все условия, указанные в предложении WHERE. В хранилище SQL Server PDW копируются только те данные, которые соответствуют условиям отбора.

```
SELECT * FROM customer WHERE customer.account_balance <= 200000 AND customer.zipcode BETWEEN 92656 AND 92677
```

### <a name="force-pushdown"></a>Принудительное включение

```
SELECT * FROM [dbo].[SensorData]
WHERE Speed > 65
OPTION (FORCE EXTERNALPUSHDOWN);
```

### <a name="disable-pushdown"></a>Отключить включение

```
SELECT * FROM [dbo].[SensorData]
WHERE Speed > 65
OPTION (DISABLE EXTERNALPUSHDOWN);
```

## <a name="import-data"></a>импорт данных

Вы можете импортировать данные из Hadoop или службы хранилища Azure в SQL Server для постоянного хранения. Чтобы импортировать данные, на которые ссылается внешняя таблица, следует использовать инструкцию SELECT INTO. Оперативно создайте реляционную таблицу, а затем индекс хранилища столбцов на основе таблицы, описанной на втором шаге.

```sql
-- PolyBase scenario - import external data into SQL Server
-- Import data for fast drivers into SQL Server to do more in-depth analysis
-- Leverage columnstore technology
  
SELECT DISTINCT   
        Insured_Customers.FirstName, Insured_Customers.LastName,   
        Insured_Customers.YearlyIncome, Insured_Customers.MaritalStatus  
INTO Fast_Customers from Insured_Customers INNER JOIN   
(  
        SELECT * FROM CarSensor_Data where Speed > 35   
) AS SensorD  
ON Insured_Customers.CustomerKey = SensorD.CustomerKey  
ORDER BY YearlyIncome  
  
CREATE CLUSTERED COLUMNSTORE INDEX CCI_FastCustomers ON Fast_Customers;  
```

## <a name="export-data"></a>Экспорт данных

Вы можете экспортировать данные из SQL Server в службу хранилища Azure или Hadoop. 

В первую очередь включите функцию экспорта, задав для аргумента `sp_configure` параметра allow polybase export значение 1. Затем создайте внешнюю таблицу, которая указывает на целевой каталог. Затем используйте инструкцию INSERT INTO, чтобы экспортировать данные из локальной таблицы SQL Server во внешний источник данных. 

При выполнении инструкции INSERT INTO создается целевой каталог (если он не существует), а результаты выполнения инструкции SELECT экспортируются в указанное расположение в заданном формате файла. Внешние файлы получают имена вида *ИДзапроса_дата_время_ИД.формат*, где *ИД* — это нарастающий идентификатор, а *формат* — это формат экспортированных данных. Например, имя одного из файлов может выглядеть так: QID776_20160130_182739_0.orc.

> [!NOTE]
> При экспорте данных в Hadoop или хранилище BLOB-объектов Azure с помощью PolyBase передаются только данные без имен столбцов (метаданных), как определено в команде CREATE EXTERNAL TABLE.

```sql  
-- PolyBase scenario  - export data from SQL Server to Hadoop
-- Create an external table
CREATE EXTERNAL TABLE [dbo].[FastCustomers2009] (  
        [FirstName] char(25) NOT NULL,   
        [LastName] char(25) NOT NULL,   
        [YearlyIncome] float NULL,   
        [MaritalStatus] char(1) NOT NULL  
)  
WITH (  
        LOCATION='/old_data/2009/customerdata',  
        DATA_SOURCE = HadoopHDP2,  
        FILE_FORMAT = TextFileFormat,  
        REJECT_TYPE = VALUE,  
        REJECT_VALUE = 0  
);  
  
-- Export data: Move old data to Hadoop while keeping it query-able via an external table.  
INSERT INTO dbo.FastCustomer2009  
SELECT T.* FROM Insured_Customers T1 JOIN CarSensor_Data T2  
ON (T1.CustomerKey = T2.CustomerKey)  
WHERE T2.YearMeasured = 2009 and T2.Speed > 40;  
```

## <a name="new-catalog-views"></a>Новые представления каталога

В новых представлениях каталога, указанных ниже, отображаются внешние ресурсы.
  
```sql
SELECT * FROM sys.external_data_sources;   
SELECT * FROM sys.external_file_formats;  
SELECT * FROM sys.external_tables;  
```
  
 Определить, является ли таблица внешней, можно с помощью `is_external`  
  
```sql  
SELECT name, type, is_external FROM sys.tables WHERE name='myTableName'   
```  
  
## <a name="next-steps"></a>Следующие шаги  

Дополнительные сведения об устранении неполадок см. в статье [Устранение неполадок с PolyBase](../../relational-databases/polybase/polybase-troubleshooting.md).
