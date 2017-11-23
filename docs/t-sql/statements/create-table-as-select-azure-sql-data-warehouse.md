---
title: "Создание TABLE AS SELECT (хранилище данных Azure SQL) | Документы Microsoft"
ms.custom: 
ms.date: 10/07/2016
ms.prod: 
ms.prod_service: sql-data-warehouse, pdw
ms.reviewer: 
ms.service: sql-data-warehouse
ms.component: t-sql|statements
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
ms.assetid: d1e08f88-64ef-4001-8a66-372249df2533
caps.latest.revision: "40"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 68cdce96ae6c8e6f98b3c6d922101c6f830ff208
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="create-table-as-select-azure-sql-data-warehouse"></a>Создание TABLE AS SELECT (хранилище данных Azure SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

Создание таблицы AS ВЫБЕРИТЕ (CTAS) является одним из наиболее важных функций T-SQL, которые доступны. Это полностью Параллелизованный операцию, которая создает новые таблицы, основанной на выходных данных инструкции SELECT. CTAS является простой и быстрый способ создать копию таблицы.   
 
 Например можно используйте CTAS для:  
  
-   Повторно создайте таблицу со столбцом распространения другой хэш.
-   Повторно создайте таблицу репликации.   
-   Создайте индекс columnstore на лишь некоторые из столбцов в таблице.  
-   Запрос или импортируйте внешние данные.  

> [!NOTE]  
> Поскольку CTAS добавляет возможности создания таблицы, в этом разделе пытается не повторять в разделе CREATE TABLE. Вместо этого он описаны различия между инструкциями CTAS и CREATE TABLE. Подробности CREATE TABLE см. в разделе [CREATE TABLE (хранилище данных SQL Azure)](https://msdn.microsoft.com/library/mt203953/) инструкции. 
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
<a name="syntax-bk"></a>

## <a name="syntax"></a>Синтаксис   

```  
CREATE TABLE [ database_name . [ schema_name ] . | schema_name. ] table_name   
    [ ( column_name [ ,...n ] ) ]  
    WITH ( 
      <distribution_option> -- required
      [ , <table_option> [ ,...n ] ]    
    )  
    AS <select_statement>   
[;]  

<distribution_option> ::=
    { 
        DISTRIBUTION = HASH ( distribution_column_name ) 
      | DISTRIBUTION = ROUND_ROBIN 
      | DISTRIBUTION = REPLICATE
    }   

<table_option> ::= 
    {   
        CLUSTERED COLUMNSTORE INDEX --default for SQL Data Warehouse 
      | HEAP --default for Parallel Data Warehouse   
      | CLUSTERED INDEX ( { index_column_name [ ASC | DESC ] } [ ,...n ] ) --default is ASC 
    }  
    | PARTITION ( partition_column_name RANGE [ LEFT | RIGHT ] --default is LEFT  
        FOR VALUES ( [ boundary_value [,...n] ] ) ) 
  
<select_statement> ::=  
    [ WITH <common_table_expression> [ ,...n ] ]  
    SELECT select_criteria  

```  

<a name="arguments-bk"></a>
  
## <a name="arguments"></a>Аргументы  
Дополнительные сведения см. в разделе [раздел «аргументы»](https://msdn.microsoft.com/library/mt203953/#Arguments) в инструкции CREATE TABLE.  

<a name="column-options-bk"></a>

### <a name="column-options"></a>Параметры столбца
`column_name` [ ,...`n` ]   
 Имена столбцов не допускают [параметры столбца](https://msdn.microsoft.com/library/mt203953/#ColumnOptions) упоминалось в инструкции CREATE TABLE.  Вместо этого можно предоставить необязательный список из одного или нескольких имен столбцов для новой таблицы. Столбцы в новой таблице будут использовать имена, указываемые. При указании имен столбцов, число столбцов в списке столбцов должно совпадать количеством столбцов в результатах выберите. Если не указать имена столбцов, новая целевая таблица будет использовать имена столбцов в результатах инструкции select. 
  
 Нельзя указать параметры столбцов, таких как типы данных, параметров сортировки или допустимости значений NULL. Каждый из этих атрибутов является производным от результатов `SELECT` инструкции. Тем не менее можно использовать инструкцию SELECT для изменения атрибутов. Пример см. в разделе [CTAS используется для изменения столбца атрибутов](#ctas-change-column-attributes-bk).   

<a name="table-distribution-options-bk"></a>

### <a name="table-distribution-options"></a>Параметры распространения таблицы

`DISTRIBUTION` = `HASH`( *distribution_column_name* ) | ROUND_ROBIN | РЕПЛИЦИРОВАТЬ      
Инструкция CTAS требует параметр распространения и не имеет значения по умолчанию. Это отличается от СОЗДАНИЯ таблицы, которая имеет значения по умолчанию. 

Дополнительные сведения и понять, как выбрать столбец лучше всего распространения см. раздел [параметры распространения таблицы](https://msdn.microsoft.com/library/mt203953/#TableDistributionOptions) раздел в инструкции CREATE TABLE. 

<a name="table-partition-options-bk"></a>

### <a name="table-partition-options"></a>Параметры секционирования таблицы
Оператор CTAS создает несекционированная таблица по умолчанию, даже если исходная таблица является секционированной. Чтобы создать секционированную таблицу с помощью инструкции CTAS, необходимо указать параметр секционирования. 

Дополнительные сведения см. в разделе [параметры секционирования таблицы](https://msdn.microsoft.com/library/mt203953/#TablePartitionOptions) раздел в инструкции CREATE TABLE.

<a name="select-options-bk"></a>

### <a name="select-options"></a>Выберите параметры
Инструкция select является принципиальные различия между CTAS и CREATE TABLE.  

 `WITH`*обобщенное_табличное_выражение*  
 Задается временно именованный результирующий набор, называемый обобщенным табличным выражением (ОТВ). Дополнительные сведения см. в разделе [с общее_табличное_выражение &#40; Transact-SQL &#41; ](../../t-sql/queries/with-common-table-expression-transact-sql.md).  
  
 `SELECT`*select_criteria*  
 Заполняет новую таблицу с результатами из инструкции SELECT. *select_criteria* текст инструкции SELECT, которое определяет, какие данные необходимо скопировать в новую таблицу. Сведения об инструкциях SELECT см. в разделе [ВЫБЕРИТЕ &#40; Transact-SQL &#41; ](../../t-sql/queries/select-transact-sql.md).  
  
<a name="permissions-bk"></a>  
  
## <a name="permissions"></a>Permissions  
Требуется CTAS `SELECT` разрешений на любые объекты, на которые ссылается *select_criteria*.

Разрешения на создание таблицы в разделе [разрешений](https://msdn.microsoft.com/library/mt203953/#Permissions) в инструкции CREATE TABLE. 
  
<a name="general-remarks-bk"></a>
  
## <a name="general-remarks"></a>Общие замечания
Дополнительные сведения см. в разделе [Общие замечания](https://msdn.microsoft.com/library/mt203953/#GeneralRemarks) в инструкции CREATE TABLE.

<a name="limitations-bk"></a>

## <a name="limitations-and-restrictions"></a>Ограничения  
Хранилище данных SQL Azure выполняет еще не поддержки автоматическое создание или автоматическое обновление статистики.  Чтобы добиться наилучшей производительности запросов, очень важно для создания статистики для всех столбцов всех таблиц, после запуска CTAS, и после любой значительных изменений в данных. Дополнительные сведения см. в разделе [CREATE STATISTICS (Transact-SQL)](../../t-sql/statements/create-statistics-transact-sql.md).

[SET ROWCOUNT &#40; Transact-SQL &#41; ](../../t-sql/statements/set-rowcount-transact-sql.md) не влияет на CTAS. Чтобы достичь такое же поведение, используйте [в начало &#40; Transact-SQL &#41; ](../../t-sql/queries/top-transact-sql.md).  
 
Дополнительные сведения см. в разделе [ограничения](https://msdn.microsoft.com/library/mt203953/#LimitationsRestrictions) в инструкции CREATE TABLE.

<a name="locking-behavior-bk"></a>
  
## <a name="locking-behavior"></a>Режим блокировки  
 Дополнительные сведения см. в разделе [режим блокировки](https://msdn.microsoft.com/library/mt203953/#LockingBehavior) в инструкции CREATE TABLE.
 
<a name="performance-bk"></a>
 
 ## <a name="performance"></a>Производительность 

Для распределенных хэш таблицы Чтобы выбрать столбец иное распределение, чтобы добиться максимальной производительности для соединения и статистические вычисления можно использовать CTAS. При выборе другой дистрибутив столбец не является поставленной задачи, вы получите наилучшей производительности CTAS при указании один и тот же столбец распределения, так как это позволит избежать повторного распространения строк. 

Если создать таблицу с помощью CTAS и производительности не является фактором, можно указать `ROUND_ROBIN` во избежание необходимости выбрать столбец распределения.

Чтобы избежать перемещения данных в последующих запросах, можно указать `REPLICATE` за счет увеличения хранилища для загрузки полной копии таблицы на каждом вычислительном узле.  


<a name="examples-copy-table-bk"></a>

## <a name="examples-for-copying-a-table"></a>Примеры копирования таблицы

<a name="ctas-copy-table-bk"></a>

### <a name="a-use-ctas-to-copy-a-table"></a>A. Используйте CTAS, чтобы скопировать таблицу 
Применяется к: хранилище данных Azure SQL и параллельные хранилища данных

Возможно одно из наиболее распространенные способы применения `CTAS` является создание копии таблицы, можно изменить DDL. Например которые использовались при создании таблицы как `ROUND_ROBIN` и теперь хотите изменить его в таблицу, распределенных по столбцу, `CTAS` является изменение столбца распределения. `CTAS`может также использоваться для изменения типов секционирование, индексирование или столбца.

Предположим, что вы создали в этой таблице, с использованием типа распределения по умолчанию `ROUND_ROBIN` распределенных, так как столбец распределения не была указана в `CREATE TABLE`.

```sql
CREATE TABLE FactInternetSales
(
    ProductKey int NOT NULL,
    OrderDateKey int NOT NULL,
    DueDateKey int NOT NULL,
    ShipDateKey int NOT NULL,
    CustomerKey int NOT NULL,
    PromotionKey int NOT NULL,
    CurrencyKey int NOT NULL,
    SalesTerritoryKey int NOT NULL,
    SalesOrderNumber nvarchar(20) NOT NULL,
    SalesOrderLineNumber tinyint NOT NULL,
    RevisionNumber tinyint NOT NULL,
    OrderQuantity smallint NOT NULL,
    UnitPrice money NOT NULL,
    ExtendedAmount money NOT NULL,
    UnitPriceDiscountPct float NOT NULL,
    DiscountAmount float NOT NULL,
    ProductStandardCost money NOT NULL,
    TotalProductCost money NOT NULL,
    SalesAmount money NOT NULL,
    TaxAmt money NOT NULL,
    Freight money NOT NULL,
    CarrierTrackingNumber nvarchar(25),
    CustomerPONumber nvarchar(25)
);
```

Теперь необходимо создать новую копию этой таблицы в кластеризованном индексе, чтобы воспользоваться преимуществами производительность таблиц кластеризованный индекс columnstore. Также требуется распространить данной таблицей по ProductKey, так как планирование соединения по этому столбцу и требуется избежать перемещения данных во время соединения, в отношении ProductKey. Наконец необходимо также добавить секционирование по OrderDateKey, чтобы быстро старые данные можно удалить, удалив старые секции. Вот CTAS инструкцию, которая будет копировать вашей старой таблицы в новую таблицу.

```sql
CREATE TABLE FactInternetSales_new
WITH
(
    CLUSTERED COLUMNSTORE INDEX,
    DISTRIBUTION = HASH(ProductKey),
    PARTITION
    (
        OrderDateKey RANGE RIGHT FOR VALUES
        (
        20000101,20010101,20020101,20030101,20040101,20050101,20060101,20070101,20080101,20090101,
        20100101,20110101,20120101,20130101,20140101,20150101,20160101,20170101,20180101,20190101,
        20200101,20210101,20220101,20230101,20240101,20250101,20260101,20270101,20280101,20290101
        )
    )
)
AS SELECT * FROM FactInternetSales;
```

Наконец можно переименовать таблиц для переключения в новую таблицу и затем удалите старый таблицы.

```sql
RENAME OBJECT FactInternetSales TO FactInternetSales_old;
RENAME OBJECT FactInternetSales_new TO FactInternetSales;

DROP TABLE FactInternetSales_old;
```

<a name="examples-column-bk"></a>

## <a name="examples-for-column-options"></a>Примеры для параметры столбца

<a name="ctas-change-column-attributes-bk"></a>

### <a name="b-use-ctas-to-change-column-attributes"></a>Б. Используйте CTAS, чтобы изменить атрибуты столбцов 
Применяется к: хранилище данных Azure SQL и параллельные хранилища данных

Этот пример использует CTAS для изменения типов данных, допустимость значений NULL и параметры сортировки для нескольких столбцов в таблице DimCustomer2.  
  
```  
-- Original table 
CREATE TABLE [dbo].[DimCustomer2] (  
    [CustomerKey] int NOT NULL,  
    [GeographyKey] int NULL,  
    [CustomerAlternateKey] nvarchar(15) COLLATE SQL_Latin1_General_CP1_CI_AS NOT NULL  
)  
WITH (CLUSTERED COLUMNSTORE INDEX, DISTRIBUTION = HASH([CustomerKey]));  
  
-- CTAS example to change data types, nullability, and column collations  
CREATE TABLE test  
WITH (HEAP, DISTRIBUTION = ROUND_ROBIN)  
AS  
SELECT  
    CustomerKey AS CustomerKeyNoChange,  
    CustomerKey*1 AS CustomerKeyChangeNullable,  
    CAST(CustomerKey AS DECIMAL(10,2)) AS CustomerKeyChangeDataTypeNullable,  
    ISNULL(CAST(CustomerKey AS DECIMAL(10,2)),0) AS CustomerKeyChangeDataTypeNotNullable,  
    GeographyKey AS GeographyKeyNoChange,  
    ISNULL(GeographyKey,0) AS GeographyKeyChangeNotNullable,  
    CustomerAlternateKey AS CustomerAlternateKeyNoChange,  
    CASE WHEN CustomerAlternateKey = CustomerAlternateKey 
        THEN CustomerAlternateKey END AS CustomerAlternateKeyNullable,  
    CustomerAlternateKey COLLATE Latin1_General_CS_AS_KS_WS AS CustomerAlternateKeyChangeCollation  
FROM [dbo].[DimCustomer2]  
  
-- Resulting table 
CREATE TABLE [dbo].[test] (
    [CustomerKeyNoChange] int NOT NULL, 
    [CustomerKeyChangeNullable] int NULL, 
    [CustomerKeyChangeDataTypeNullable] decimal(10, 2) NULL, 
    [CustomerKeyChangeDataTypeNotNullable] decimal(10, 2) NOT NULL, 
    [GeographyKeyNoChange] int NULL, 
    [GeographyKeyChangeNotNullable] int NOT NULL, 
    [CustomerAlternateKeyNoChange] nvarchar(15) COLLATE SQL_Latin1_General_CP1_CI_AS NOT NULL, 
    [CustomerAlternateKeyNullable] nvarchar(15) COLLATE SQL_Latin1_General_CP1_CI_AS NULL, 
    [CustomerAlternateKeyChangeCollation] nvarchar(15) COLLATE Latin1_General_CS_AS_KS_WS NOT NULL
)
WITH (DISTRIBUTION = ROUND_ROBIN);
```
 
В качестве последнего шага, можно использовать [ПЕРЕИМЕНОВАТЬ &#40; Transact-SQL &#41; ](../../t-sql/statements/rename-transact-sql.md) переключение имена таблиц. Это делает DimCustomer2 быть новую таблицу.

```
RENAME OBJECT DimCustomer2 TO DimCustomer2_old;
RENAME OBJECT test TO DimCustomer2;

DROP TABLE DimCustomer2_old;
```

<a name="examples-table-distribution-bk"></a>

## <a name="examples-for-table-distribution"></a>Примеры для распределения таблиц

<a name="ctas-change-distribution-method-bk"></a>

### <a name="c-use-ctas-to-change-the-distribution-method-for-a-table"></a>В. Используйте CTAS, чтобы изменить метод распределения для таблицы
Применяется к: хранилище данных Azure SQL и параллельные хранилища данных

Этот простой пример показано, как изменение метода распространения для таблицы. Чтобы отобразить механизм, позволяющий как это сделать, изменяется распределенных хэш таблицы для циклического и изменения таблицы циклического распределенных хэш. Последняя таблица совпадает с исходной таблицы. 

В большинстве случаев не нужно будет преобразовать в таблицу циклического распределенных хэш таблицы. Более часто может потребоваться изменение таблицы циклический перебор в хэш-таблицу распределенной. Например может сначала загрузить новые таблицы в качестве циклического и переместите его в таблицу распределенных хэш получить более высокую производительность соединения позже.

В этом примере используется образец базы данных AdventureWorksDW. Чтобы загрузить версию хранилища данных SQL, см. [загрузить образцы данных в хранилище данных SQL](https://azure.microsoft.com/documentation/articles/sql-data-warehouse-load-sample-databases/)
 
```
-- DimSalesTerritory is hash-distributed.
-- Copy it to a round-robin table.
CREATE TABLE [dbo].[myTable]   
WITH   
  (   
    CLUSTERED COLUMNSTORE INDEX,  
    DISTRIBUTION = ROUND_ROBIN  
  )  
AS SELECT * FROM [dbo].[DimSalesTerritory]; 

-- Switch table names

RENAME OBJECT [dbo].[DimSalesTerritory] to [DimSalesTerritory_old];
RENAME OBJECT [dbo].[myTable] TO [DimSalesTerritory];

DROP TABLE [dbo].[DimSalesTerritory_old];

```  
Затем измените его обратно в распределенной хэш-таблицу.

```
-- You just made DimSalesTerritory a round-robin table.
-- Change it back to the original hash-distributed table. 
CREATE TABLE [dbo].[myTable]   
WITH   
  (   
    CLUSTERED COLUMNSTORE INDEX,  
    DISTRIBUTION = HASH(SalesTerritoryKey) 
  )  
AS SELECT * FROM [dbo].[DimSalesTerritory]; 

-- Switch table names

RENAME OBJECT [dbo].[DimSalesTerritory] to [DimSalesTerritory_old];
RENAME OBJECT [dbo].[myTable] TO [DimSalesTerritory];

DROP TABLE [dbo].[DimSalesTerritory_old];
```
 
<a name="ctas-change-to-replicated-bk"></a>

### <a name="d-use-ctas-to-convert-a-table-to-a-replicated-table"></a>Г. Используйте CTAS, чтобы преобразовать таблицу в реплицированную таблицу  
Применяется к: хранилище данных Azure SQL и параллельные хранилища данных 

В этом примере применяется для преобразования циклический перебор или распределенных хэш таблицы в реплицированную таблицу. Вступает в данном конкретном примере предыдущему методу изменения распространения тип один шаг дальше.  Поскольку DimSalesTerritory является измерением и скорее всего таблицу меньшего размера, можно создать повторно таблицу репликации, чтобы избежать перемещения данных при объединении с другими таблицами. 

```
-- DimSalesTerritory is hash-distributed.
-- Copy it to a replicated table.
CREATE TABLE [dbo].[myTable]   
WITH   
  (   
    CLUSTERED COLUMNSTORE INDEX,  
    DISTRIBUTION = REPLICATE 
  )  
AS SELECT * FROM [dbo].[DimSalesTerritory]; 

-- Switch table names

RENAME OBJECT [dbo].[DimSalesTerritory] to [DimSalesTerritory_old];
RENAME OBJECT [dbo].[myTable] TO [DimSalesTerritory];

DROP TABLE [dbo].[DimSalesTerritory_old];
```
 
### <a name="e-use-ctas-to-create-a-table-with-fewer-columns"></a>Д. Используйте CTAS, чтобы создать таблицу с меньшим количеством столбцов
Применяется к: хранилище данных Azure SQL и параллельные хранилища данных 

В следующем примере создается циклическое распределенных таблицу с именем `myTable (c, ln)`. Новая таблица содержит только два столбца. Он использует псевдонимы столбцов в инструкции SELECT для имена столбцов.  
  
```  
CREATE TABLE myTable  
WITH   
  (   
    CLUSTERED COLUMNSTORE INDEX,  
    DISTRIBUTION = ROUND_ROBIN  
  )  
AS SELECT CustomerKey AS c, LastName AS ln  
    FROM dimCustomer;  
  
```  

<a name="examples-query-hints-bk"></a>

## <a name="examples-for-query-hints"></a>Примеры указания запросов

<a name="ctas-query-hint-bk"></a>

### <a name="f-use-a-query-hint-with-create-table-as-select-ctas"></a>Е. USE подсказки в запросе с CREATE TABLE AS SELECT (CTAS)  
Применяется к: хранилище данных Azure SQL и параллельные хранилища данных
  
Этот запрос показан основной синтаксис для использования подсказки в запросе соединения с CTAS инструкции. После отправки запроса [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] применяется стратегии соединения хэш при формировании плана запроса для каждого отдельного распределения. Дополнительные сведения о запросе указание соединения хэш см. в разделе [предложение OPTION &#40; Transact-SQL &#41; ](../../t-sql/queries/option-clause-transact-sql.md).  
  
```  
CREATE TABLE dbo.FactInternetSalesNew  
WITH   
  (   
    CLUSTERED COLUMNSTORE INDEX,  
    DISTRIBUTION = ROUND_ROBIN   
  )  
AS SELECT T1.* FROM dbo.FactInternetSales T1 JOIN dbo.DimCustomer T2  
ON ( T1.CustomerKey = T2.CustomerKey )  
OPTION ( HASH JOIN );  
```  

<a name="examples-external-tables"></a>

## <a name="examples-for-external-tables"></a>Примеры для внешних таблиц

<a name="ctas-azure-blob-storage-bk"></a>

### <a name="g-use-ctas-to-import-data-from-azure-blob-storage"></a>Ж. Используйте CTAS для импорта данных из хранилища больших двоичных объектов Azure  
Применяется к: хранилище данных Azure SQL и параллельные хранилища данных  

Чтобы импортировать данные из внешней таблицы, воспользуйтесь CREATE TABLE AS SELECT для выбора из внешней таблицы. Синтаксис для выбора данных из внешней таблицы в [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] является таким же, как синтаксис для выбора данных из обычной таблицы.  
  
 В следующем примере определяется внешнюю таблицу данные в учетной записи хранения BLOB-объектов Azure. Затем используется CREATE TABLE AS SELECT для выбора из внешней таблицы. Это импортирует данные из файлов с разделителями текст хранилища BLOB-объектов Azure и сохраняет данные в новую [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] таблицы.  
  
```  
--Use your own processes to create the text-delimited files on Azure blob storage.  
--Create the external table called ClickStream.  
CREATE EXTERNAL TABLE ClickStreamExt (   
    url varchar(50),  
    event_date date,  
    user_IP varchar(50)  
)  
WITH (  
    LOCATION='/logs/clickstream/2015/',  
    DATA_SOURCE = MyAzureStorage,  
    FILE_FORMAT = TextFileFormat)  
;  
  
--Use CREATE TABLE AS SELECT to import the Azure blob storage data into a new   
--SQL Data Warehouse table called ClickStreamData  
CREATE TABLE ClickStreamData   
WITH  
  (  
    CLUSTERED COLUMNSTORE INDEX,  
    DISTRIBUTION = HASH (user_IP)  
  )  
AS SELECT * FROM ClickStreamExt  
;  
```  

<a name="ctas-import-Hadoop-bk"></a>
  
### <a name="h-use-ctas-to-import-hadoop-data-from-an-external-table"></a>З. Используйте CTAS для импорта данных Hadoop из внешней таблицы  
Область применения:[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
Чтобы импортировать данные из внешней таблицы, воспользуйтесь CREATE TABLE AS SELECT для выбора из внешней таблицы. Синтаксис для выбора данных из внешней таблицы в [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] является таким же, как синтаксис для выбора данных из обычной таблицы.  
  
 В следующем примере определяется внешней таблицы в кластере Hadoop. Затем используется CREATE TABLE AS SELECT для выбора из внешней таблицы. Это импортирует данные из файлов, разделенных текстом Hadoop и сохраняет данные в новую [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] таблицы.  
  
```  
-- Create the external table called ClickStream.  
CREATE EXTERNAL TABLE ClickStreamExt (   
    url varchar(50),  
    event_date date,  
    user_IP varchar(50)  
)  
WITH (  
    LOCATION = 'hdfs://MyHadoop:5000/tpch1GB/employee.tbl',  
    FORMAT_OPTIONS ( FIELD_TERMINATOR = '|')  
)  
;  
  
-- Use your own processes to create the Hadoop text-delimited files 
-- on the Hadoop Cluster.  
  
-- Use CREATE TABLE AS SELECT to import the Hadoop data into a new 
-- table called ClickStreamPDW  
CREATE TABLE ClickStreamPDW   
WITH  
  (  
    CLUSTERED COLUMNSTORE INDEX,  
    DISTRIBUTION = HASH (user_IP)  
  )  
AS SELECT * FROM ClickStreamExt  
;   
```  
 
<a name="examples-workarounds-bk"></a>
 
## <a name="examples-using-ctas-to-replace-sql-server-code"></a>Примеры использования CTAS для замены кода SQL Server

Используйте CTAS, чтобы обойти некоторые неподдерживаемые функции. Помимо возможности для запуска кода в хранилище данных, преобразование существующего кода для использования CTAS обычно повышает производительность. Это результат его полностью Параллелизованный проектирования. 

> [!NOTE]
> Попробуйте подумать «CTAS первый». Если вы считаете, что может решить проблему с помощью `CTAS` затем это обычно лучший способ найти подход — даже при создании дополнительных данных в результате.
>

<a name="ctas-replace-select-into-bk"></a>

### <a name="i-use-ctas-instead-of-selectinto"></a>И. Используйте CTAS вместо SELECT... В  
Применяется к: хранилище данных Azure SQL и параллельные хранилища данных

Обычно код SQL Server использует SELECT... INTO для заполнения таблицы с помощью результатов инструкции SELECT. Ниже приведен пример SQL Server, выберите... В инструкции.

```sql
SELECT *
INTO    #tmp_fct
FROM    [dbo].[FactInternetSales]
```

Этот синтаксис не поддерживается в хранилище данных SQL и параллельных хранилищ данных. В этом примере показано, как для перезаписи предыдущего SELECT... В инструкции, как инструкция CTAS. Можно выбрать любой из описанных в синтаксисе CTAS РАСПРОСТРАНЕНИЯ параметров. В этом примере используется метод распространения ROUND_ROBIN.

```sql
CREATE TABLE #tmp_fct
WITH
(
    DISTRIBUTION = ROUND_ROBIN
)
AS
SELECT  *
FROM    [dbo].[FactInternetSales]
;
```

<a name="ctas-replace-implicit-joins-bk"></a>

### <a name="j-use-ctas-and-implicit-joins-to-replace-ansi-joins-in-the-from-clause-of-an-update-statement"></a>К. Используйте CTAS и неявного соединения для замены соединения ANSI в `FROM` предложения `UPDATE` инструкции  
Применяется к: хранилище данных Azure SQL и параллельные хранилища данных  

Вы можете обнаружить, что у вас есть сложные обновление, которое соединяет более двух таблиц, объединенных с помощью присоединения синтаксис ANSI для выполнения инструкции UPDATE или DELETE.

Представьте, что было необходимо обновить в этой таблице:

```sql
CREATE TABLE [dbo].[AnnualCategorySales]
(   [EnglishProductCategoryName]    NVARCHAR(50)    NOT NULL
,   [CalendarYear]                  SMALLINT        NOT NULL
,   [TotalSalesAmount]              MONEY           NOT NULL
)
WITH
(
    DISTRIBUTION = ROUND_ROBIN
)
;
```

Исходный запрос может выглядел примерно так:

```sql
UPDATE  acs
SET     [TotalSalesAmount] = [fis].[TotalSalesAmount]
FROM    [dbo].[AnnualCategorySales]     AS acs
JOIN    (
        SELECT  [EnglishProductCategoryName]
        ,       [CalendarYear]
        ,       SUM([SalesAmount])              AS [TotalSalesAmount]
        FROM    [dbo].[FactInternetSales]       AS s
        JOIN    [dbo].[DimDate]                 AS d    ON s.[OrderDateKey]             = d.[DateKey]
        JOIN    [dbo].[DimProduct]              AS p    ON s.[ProductKey]               = p.[ProductKey]
        JOIN    [dbo].[DimProductSubCategory]   AS u    ON p.[ProductSubcategoryKey]    = u.[ProductSubcategoryKey]
        JOIN    [dbo].[DimProductCategory]      AS c    ON u.[ProductCategoryKey]       = c.[ProductCategoryKey]
        WHERE   [CalendarYear] = 2004
        GROUP BY
                [EnglishProductCategoryName]
        ,       [CalendarYear]
        ) AS fis
ON  [acs].[EnglishProductCategoryName]  = [fis].[EnglishProductCategoryName]
AND [acs].[CalendarYear]                = [fis].[CalendarYear]
;
```

Поскольку хранилище данных SQL не поддерживает ANSI соединения в `FROM` предложения `UPDATE` инструкции, без изменения ее слегка нельзя использовать этот код SQL Server через.

Можно использовать сочетание `CTAS` и неявное соединение для замены этого кода:

```sql
-- Create an interim table
CREATE TABLE CTAS_acs
WITH (DISTRIBUTION = ROUND_ROBIN)
AS
SELECT  ISNULL(CAST([EnglishProductCategoryName] AS NVARCHAR(50)),0)    AS [EnglishProductCategoryName]
,       ISNULL(CAST([CalendarYear] AS SMALLINT),0)                      AS [CalendarYear]
,       ISNULL(CAST(SUM([SalesAmount]) AS MONEY),0)                     AS [TotalSalesAmount]
FROM    [dbo].[FactInternetSales]       AS s
JOIN    [dbo].[DimDate]                 AS d    ON s.[OrderDateKey]             = d.[DateKey]
JOIN    [dbo].[DimProduct]              AS p    ON s.[ProductKey]               = p.[ProductKey]
JOIN    [dbo].[DimProductSubCategory]   AS u    ON p.[ProductSubcategoryKey]    = u.[ProductSubcategoryKey]
JOIN    [dbo].[DimProductCategory]      AS c    ON u.[ProductCategoryKey]       = c.[ProductCategoryKey]
WHERE   [CalendarYear] = 2004
GROUP BY
        [EnglishProductCategoryName]
,       [CalendarYear]
;

-- Use an implicit join to perform the update
UPDATE  AnnualCategorySales
SET     AnnualCategorySales.TotalSalesAmount = CTAS_ACS.TotalSalesAmount
FROM    CTAS_acs
WHERE   CTAS_acs.[EnglishProductCategoryName] = AnnualCategorySales.[EnglishProductCategoryName]
AND     CTAS_acs.[CalendarYear]               = AnnualCategorySales.[CalendarYear]
;

--Drop the interim table
DROP TABLE CTAS_acs
;
```

<a name="ctas-replace-ansi-joins-bk"></a>

### <a name="k-use-ctas-to-specify-which-data-to-keep-instead-of-using-ansi-joins-in-the-from-clause-of-a-delete-statement"></a>Л. Используйте CTAS, чтобы указать, какие данные следует хранить вместо ANSI соединения в предложении FROM инструкции DELETE  
Применяется к: хранилище данных Azure SQL и параллельные хранилища данных  

Иногда для удаления данных, лучше использовать `CTAS`. Вместо удаления данных, просто выберите данные, которые требуется сохранить. Это особенно верно для `DELETE` инструкции, которые используют соединения присоединяемый синтаксиса, так как хранилище данных SQL не поддерживает ANSI в ansi `FROM` предложения `DELETE` инструкции.

Пример инструкции DELETE преобразованный приведен ниже:

```sql
CREATE TABLE dbo.DimProduct_upsert
WITH
(   Distribution=HASH(ProductKey)
,   CLUSTERED INDEX (ProductKey)
)
AS -- Select Data you wish to keep
SELECT     p.ProductKey
,          p.EnglishProductName
,          p.Color
FROM       dbo.DimProduct p
RIGHT JOIN dbo.stg_DimProduct s
ON         p.ProductKey = s.ProductKey
;

RENAME OBJECT dbo.DimProduct        TO DimProduct_old;
RENAME OBJECT dbo.DimProduct_upsert TO DimProduct;
```

<a name="ctas-simplify-merge-bk"></a>

### <a name="l-use-ctas-to-simplify-merge-statements"></a>М. Использовать CTAS для упрощения инструкций merge  
Применяется к: хранилище данных Azure SQL и параллельные хранилища данных  

Операторы объединения может быть заменен, по крайней мере в части с помощью `CTAS`. Можно консолидировать `INSERT` и `UPDATE` в один оператор. Удаленные записи потребуется закрыть в еще одну инструкцию.

Пример `UPSERT` приведен ниже:

```sql
CREATE TABLE dbo.[DimProduct_upsert]
WITH
(   DISTRIBUTION = HASH([ProductKey])
,   CLUSTERED INDEX ([ProductKey])
)
AS
-- New rows and new versions of rows
SELECT      s.[ProductKey]
,           s.[EnglishProductName]
,           s.[Color]
FROM      dbo.[stg_DimProduct] AS s
UNION ALL  
-- Keep rows that are not being touched
SELECT      p.[ProductKey]
,           p.[EnglishProductName]
,           p.[Color]
FROM      dbo.[DimProduct] AS p
WHERE NOT EXISTS
(   SELECT  *
    FROM    [dbo].[stg_DimProduct] s
    WHERE   s.[ProductKey] = p.[ProductKey]
)
;

RENAME OBJECT dbo.[DimProduct]          TO [DimProduct_old];
RENAME OBJECT dbo.[DimpProduct_upsert]  TO [DimProduct];

```

<a name="ctas-data-type-and-nullability-bk"></a>

### <a name="m-explicitly-state-data-type-and-nullability-of-output"></a>Н. Явным образом определить тип данных и допустимость значений NULL для выходных данных  
Применяется к: хранилище данных Azure SQL и параллельные хранилища данных  

При переносе кода SQL Server в хранилище данных SQL, возможно, выполняется на нескольких этот тип шаблона кодирования:

```sql
DECLARE @d decimal(7,2) = 85.455
,       @f float(24)    = 85.455

CREATE TABLE result
(result DECIMAL(7,2) NOT NULL
)
WITH (DISTRIBUTION = ROUND_ROBIN)

INSERT INTO result
SELECT @d*@f
;
```

Instinctively вы думаете, этот код следует перенести в CTAS, и они будут правильно. Тем не менее существует проблема скрытые здесь.

Следующий код не дает тот же результат:

```sql
DECLARE @d decimal(7,2) = 85.455
,       @f float(24)    = 85.455
;

CREATE TABLE ctas_r
WITH (DISTRIBUTION = ROUND_ROBIN)
AS
SELECT @d*@f as result
;
```

Обратите внимание, столбец «результат» вперед содержит тип и допустимость значений NULL значения данных выражения. Это может привести к незначительные различия в значения, следует соблюдать осторожность.

Попробуйте сделать следующее в качестве примера:

```sql
SELECT result,result*@d
from result
;

SELECT result,result*@d
from ctas_r
;
```

Значение, сохраненное для результата отличается. Сохраненное значение в столбце результатов используется в других выражениях становится еще более значительные ошибки.

![CREATE TABLE AS SELECT результатов](../../t-sql/statements/media/create-table-as-select-results.png)

Это особенно важно для миграции данных. Несмотря на то, что второй запрос пожалуй точнее имеется проблема. Данные будут содержать разные по сравнению с исходной системы и это ведет к вопросы целостности в процессе переноса. Это одна из этих редких случаях, когда ответ «неправильный» фактически нужную!

Поэтому мы увидим это несоответствие между двумя результаты опускается до неявное приведение. В первом примере определяются определение столбца в таблице. При вставке строки происходит неявное преобразование типов. Во втором примере отсутствует неявное преобразование как выражение определяет тип данных столбца. Обратите внимание, что столбцов во втором примере определен как столбец допускает значения NULL, тогда как в первом примере есть не. При создании таблицы в столбец первый пример допустимость значений NULL явно определен. Во втором примере, он был только что оставлять выражения и по умолчанию это приведет к определением NULL.  

Для устранения этих проблем необходимо явно задать преобразование типов и допустимость значений NULL в `SELECT` часть `CTAS` инструкции. Невозможно установить эти свойства в части создания таблицы.

В приведенном ниже примере показано, как исправить код:

```sql
DECLARE @d decimal(7,2) = 85.455
,       @f float(24)    = 85.455

CREATE TABLE ctas_r
WITH (DISTRIBUTION = ROUND_ROBIN)
AS
SELECT ISNULL(CAST(@d*@f AS DECIMAL(7,2)),0) as result
```

Следует отметить следующее.
- CAST или CONVERT мог бы использоваться
- Функция ISNULL используется, чтобы обеспечить допустимость значений NULL не COALESCE
- Функция ISNULL является внешней функции
- Во второй части ISNULL является константой т. е. 0

> [!NOTE]
> Для поддержки значений NULL, чтобы правильно задать его крайне важно для использования `ISNULL` и не `COALESCE`. `COALESCE`не является детерминированной функции и поэтому результат выражения всегда будет иметь значения NULL. `ISNULL`отличается. Он является детерминированной. Поэтому при во второй части `ISNULL` функции является константой или литералом, то будет результирующее значение NOT NULL.

Этот совет не просто нужно, чтобы гарантировать целостность вычисления. Также важно для переключения секции таблицы. Представьте, что у вас есть в этой таблице определен как ваш фактов:

```sql
CREATE TABLE [dbo].[Sales]
(
    [date]      INT     NOT NULL
,   [product]   INT     NOT NULL
,   [store]     INT     NOT NULL
,   [quantity]  INT     NOT NULL
,   [price]     MONEY   NOT NULL
,   [amount]    MONEY   NOT NULL
)
WITH
(   DISTRIBUTION = HASH([product])
,   PARTITION   (   [date] RANGE RIGHT FOR VALUES
                    (20000101,20010101,20020101
                    ,20030101,20040101,20050101
                    )
                )
)
;
```

В поле значение то, вычисляемое выражение не является частью источника данных.

Для создания набора секционированных данных может потребоваться сделать это:

```sql
CREATE TABLE [dbo].[Sales_in]
WITH    
(   DISTRIBUTION = HASH([product])
,   PARTITION   (   [date] RANGE RIGHT FOR VALUES
                    (20000101,20010101
                    )
                )
)
AS
SELECT
    [date]    
,   [product]
,   [store]
,   [quantity]
,   [price]   
,   [quantity]*[price]  AS [amount]
FROM [stg].[source]
OPTION (LABEL = 'CTAS : Partition IN table : Create')
;
```

Запрос будет выполняться в полном порядке. Проблема возникает при попытке выполнить переключение секций. Определения таблиц не совпадают. Чтобы сделать соответствует CTAS определения таблиц необходимо изменить.

```sql
CREATE TABLE [dbo].[Sales_in]
WITH    
(   DISTRIBUTION = HASH([product])
,   PARTITION   (   [date] RANGE RIGHT FOR VALUES
                    (20000101,20010101
                    )
                )
)
AS
SELECT
    [date]    
,   [product]
,   [store]
,   [quantity]
,   [price]   
,   ISNULL(CAST([quantity]*[price] AS MONEY),0) AS [amount]
FROM [stg].[source]
OPTION (LABEL = 'CTAS : Partition IN table : Create');
```

Вы увидите таким образом, согласованности типов и поддержка свойства допустимости значений NULL на CTAS все же рекомендуется хорошо реконструирования. Он помогает поддерживать целостность в вычислениях и также гарантирует, что переключение секций невозможно.
 
## <a name="see-also"></a>См. также:  
 [CREATE EXTERNAL DATA SOURCE (Transact-SQL)](../../t-sql/statements/create-external-data-source-transact-sql.md)   
 [CREATE EXTERNAL FILE FORMAT (Transact-SQL)](../../t-sql/statements/create-external-file-format-transact-sql.md)   
 [CREATE EXTERNAL TABLE (Transact-SQL)](../../t-sql/statements/create-external-table-transact-sql.md)   
 [СОЗДАТЬ внешний TABLE AS SELECT &#40; Transact-SQL &#41;](../../t-sql/statements/create-external-table-as-select-transact-sql.md)   
 [СОЗДАТЬ ТАБЛИЦУ &#40; Хранилище данных Azure SQL &#41; ](../../t-sql/statements/create-table-azure-sql-data-warehouse.md) [Удалить ТАБЛИЦУ &#40; Transact-SQL &#41;](../../t-sql/statements/drop-table-transact-sql.md)   
 [Удалите ВНЕШНЮЮ ТАБЛИЦУ &#40; Transact-SQL &#41;](../../t-sql/statements/drop-external-table-transact-sql.md)   
 [ALTER TABLE (Transact-SQL)](../../t-sql/statements/alter-table-transact-sql.md)   
 [ALTER EXTERNAL TABLE &#40; Transact-SQL &#41;](http://msdn.microsoft.com/library/4ae1b23c-67f6-41d0-b614-7a8de914d145)  
  
  


