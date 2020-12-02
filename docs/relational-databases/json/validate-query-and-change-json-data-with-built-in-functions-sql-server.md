---
description: Проверка, построение запросов и изменение данных JSON с помощью встроенных функций (SQL Server)
title: Проверка, построение запросов и изменение данных JSON с помощью встроенных функций
ms.date: 06/03/2020
ms.prod: sql
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- JSON, built-in functions
- functions (JSON)
ms.assetid: 6b6c7673-d818-4fa9-8708-b4ed79cb1b41
author: jovanpop-msft
ms.author: jovanpop
ms.reviewer: jroth
ms.custom: seo-dt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 76644f677a03f34312e6731f5a973167313ad22a
ms.sourcegitcommit: c5078791a07330a87a92abb19b791e950672e198
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "88424096"
---
# <a name="validate-query-and-change-json-data-with-built-in-functions-sql-server"></a>Проверка, построение запросов и изменение данных JSON с помощью встроенных функций (SQL Server)
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]

Встроенная поддержка JSON включает следующие встроенные функции, кратко описанные в этой статье.  
  
-   [ISJSON](#ISJSON) проверяет наличие допустимых данных JSON в строке.  
  
-   [JSON_VALUE](#VALUE) извлекает скалярное значение из строки JSON.  
  
-   [JSON_QUERY](#QUERY) извлекает объект или массив из строки JSON.  
  
-   [JSON_MODIFY](#MODIFY) обновляет значение свойства в строке JSON и возвращает обновленную строку JSON.  
 
## <a name="json-text-for-the-examples-on-this-page"></a>Текст JSON для примеров на этой странице

В примерах на этой странице используется текст JSON, аналогичный содержимому в следующем примере:

```json
{
  "id": "WakefieldFamily",
  "parents": [
      { "familyName": "Wakefield", "givenName": "Robin" },
      { "familyName": "Miller", "givenName": "Ben" }
  ],
  "children": [
      {
        "familyName": "Merriam",
        "givenName": "Jesse",
        "gender": "female",
        "grade": 1,
        "pets": [
            { "givenName": "Goofy" },
            { "givenName": "Shadow" }
        ]
      },
      { 
        "familyName": "Miller",
         "givenName": "Lisa",
         "gender": "female",
         "grade": 8 }
  ],
  "address": { "state": "NY", "county": "Manhattan", "city": "NY" },
  "creationDate": 1431620462,
  "isRegistered": false
}
```

Этот документ JSON, содержащий вложенные сложные элементы, хранится в следующем образце таблицы:

```sql
CREATE TABLE Families (
   id int identity constraint PK_JSON_ID primary key,
   doc nvarchar(max)
)
``` 

##  <a name="validate-json-text-by-using-the-isjson-function"></a><a name="ISJSON"></a> Проверка строки JSON с помощью функции ISJSON  
 Функция **ISJSON** проверяет наличие допустимых данных JSON в строке.  
  
В приведенном ниже примере возвращаются строки, в которых столбец JSON содержит допустимый текст JSON. Обратите внимание, что без явного ограничения JSON в столбце NVARCHAR можно ввести любой текст:  
  
```sql  
SELECT *
FROM Families
WHERE ISJSON(doc) > 0 
```  

Дополнительные сведения см. в разделе [ISJSON (Transact-SQL)](../../t-sql/functions/isjson-transact-sql.md).  
  
##  <a name="extract-a-value-from-json-text-by-using-the-json_value-function"></a><a name="VALUE"></a> Для извлечения значения из строки JSON используется функция JSON_VALUE  
Функция **JSON_VALUE** извлекает скалярное значение из строки JSON. Следующий запрос вернет документы, в которых поле JSON `id` соответствует значению `AndersenFamily`, с упорядочением по полям JSON `city` и `state`:

```sql  
SELECT JSON_VALUE(f.doc, '$.id')  AS Name, 
       JSON_VALUE(f.doc, '$.address.city') AS City,
       JSON_VALUE(f.doc, '$.address.county') AS County
FROM Families f 
WHERE JSON_VALUE(f.doc, '$.id') = N'AndersenFamily'
ORDER BY JSON_VALUE(f.doc, '$.address.city') DESC, JSON_VALUE(f.doc, '$.address.state') ASC
```  

Результаты этого запроса показаны в приведенной ниже таблице.

| Имя | Город | Округ |
| --- | --- | --- |
| AndersenFamily | Нью-Йорк | Manhattan |

Дополнительные сведения см. в разделе [JSON_VALUE (Transact-SQL)](../../t-sql/functions/json-value-transact-sql.md).  
  
##  <a name="extract-an-object-or-an-array-from-json-text-by-using-the-json_query-function"></a><a name="QUERY"></a> Для извлечения объекта или массива из строки JSON используется функция JSON_QUERY  

Функция **JSON_QUERY** извлекает объект или массив из строки JSON. В следующем примере показано, как можно вернуть фрагмент JSON в результатах запроса.  
  
```sql
SELECT JSON_QUERY(f.doc, '$.address') AS Address,
       JSON_QUERY(f.doc, '$.parents') AS Parents,
       JSON_QUERY(f.doc, '$.parents[0]') AS Parent0
FROM Families f 
WHERE JSON_VALUE(f.doc, '$.id') = N'AndersenFamily'
```  
Результаты этого запроса показаны в приведенной ниже таблице.

| Адрес | Parents | Parent0 |
| --- | --- | --- |
| { "state": "NY", "county": "Manhattan", "city": "NY" } | [{ "familyName": "Wakefield", "givenName": "Robin" }, {"familyName": "Miller", "givenName": "Ben" } ]| { "familyName": "Wakefield", "givenName": "Robin" } |

Дополнительные сведения см. в разделе [JSON_QUERY (Transact-SQL)](../../t-sql/functions/json-query-transact-sql.md).  

## <a name="parse-nested-json-collections"></a>Анализ вложенных коллекций JSON

Функция `OPENJSON` позволяет преобразовать вложенный массив JSON в набор строк, а затем присоединить его к родительскому элементу. Например, можно вернуть все документы о семьях и присоединить их к объектам `children`, которые хранятся в виде внутреннего массива JSON:

```sql
SELECT JSON_VALUE(f.doc, '$.id')  AS Name, 
       JSON_VALUE(f.doc, '$.address.city') AS City,
       c.givenName, c.grade
FROM Families f
        CROSS APPLY OPENJSON(f.doc, '$.children')
            WITH(grade int, givenName nvarchar(100))  c
```

Результаты этого запроса показаны в приведенной ниже таблице.

| Имя | Город | givenName | grade |
| --- | --- | --- | --- |
| AndersenFamily | Нью-Йорк | Jesse | 1 |
| AndersenFamily | Нью-Йорк | Lisa | 8 |

В результате мы получаем две строки, так как одна родительская строка объединена с двумя дочерними строками, созданными путем анализа двух элементов дочернего подмассива. Функция `OPENJSON` анализирует фрагмент `children` из столбца `doc` и возвращает `grade` и `givenName` из каждого элемента в виде набора строк. Этот набор строк можно объединить с родительским документом.
 
## <a name="query-nested-hierarchical-json-sub-arrays"></a>Запрос вложенных иерархических подмассивов JSON

Вы можете использовать несколько вызовов `CROSS APPLY OPENJSON` для запроса вложенных структур JSON. В документе JSON, используемом в этом примере, есть вложенный массив с именем `children`, каждый дочерний элемент которого имеет вложенный массив `pets`. Следующий запрос будет анализировать дочерние элементы из каждого документа, возвращать каждый объект массива в виде строки, а затем анализировать массив `pets`:

```sql
SELECT  familyName,
    c.givenName AS childGivenName,
    c.firstName AS childFirstName,
    p.givenName AS petName 
FROM Families f 
    CROSS APPLY OPENJSON(f.doc) 
        WITH (familyName nvarchar(100), children nvarchar(max) AS JSON)
        CROSS APPLY OPENJSON(children) 
        WITH (givenName nvarchar(100), firstName nvarchar(100), pets nvarchar(max) AS JSON) as c
            OUTER APPLY OPENJSON (pets)
            WITH (givenName nvarchar(100))  as p
```

Первый вызов `OPENJSON` вернет фрагмент массива `children` с помощью предложения AS JSON. Этот фрагмент массива будет передан во вторую функцию `OPENJSON`, которая вернет `givenName`, `firstName` каждого дочернего элемента, а также массив `pets`. Массив `pets` будет передан в третью функцию `OPENJSON`, которая вернет значение `givenName` для домашнего животного.
Результаты этого запроса показаны в приведенной ниже таблице.

| familyName | childGivenName | childFirstName | petName |
| --- | --- | --- | --- |
| AndersenFamily | Jesse | Merriam | Goofy |
| AndersenFamily | Jesse | Merriam | Shadow |
| AndersenFamily | Lisa | Miller| `NULL` |

Корневой документ объединяется с двумя строками `children`, возвращаемыми при первом вызове `OPENJSON(children)`, в результате чего получаются две строки (или два кортежа). Затем каждая строка объединяется с новыми строками, созданными функцией `OPENJSON(pets)`, с помощью оператора `OUTER APPLY`. У Jesse два домашних животных, поэтому `(AndersenFamily, Jesse, Merriam)` объединяется с двумя строками, созданными для Goofy и Shadow. У Lisa нет домашних животных, поэтому функция `OPENJSON(pets)` не возвращает строк для этого кортежа. Однако, так как используется оператор `OUTER APPLY`, в столбце будет значение `NULL`. Если использовать `CROSS APPLY` вместо `OUTER APPLY`, Lisa не будет возвращаться в результатах из-за отсутствия строк домашних животных, которые можно было бы объединить с этим кортежем.

##  <a name="compare-json_value-and-json_query"></a><a name="JSONCompare"></a> Сравнение JSON_VALUE и JSON_QUERY  
Основное различие между **JSON_VALUE** и **JSON_QUERY** заключается в том, что **JSON_VALUE** возвращает скалярное значение, а **JSON_QUERY** возвращает объект или массив.  
  
Рассмотрим следующий пример данных в формате JSON.  
  
```json  
{
    "a": "[1,2]",
    "b": [1, 2],
    "c": "hi"
}  
```  
  
В приведенном примере элементы "а" и "c" являются строковыми значениями, а элемент "b" — массивом. **JSON_VALUE** и **JSON_QUERY** возвращают следующие результаты:  
  
|Путь|**JSON_VALUE** возвращает|**JSON_QUERY** возвращает|  
|-----------|-----------------------------|-----------------------------|  
|**$**|NULL или ошибка|`{ "a": "[1,2]", "b": [1,2], "c":"hi"}`|  
|**$.a**|[1,2]|NULL или ошибка|  
|**$.b**|NULL или ошибка|[1,2]|  
|**$.b [0]**|1|NULL или ошибка|  
|**$.c**|hi|NULL или ошибка|  
  
## <a name="test-json_value-and-json_query-with-the-adventureworks-sample-database"></a>Тестирование JSON_VALUE и JSON_QUERY на образце базы данных AdventureWorks  
Чтобы проверить работу встроенных функций, описанных в этой статье, запустите следующие примеры. Они обращаются к базе данных AdventureWorks. Сведения о получении AdventureWorks, а также о добавлении данных JSON для тестирования с помощью скрипта см. в разделе [Проверка встроенной поддержки JSON](json-data-sql-server.md#test-drive-built-in-json-support-with-the-adventureworks-sample-database).
  
В следующих примерах столбец `Info` таблицы `SalesOrder_json` содержит текст в формате JSON.  
  
### <a name="example-1---return-both-standard-columns-and-json-data"></a>Пример 1. Возвращение стандартных столбцов и данных JSON  
Следующий запрос возвращает значения и из стандартных реляционных столбцов, и из столбца JSON.  
  
```sql  
SELECT SalesOrderNumber, OrderDate, Status, ShipDate, Status, AccountNumber, TotalDue,
 JSON_QUERY(Info,'$.ShippingInfo') ShippingInfo,
 JSON_QUERY(Info,'$.BillingInfo') BillingInfo,
 JSON_VALUE(Info,'$.SalesPerson.Name') SalesPerson,
 JSON_VALUE(Info,'$.ShippingInfo.City') City,
 JSON_VALUE(Info,'$.Customer.Name') Customer,
 JSON_QUERY(OrderItems,'$') OrderItems
FROM Sales.SalesOrder_json
WHERE ISJSON(Info) > 0
```  
  
### <a name="example-2--aggregate-and-filter-json-values"></a>Пример 2. Агрегирование и фильтрация значений JSON  
Следующий запрос рассчитывает промежуточные итоги по имени клиента (хранятся в формате JSON) и состояние (хранится в обычном столбце). Затем результаты фильтруются по городу (в формате JSON) и по дате заказа OrderDate (в обычном столбце).  
  
```sql  
DECLARE @territoryid INT;
DECLARE @city NVARCHAR(32);

SET @territoryid=3;

SET @city=N'Seattle';

SELECT JSON_VALUE(Info, '$.Customer.Name') AS Customer, Status, SUM(SubTotal) AS Total
FROM Sales.SalesOrder_json
WHERE TerritoryID=@territoryid
 AND JSON_VALUE(Info, '$.ShippingInfo.City') = @city
 AND OrderDate > '1/1/2015'
GROUP BY JSON_VALUE(Info, '$.Customer.Name'), Status
HAVING SUM(SubTotal)>1000
```  
  
##  <a name="update-property-values-in-json-text-by-using-the-json_modify-function"></a><a name="MODIFY"></a> Обновление значений свойств в тексте JSON с помощью функции JSON_MODIFY  
Функция **JSON_MODIFY** изменяет значение свойства в строке JSON и возвращает обновленную строку JSON.  
  
В следующем примере показано изменение значения свойства JSON в переменной, содержащей JSON-данные.  
  
```sql  
SET @info = JSON_MODIFY(@jsonInfo, "$.info.address[0].town", 'London')    
```  
  
 Дополнительные сведения см. в разделе [JSON_MODIFY (Transact-SQL)](../../t-sql/functions/json-modify-transact-sql.md).  
  
## <a name="learn-more-about-json-in-sql-server-and-azure-sql-database"></a>Дополнительные сведения о JSON в SQL Server и базе данных SQL Azure  
  
### <a name="microsoft-videos"></a>Видео Майкрософт

Наглядные инструкции по встроенной поддержке JSON в SQL Server и базе данных SQL Azure см. в следующих видео.

-   [SQL Server 2016 and JSON Support](https://channel9.msdn.com/Shows/Data-Exposed/SQL-Server-2016-and-JSON-Support) (SQL Server 2016 и поддержка JSON)

-   [Using JSON in SQL Server 2016 and Azure SQL Database](https://channel9.msdn.com/Shows/Data-Exposed/Using-JSON-in-SQL-Server-2016-and-Azure-SQL-Database) (Использование JSON в SQL Server 2016 и базе данных SQL Azure)

-   [JSON as a bridge between NoSQL and relational worlds](https://channel9.msdn.com/events/DataDriven/SQLServer2016/JSON-as-a-bridge-betwen-NoSQL-and-relational-worlds) (JSON как мост между NoSQL и реляционными решениями)
  
## <a name="see-also"></a>См. также:  
 [ISJSON (Transact-SQL)](../../t-sql/functions/isjson-transact-sql.md)   
 [JSON_VALUE (Transact-SQL)](../../t-sql/functions/json-value-transact-sql.md)   
 [JSON_QUERY (Transact-SQL)](../../t-sql/functions/json-query-transact-sql.md)   
 [JSON_MODIFY (Transact-SQL)](../../t-sql/functions/json-modify-transact-sql.md)   
 [Выражения пути JSON (SQL Server)](../../relational-databases/json/json-path-expressions-sql-server.md)  
  
  
