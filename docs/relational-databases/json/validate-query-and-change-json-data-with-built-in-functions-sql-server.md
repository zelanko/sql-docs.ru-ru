---
title: "Проверка, построение запросов и изменение данных JSON с помощью встроенных функций (SQL Server) | Документация Майкрософт"
ms.custom: 
ms.date: 07/17/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.component: json
ms.reviewer: 
ms.suite: sql
ms.technology:
- dbe-json
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- JSON, built-in functions
- functions (JSON)
ms.assetid: 6b6c7673-d818-4fa9-8708-b4ed79cb1b41
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: c6803992992cf2a62afe741df536c0fa87a5fe2d
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/03/2018
---
# <a name="validate-query-and-change-json-data-with-built-in-functions-sql-server"></a>Проверка, построение запросов и изменение данных JSON с помощью встроенных функций (SQL Server)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

Встроенная поддержка JSON включает следующие встроенные функции, кратко описанные в этой статье.  
  
-   [ISJSON](#ISJSON) проверяет наличие допустимых данных JSON в строке.  
  
-   [JSON_VALUE](#VALUE) извлекает скалярное значение из строки JSON.  
  
-   [JSON_QUERY](#QUERY) извлекает объект или массив из строки JSON.  
  
-   [JSON_MODIFY](#MODIFY) обновляет значение свойства в строке JSON и возвращает обновленную строку JSON.  
 
## <a name="json-text-for-the-examples-on-this-page"></a>Текст JSON для примеров на этой странице
Примеры, представленные на этой странице, используют следующий текст в формате JSON, который содержит сложный элемент.

```sql 
DECLARE @jsonInfo NVARCHAR(MAX)

SET @jsonInfo=N'{  
     "info":{    
       "type":1,  
       "address":{    
         "town":"Bristol",  
         "county":"Avon",  
         "country":"England"  
       },  
       "tags":["Sport", "Water polo"]  
    },  
    "type":"Basic"  
 }' 
``` 

##  <a name="ISJSON"></a> Проверка строки JSON с помощью функции ISJSON  
 Функция **ISJSON** проверяет наличие допустимых данных JSON в строке.  
  
В следующем примере возвращаются строки, в которых столбец `json_col` содержит допустимые данные JSON.  
  
```sql  
SELECT id, json_col
FROM tab1
WHERE ISJSON(json_col) > 0 
```  

Дополнительные сведения см. в разделе [ISJSON (Transact-SQL)](../../t-sql/functions/isjson-transact-sql.md).  
  
##  <a name="VALUE"></a> Для извлечения значения из строки JSON используется функция JSON_VALUE  
Функция **JSON_VALUE** извлекает скалярное значение из строки JSON.  
  
В следующем примере значение вложенного свойства JSON `town` извлекается в локальную переменную.  
  
```sql  
SET @town = JSON_VALUE(@jsonInfo, '$.info.address.town')  
```  
  
Дополнительные сведения см. в разделе [JSON_VALUE (Transact-SQL)](../../t-sql/functions/json-value-transact-sql.md).  
  
##  <a name="QUERY"></a> Для извлечения объекта или массива из строки JSON используется функция JSON_QUERY  
Функция **JSON_QUERY** извлекает объект или массив из строки JSON.  
 
В следующем примере показано, как можно вернуть фрагмент JSON в результатах запроса.  
  
```sql  
SELECT FirstName, LastName, JSON_QUERY(jsonInfo,'$.info.address') AS Address
FROM Person.Person
ORDER BY LastName
```  
  
Дополнительные сведения см. в разделе [JSON_QUERY (Transact-SQL)](../../t-sql/functions/json-query-transact-sql.md).  
  
##  <a name="JSONCompare"></a> Сравнение JSON_VALUE и JSON_QUERY  
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
  
## <a name="test-jsonvalue-and-jsonquery-with-the-adventureworks-sample-database"></a>Тестирование JSON_VALUE и JSON_QUERY на образце базы данных AdventureWorks  
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
  
##  <a name="MODIFY"></a> Обновление значений свойств в тексте JSON с помощью функции JSON_MODIFY  
Функция **JSON_MODIFY** изменяет значение свойства в строке JSON и возвращает обновленную строку JSON.  
  
В следующем примере показано изменение значения свойства JSON в переменной, содержащей JSON-данные.  
  
```sql  
SET @info = JSON_MODIFY(@jsonInfo, "$.info.address[0].town", 'London')    
```  
  
 Дополнительные сведения см. в разделе [JSON_MODIFY &#40;Transact-SQL&#41;](../../t-sql/functions/json-modify-transact-sql.md).  
  
## <a name="learn-more-about-json-in-sql-server-and-azure-sql-database"></a>Дополнительные сведения о JSON в SQL Server и базе данных SQL Azure  
  
### <a name="microsoft-blog-posts"></a>Публикации блога Майкрософт  
  
Конкретные решения, варианты использования и рекомендации см. в [записях блога](http://blogs.msdn.com/b/sqlserverstorageengine/archive/tags/json/) о встроенной поддержке JSON в SQL Server и базе данных SQL Azure.  

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
  
  
