---
title: "Запросы PolyBase | Документация Майкрософт"
ms.custom: 
ms.date: 03/09/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: polybase
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine-polybase
ms.tgt_pltfrm: 
ms.topic: article
keywords:
- PolyBase
helpviewer_keywords:
- PolyBase, import and export
- Hadoop, import with PolyBase
- Hadoop, export with PolyBase
- Azure blob storage, import with PolyBase
- Azure blob storage, export with PolyBase
ms.assetid: 2c5aa2bd-af7d-4f57-9a28-9673c2a4c07e
caps.latest.revision: 18
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: d6cc1b4523bdb0b48cfc22b34b205e15613fb290
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="polybase-queries"></a>PolyBase Queries
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  Здесь приведены примеры запросов, в которых применяется компонент [Руководство по PolyBase](../../relational-databases/polybase/polybase-guide.md) службы SQL Server 2016. Прежде чем использовать эти запросы, следует ознакомиться с инструкциями T-SQL, необходимыми для установки PolyBase. (Дополнительные сведения см. в статье [Объекты T-SQL PolyBase](../../relational-databases/polybase/polybase-t-sql-objects.md).)  
  
## <a name="queries"></a>Запросы  
 Отправить запрос к внешним таблицам можно с помощью инструкций Transact-SQL или средств бизнес-аналитики.  
  
## <a name="select-from-external-table"></a>Выбор данных из внешней таблицы (SELECT)  
 Простой запрос, возвращающий данные из определенной внешней таблицы.  
  
```tsql  
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
  
 Здесь SQL Server 2016 инициирует задание map-reduce для получения строк, соответствующих предикату customer.account_balance < 200000 в Hadoop. Поскольку запрос может быть выполнен и без сканирования всех строк в таблице, в SQL Server копируются только строки, удовлетворяющие условиям предиката. Это существенно экономит время и место для временного хранения данных, если число клиентов с балансом < 200 000 меньше числа клиентов с балансом >= 200 000.  
  Copy imageCopy Code   
SELECT * FROM customer WHERE customer.account_balance < 200000.  
  
```  
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
  
-   Операторы двоичного сравнения (\<, >, =,! =, <>, > =, < =) для чисел, дат и значений времени.  
  
-   Арифметические операторы (+, -, *, /, %).  
  
-   Логические операторы (AND, OR).  
  
-   Унарные операторы (NOT, IS NULL, IS NOT NULL).  
  
 Операторы BETWEEN, NOT, IN и LIKE можно включить. Это зависит от того, каким образом оптимизатор запросов перезаписывает их как последовательность инструкций с использованием основных реляционных операторов.  
  
 Этот запрос содержит несколько предикатов, которые могут быть переданы в Hadoop. SQL Server может отправлять в Hadoop задания map-reduce для выполнения предиката customer.account_balance <= 200000. Выражение BETWEEN 92656 и 92677 состоит из двоичных и логических операций, которые могут быть переданы в Hadoop. Логический оператор AND в столбцах customer.account_balance и customer.zipcode является конечным выражением.  
  
 Говоря в целом, задания map-reduce могут выполнять все условия, указанные в предложении WHERE. В параллельное хранилище данных SQL Server копируются только те данные, которые соответствуют условиям отбора.  
  
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
 Вы можете импортировать данные из Hadoop или службы хранилища Azure в SQL Server для постоянного хранения. Чтобы импортировать данные, на которые ссылается внешняя таблица, следует использовать инструкцию SELECT INTO. Оперативно создайте реляционную таблицу, а затем индекс хранилища столбца на основе таблицы, описанной на втором шаге.  
  
```sql  
-- PolyBase Scenario 2: Import external data into SQL Server.  
-- Import data for fast drivers into SQL Server to do more in-depth analysis and  
-- leverage Columnstore technology.  
  
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
Вы можете экспортировать данные из SQL Server в службу хранилища Azure или Hadoop. В первую очередь включите функцию экспорта, задав для аргумента sp_configure параметра 'allow polybase export' значение 1. Затем создайте внешнюю таблицу, которая указывает на целевой каталог. Затем используйте инструкцию INSERT INTO, чтобы экспортировать данные из локальной таблицы SQL Server во внешний источник данных. При выполнении инструкции INSERT INTO создается целевой каталог (если его не существует), а результаты выполнения инструкции SELECT экспортируются в указанное расположение в заданном формате. Внешние файлы получают имена вида *ИДзапроса_дата_время_ИД.формат*, где *ИД* — это нарастающий идентификатор, а *формат* — это формат экспортированных данных. Пример: QID776_20160130_182739_0.orc.  
  
```sql  
-- PolyBase Scenario 3: Export data from SQL Server to Hadoop.  
-- Create an external table.   
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
  
  

