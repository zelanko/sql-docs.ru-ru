---
title: "Оптимизация обработки JSON с помощью выполняющейся в памяти OLTP | Документация Майкрософт"
ms.custom: 
ms.date: 02/03/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-json
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d9c5adb1-3209-4186-bc10-8e41a26f5e57
caps.latest.revision: 3
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 4e0331c288665fd9f69444d0d14366dfa69a668f
ms.contentlocale: ru-ru
ms.lasthandoff: 04/11/2017

---
# <a name="optimize-json-processing-with-in-memory-oltp"></a>Оптимизация обработки JSON с помощью выполняющейся в памяти OLTP
[!INCLUDE[tsql-appliesto-ssvNxt-asdb-xxxx-xxx](../../includes/tsql-appliesto-ssvnxt-asdb-xxxx-xxx.md)]

База данных SQL Azure и SQL Server позволяют работать с текстами в формате JSON. Чтобы увеличить производительность запросов OLTP, которые обрабатывают данные JSON, вы можете хранить документы JSON в таблицах, оптимизированных для памяти, с помощью стандартных столбцов строкового типа (типа nvarchar).

## <a name="store-json-in-memory-optimized-tables"></a>Хранение документов JSON в таблицах, оптимизированных для памяти
В примере ниже показана таблица `Product`, оптимизированная для памяти, с двумя столбцами JSON — `Tags` и `Data`.

```sql
CREATE SCHEMA xtp;
GO
CREATE TABLE xtp.Product(
    ProductID int PRIMARY KEY NONCLUSTERED, --standard column
    Name nvarchar(400) NOT NULL, --standard column
    Price float, --standard column

    Tags nvarchar(400),--json stored in string column
    Data nvarchar(4000) --json stored in string column

) WITH (MEMORY_OPTIMIZED=ON);
```
Хранение данных JSON в таблицах, оптимизированных для памяти, повышает производительность запросов за счет доступа к данным в памяти в режиме без блокировки.

## <a name="optimize-json-with-additional-in-memory-features"></a>Оптимизация JSON с помощью дополнительных функций выполнения в памяти
Новые функции, доступные в базе данных SQL Azure и SQL Server, позволяют полностью интегрировать возможности JSON с существующими технологиями выполнения OLTP в памяти. Вы сможете выполнять следующее:
 - проверять структуру документов JSON, хранящихся в таблицах, оптимизированных для памяти, с помощью скомпилированных в собственном коде ограничений CHECK;
 - предоставлять строго типизированные значения, сохраненные в документах JSON, с помощью вычисляемых столбцов;
 - индексировать значения в документах JSON с помощью индексов, оптимизированных для памяти;
 - компилировать в собственном коде SQL-запросы, использующие значения из документов JSON или форматирующие результаты в виде текста JSON.

## <a name="validate-json-columns"></a>Проверка столбцов JSON
База данных SQL Azure и SQL Server позволяют добавлять скомпилированные в собственном коде ограничения CHECK, проверяющие содержимое документов JSON, которые хранятся в строковом столбце, как показано в примере ниже.

```sql
DROP TABLE IF EXISTS xtp.Product;
GO
CREATE TABLE xtp.Product(
    ProductID int PRIMARY KEY NONCLUSTERED,
    Name nvarchar(400) NOT NULL,
    Price float,

    Tags nvarchar(400)
            CONSTRAINT [Tags should be formatted as JSON]
                CHECK (ISJSON(Tags)=1),
    Data nvarchar(4000)

) WITH (MEMORY_OPTIMIZED=ON);
```

Скомпилированное в собственном коде ограничение CHECK можно добавить в существующие таблицы, содержащие столбцы JSON.

```sql
ALTER TABLE xtp.Product
    ADD CONSTRAINT [Data should be JSON]
        CHECK (ISJSON(Data)=1)
```

Благодаря скомпилированным в собственном коде проверочным ограничениям JSON тексты JSON хранятся в таблицах, оптимизированных для памяти, в правильном формате.

## <a name="expose-json-values-using-computed-columns"></a>Предоставление значений JSON с помощью вычисляемых столбцов
С помощью вычисляемых столбцов можно предоставлять значения из текста JSON, а также получать доступ к этим значениям без переоценки выражений, извлекающих значение из текста JSON, и без повторного анализа структуры JSON. Предоставленные значения являются строго типизированными и физически материализованы в вычисляемых столбцах. Доступ к значениям JSON с помощью материализованных вычисляемых столбцов выполняется быстрее, чем доступ к значениям в документе JSON.

В примере ниже показано, как предоставить следующие два значения из столбца JSON `Data`:
-   страну, в которой был изготовлен товар;
-   себестоимость производства товара.

```sql
DROP TABLE IF EXISTS xtp.Product;
GO
CREATE TABLE xtp.Product(
    ProductID int PRIMARY KEY NONCLUSTERED,
    Name nvarchar(400) NOT NULL,
    Price float,

    Data nvarchar(4000),

    MadeIn AS CAST(JSON_VALUE(Data, '$.MadeIn') as NVARCHAR(50)) PERSISTED,
    Cost   AS CAST(JSON_VALUE(Data, '$.ManufacturingCost') as float)

) WITH (MEMORY_OPTIMIZED=ON);
```

Вычисляемые столбцы `MadeIn` и `Cost` обновляются каждый раз, когда изменяется документ JSON, сохраненный в столбце `Data`.

## <a name="index-values-in-json-columns"></a>Индексирование значений в столбцах JSON
База данных SQL Azure и SQL Server позволяют индексировать значения в столбцах JSON с помощью оптимизированных для памяти индексов. Индексированные значения JSON должны быть строго типизированными и предоставленными с помощью вычисляемых столбцов, как показано в примере ниже.

```sql
DROP TABLE IF EXISTS xtp.Product;
GO
CREATE TABLE xtp.Product(
    ProductID int PRIMARY KEY NONCLUSTERED,
    Name nvarchar(400) NOT NULL,
    Price float,

    Data nvarchar(4000),

    MadeIn AS CAST(JSON_VALUE(Data, '$.MadeIn') as NVARCHAR(50)) PERSISTED,
    Cost   AS CAST(JSON_VALUE(Data, '$.ManufacturingCost') as float) PERSISTED,

    INDEX [idx_Product_MadeIn] NONCLUSTERED (MadeIn)

) WITH (MEMORY_OPTIMIZED=ON)

ALTER TABLE Product
    ADD INDEX [idx_Product_Cost] NONCLUSTERED HASH(Cost)
        WITH (BUCKET_COUNT=20000)
```
Значения в столбцах JSON можно индексировать с помощью двух стандартных индексов — некластеризованного и хеш-индекса.
-   Некластеризованные индексы оптимизируют запросы, которые выбирают диапазоны строк по какому-либо значению JSON или сортируют результаты по значениям JSON.
-   Хэш-индексы обеспечивают оптимальную производительность, позволяя извлечь одну строку или ряд по точному поисковому запросу.

## <a name="native-compilation-of-json-queries"></a>Компиляция запросов JSON в собственном коде
Наконец, компиляция в собственном коде процедур функций и триггеров Transact-SQL, которые содержат запросы с функциями JSON, повышает производительность запросов и понижает циклы ЦП, необходимые для выполнения процедур. В примере ниже показана скомпилированная в собственном коде процедура, использующая несколько функций JSON — JSON_VALUE, OPENJSON и JSON_MODIFY.

```sql
CREATE PROCEDURE xtp.ProductList(@ProductIds nvarchar(100))
WITH SCHEMABINDING, NATIVE_COMPILATION
AS BEGIN
    ATOMIC WITH (transaction isolation level = snapshot,  language = N'English')

    SELECT ProductID,Name,Price,Data,Tags, JSON_VALUE(data,'$.MadeIn') AS MadeIn
    FROM xtp.Product
        JOIN OPENJSON(@ProductIds)
            ON ProductID = value

END;

CREATE PROCEDURE xtp.UpdateProductData(@ProductId int, @Property nvarchar(100), @Value nvarchar(100))
WITH SCHEMABINDING, NATIVE_COMPILATION
AS BEGIN
    ATOMIC WITH (transaction isolation level = snapshot,  language = N'English')

    UPDATE xtp.Product
    SET Data = JSON_MODIFY(Data, @Property, @Value)
    WHERE ProductID = @ProductId;

END
```

## <a name="next-steps"></a>Следующие шаги
JSON в собственных модулях выполняющейся в памяти OLTP улучшает производительность встроенных функциональных возможностей JSON, доступных в базе данных SQL Azure и SQL Server.

Чтобы получить дополнительные сведения об основных сценариях использования JSON, ознакомьтесь со следующими ресурсами:

-   [Блог SQL Server](https://blogs.technet.microsoft.com/dataplatforminsider/2016/01/05/json-in-sql-server-2016-part-1-of-4/)
-   [Данные JSON (SQL Server)](https://msdn.microsoft.com/library/dn921897.aspx)
-   [SQL Server 2016 и поддержка JSON](https://channel9.msdn.com/Shows/Data-Exposed/SQL-Server-2016-and-JSON-Support)

Чтобы получить дополнительные сведения о различных сценариях интеграции JSON в приложение, ознакомьтесь с приведенными ниже ресурсами.
-   Просмотрите демонстрационный видеоматериал на [Channel 9](https://channel9.msdn.com/Events/DataDriven/SQLServer2016/JSON-as-a-bridge-betwen-NoSQL-and-relational-worlds).
-   Найдите подходящий сценарий в [записях блога о JSON](http://blogs.msdn.com/b/sqlserverstorageengine/archive/tags/json/).
-   Ознакомьтесь с примерами в нашем [репозитории GitHub](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/json/).


