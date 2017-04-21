---
title: "Автоматическое форматирование выходных данных JSON в режиме AUTO (SQL Server) | Документация Майкрософт"
ms.custom:
- SQL2016_New_Updated
ms.date: 06/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-json
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- FOR JSON AUTO
ms.assetid: 178a2a4e-e0f6-49b9-9895-396956d3c7d9
caps.latest.revision: 17
author: douglaslMS
ms.author: douglasl
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 3a04977311f1f04171caa1de0d15373d0b3cdf15
ms.lasthandoff: 04/11/2017

---
# <a name="format-json-output-automatically-with-auto-mode-sql-server"></a>Автоматическое форматирование выходных данных JSON в режиме AUTO (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

Для автоматического форматирования выходных данных предложения **FOR JSON** на основе структуры инструкции **SELECT** укажите параметр **AUTO**.  
  
Благодаря параметру **AUTO** формат выходных данных JSON определяется автоматически на основе порядка столбцов в списке SELECT и соответствующих исходных таблиц. Этот формат изменить нельзя.
 
 Кроме того, для управления выходными данными можно использовать параметр **PATH**.
 -   Дополнительные сведения о параметре **PATH** см. в статье [Format Nested JSON Output with PATH Mode (SQL Server)](../../relational-databases/json/format-nested-json-output-with-path-mode-sql-server.md) (Форматирование вложенных выходных данных JSON в режиме PATH (SQL Server)).
 -   Общие сведения об этих параметрах см. в статье [Format Query Results as JSON with FOR JSON (SQL Server)](../../relational-databases/json/format-query-results-as-json-with-for-json-sql-server.md) (Форматирование результатов запроса как JSON с помощью предложения FOR JSON (SQL Server)).
  
 В запросе, где используется параметр **FOR JSON AUTO** , должно быть предложение **FROM** .  
  
 Ниже приведены некоторые примеры предложения **FOR JSON** с параметром **AUTO** .  
  
## <a name="examples"></a>Примеры  
 **Запрос 1**  
  
Если в запросе используется только одна таблица, результаты предложения FOR JSON AUTO будут аналогичны результатам предложения FOR JSON PATH. В этом случае FOR JSON AUTO не создает никакие вложенные объекты. Единственное отличие состоит в том, что FOR JSON AUTO выводит псевдонимы, разделенные точками, (например, `Info.MiddleName` в следующем примере) как ключи с точками, а не как вложенные объекты.  
  
```tsql  
SELECT TOP 5   
       BusinessEntityID As Id,  
       FirstName, LastName,  
       Title As 'Info.Title',  
       MiddleName As 'Info.MiddleName'  
   FROM Person.Person  
   FOR JSON AUTO  
```  
  
 **Результат 1**  
  
```json  
[{
    "Id": 1,
    "FirstName": "Ken",
    "LastName": "Sánchez",
    "Info.MiddleName": "J"
}, {
    "Id": 2,
    "FirstName": "Terri",
    "LastName": "Duffy",
    "Info.MiddleName": "Lee"
}, {
    "Id": 3,
    "FirstName": "Roberto",
    "LastName": "Tamburello"
}, {
    "Id": 4,
    "FirstName": "Rob",
    "LastName": "Walters"
}, {
    "Id": 5,
    "FirstName": "Gail",
    "LastName": "Erickson",
    "Info.Title": "Ms.",
    "Info.MiddleName": "A"
}]
```  
  
 **Запрос 2**  
  
 При соединении таблиц столбцы в первой таблице создаются как свойства корневого объекта. Столбцы во второй таблице создаются как свойства вложенного объекта. В качестве имени вложенного массива используется имя таблицы или псевдоним второй таблицы (например, `D` в следующем примере).  
  
```tsql  
SELECT TOP 2 SalesOrderNumber,  
        OrderDate,  
        UnitPrice,  
        OrderQty  
FROM Sales.SalesOrderHeader H  
   INNER JOIN Sales.SalesOrderDetail D  
     ON H.SalesOrderID = D.SalesOrderID  
FOR JSON AUTO   
```  
  
 **Результат 2**  
  
```json  
[{
    "SalesOrderNumber": "SO43659",
    "OrderDate": "2011-05-31T00:00:00",
    "D": [{
        "UnitPrice": 24.99,
        "OrderQty": 1
    }]
}, {
    "SalesOrderNumber": "SO43659",
    "D": [{
        "UnitPrice": 34.40
    }, {
        "UnitPrice": 134.24,
        "OrderQty": 5
    }]
}]
```  
 
 **Запрос 3**  
 Вместо использования FOR JSON AUTO можно вкладывать вложенный запрос FOR JSON PATH в инструкцию SELECT, как показано в следующем примере. В этом примере выводится тот же результат, что и в предыдущем.  
  
```tsql  
SELECT TOP 2  
    SalesOrderNumber,  
    OrderDate,  
    (SELECT UnitPrice, OrderQty  
      FROM Sales.SalesOrderDetail AS D  
      WHERE H.SalesOrderID = D.SalesOrderID  
     FOR JSON PATH) AS D  
FROM Sales.SalesOrderHeader AS H  
FOR JSON PATH  
```  
  
 **Результат 3**  
  
```json  
[{
    "SalesOrderNumber": "SO43659",
    "OrderDate": "2011-05-31T00:00:00",
    "D": [{
        "UnitPrice": 24.99,
        "OrderQty": 1
    }]
}, {
    "SalesOrderNumber": "SO4390",
    "D": [{
        "UnitPrice": 24.99
    }]
}]
```  
  
## <a name="see-also"></a>См. также:  
 [Предложение FOR (Transact-SQL)](../../t-sql/queries/select-for-clause-transact-sql.md)  
  
  

