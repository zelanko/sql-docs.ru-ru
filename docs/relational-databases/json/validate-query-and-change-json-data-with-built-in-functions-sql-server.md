---
title: "Проверка, построение запросов и изменение данных JSON с помощью встроенных функций (SQL Server) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "06/02/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-json"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "JSON, встроенные функции"
  - "функции (JSON)"
ms.assetid: 6b6c7673-d818-4fa9-8708-b4ed79cb1b41
caps.latest.revision: 21
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 19
---
# Проверка, построение запросов и изменение данных JSON с помощью встроенных функций (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Встроенная поддержка JSON включает следующие функции, описанные в этой статье.  
  
-   [ISJSON](#ISJSON) проверяет наличие допустимых данных JSON в строке.  
  
-   [JSON_VALUE](#VALUE) извлекает скалярное значение из строки JSON.  
  
-   [JSON_QUERY](#QUERY) извлекает объект или массив из строки JSON.  
  
-   [JSON_MODIFY](#MODIFY) обновляет значение свойства в строке JSON и возвращает обновленную строку JSON.  
  
##  <a name="ISJSON"></a> Проверка строки JSON с помощью функции ISJSON  
 Функция **ISJSON** проверяет наличие допустимых данных JSON в строке.  
  
 Следующий пример возвращает текст JSON, если столбец содержит допустимые данные JSON.  
  
```tsql  
SELECT id, json_col  
FROM tab1  
WHERE ISJSON(json_col) > 0  
```  
  
 Дополнительные сведения см. в разделе [ISJSON (Transact-SQL)](../../t-sql/functions/isjson-transact-sql.md).  
  
##  <a name="VALUE"></a> Для извлечения значения из строки JSON используется функция JSON_VALUE  
 Функция **JSON_VALUE** извлекает скалярное значение из строки JSON.  
  
 Следующий пример извлекает значение свойства JSON в локальную переменную.  
  
```tsql  
SET @town = JSON_VALUE(@jsonInfo, '$.info.address.town')  
```  
  
 Дополнительные сведения см. в разделе [JSON_VALUE (Transact-SQL)](../../t-sql/functions/json-value-transact-sql.md).  
  
##  <a name="QUERY"></a> Для извлечения объекта или массива из строки JSON используется функция JSON_QUERY  
 Функция **JSON_QUERY** извлекает объект или массив из строки JSON.  
  
 Рассмотрим следующие данные в формате JSON, которые содержат сложный элемент.  
  
```json  
DECLARE @jsonInfo VARCHAR(MAX)  
SET @jsonInfo = N'{  
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
  
 В следующем примере показано, как можно вернуть фрагмент JSON в результатах запроса.  
  
```tsql  
SELECT FirstName, LastName,   
       JSON_QUERY(jsonInfo, '$.info.address') AS Address  
FROM Person.Person  
ORDER BY LastName  
```  
  
 Дополнительные сведения см. в разделе [JSON_QUERY (Transact-SQL)](../../t-sql/functions/json-query-transact-sql.md).  
  
##  <a name="JSONCompare"></a> Сравнение JSON_VALUE и JSON_QUERY  
 Основное различие между **JSON_VALUE** и **JSON_QUERY** заключается в том, что **JSON_VALUE** возвращает скалярное значение, а **JSON_QUERY** возвращает объект или массив.  
  
 Рассмотрим следующий пример данных в формате JSON.  
  
```json  
{ "a": "[1,2]", "b": [1,2], "c": "hi" }  
```  
  
 В приведенном примере элементы "а" и "c" являются строковыми значениями, а элемент "b" — массивом. **JSON_VALUE** и **JSON_QUERY** возвращают следующие результаты:  
  
|Запрос|**JSON_VALUE** возвращает|**JSON_QUERY** возвращает|  
|-----------|-----------------------------|-----------------------------|  
|**$**|NULL или ошибка|`{ "a": "[1,2]", "b": [1,2], "c":"hi"}`|  
|**$.a**|[1,2]|NULL или ошибка|  
|**$.b**|NULL или ошибка|[1,2]|  
|**$.b [0]**|1|NULL или ошибка|  
|**$.c**|hi|NULL или ошибка|  
  
## Тестирование JSON_VALUE и JSON_QUERY на образце базы данных AdventureWorks  
 Чтобы проверить работу встроенных функций, описанных в этой статье, запустите следующие примеры. Они обращаются к базе данных AdventureWorks, которая содержит данные в формате JSON. Чтобы загрузить образец базы данных AdventureWorks, [щелкните здесь](http://www.microsoft.com/en-us/download/details.aspx?id=49502).  
  
 В следующих примерах столбец Info таблицы SalesOrder_json содержит текст в формате JSON.  
  
### Пример 1. Возвращение стандартных столбцов и данных JSON  
 Следующий запрос возвращает стандартные реляционные столбцы и значения из столбца JSON.  
  
```tsql  
SELECT SalesOrderNumber, OrderDate, Status, ShipDate, Status, AccountNumber, TotalDue,  
             JSON_QUERY(Info, '$.ShippingInfo') ShippingInfo,  
             JSON_QUERY(Info, '$.BillingInfo') BillingInfo,  
             JSON_VALUE(Info, '$.SalesPerson.Name') SalesPerson,  
             JSON_VALUE(Info, '$.ShippingInfo.City') City,  
             JSON_VALUE(Info, '$.Customer.Name') Customer,  
             JSON_QUERY(OrderItems, '$') OrderItems  
FROM Sales.SalesOrder_json  
WHERE ISJSON(Info) > 0  
  
```  
  
### Пример 2. Агрегирование и фильтрация значений JSON  
 Следующий запрос рассчитывает промежуточные итоги по имени клиента (хранятся в формате JSON) и состояние (хранится в обычном столбце). Затем результаты фильтруются по городу (в формате JSON) и OrderDate (в обычном столбце).  
  
```tsql  
SELECT JSON_VALUE(Info, '$.Customer.Name') AS Customer, Status, SUM(SubTotal) AS Total  
FROM Sales.SalesOrder_json  
WHERE TerritoryID = @territoryid  
AND JSON_VALUE(Info, '$.ShippingInfo.City') = @city  
AND OrderDate > '1/1/2015'  
GROUP BY JSON_VALUE(Info, '$.Customer.Name'), Status  
HAVING SUM(SubTotal) > 1000  
  
```  
  
##  <a name="MODIFY"></a> Обновление значений свойств в тексте JSON с помощью функции JSON_MODIFY  
 Функция **JSON_MODIFY** обновляет значение свойства в строке JSON и возвращает обновленную строку JSON.  
  
 В следующем примере показано, как изменить значение свойства в переменной, которая содержит данные в формате JSON.  
  
```tsql  
SET @info = JSON_MODIFY(@jsonInfo, "$.info.address[0].town", 'London')  
```  
  
 Дополнительные сведения см. в разделе [JSON_MODIFY (Transact-SQL)](../../t-sql/functions/json-modify-transact-sql.md).  
  
## Дополнительные сведения о встроенной поддержке JSON в SQL Server  
 [Публикации блога Йована Поповича (Jovan Popovic), руководителя программы Microsoft](http://blogs.msdn.com/b/sqlserverstorageengine/archive/tags/json/)  
  
## См. также:  
 [ISJSON (Transact-SQL)](../../t-sql/functions/isjson-transact-sql.md)   
 [JSON_VALUE (Transact-SQL)](../../t-sql/functions/json-value-transact-sql.md)   
 [JSON_QUERY (Transact-SQL)](../../t-sql/functions/json-query-transact-sql.md)   
 [JSON_MODIFY (Transact-SQL)](../../t-sql/functions/json-modify-transact-sql.md)   
 [Выражения пути JSON (SQL Server)](../../relational-databases/json/json-path-expressions-sql-server.md)  
  
  