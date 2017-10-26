---
title: "Автоматическое форматирование выходных данных JSON в режиме AUTO (SQL Server) | Документация Майкрософт"
ms.custom:
- SQL2016_New_Updated
ms.date: 07/17/2017
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
manager: craigg
ms.workload: On Demand
ms.translationtype: HT
ms.sourcegitcommit: 9045ebe77cf2f60fecad22672f3f055d8c5fdff2
ms.openlocfilehash: 0a1219eb4dac8621ef678cf309ef36b4b039536b
ms.contentlocale: ru-ru
ms.lasthandoff: 07/31/2017

---
# <a name="format-json-output-automatically-with-auto-mode-sql-server"></a>Автоматическое форматирование выходных данных JSON в режиме AUTO (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

Для автоматического форматирования выходных данных предложения **FOR JSON** на основе структуры инструкции **SELECT** укажите параметр **AUTO**.  
  
При указании параметра **AUTO** формат выходных данных JSON определяется автоматически на основе порядка столбцов в списке SELECT и соответствующих им исходных таблиц. Этот формат изменить нельзя.
 
Кроме того, для управления выходными данными можно использовать параметр **PATH**.
-   Дополнительные сведения о параметре **PATH** см. в статье [Форматирование вложенных выходных данных JSON в режиме PATH (SQL Server)](../../relational-databases/json/format-nested-json-output-with-path-mode-sql-server.md).
-   Общие сведения об этих параметрах см. в статье [Форматирование результатов запроса как JSON с помощью предложения FOR JSON (SQL Server)](../../relational-databases/json/format-query-results-as-json-with-for-json-sql-server.md).

В запросе, где используется параметр **FOR JSON AUTO** , должно быть предложение **FROM** .  
  
Ниже приведены некоторые примеры предложения **FOR JSON** с параметром **AUTO** .  
  
## <a name="examples"></a>Примеры

### <a name="example-1"></a>Пример 1
 **Запрос**  
  
Если запрос ссылается только на одну таблицу, результаты предложения FOR JSON AUTO будут похожи на результаты предложения FOR JSON PATH. В этом случае FOR JSON AUTO не создает никакие вложенные объекты. Единственное отличие состоит в том, что FOR JSON AUTO выводит псевдонимы, разделенные точками, (например, `Info.MiddleName` в следующем примере) как ключи с точками, а не как вложенные объекты.  
  
```sql  
SELECT TOP 5   
       BusinessEntityID As Id,  
       FirstName, LastName,  
       Title As 'Info.Title',  
       MiddleName As 'Info.MiddleName'  
   FROM Person.Person  
   FOR JSON AUTO  
```  
  
 **Результат**  
  
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

### <a name="example-2"></a>Пример 2

**Запрос**  
  
При соединении таблиц столбцы в первой таблице создаются как свойства корневого объекта. Столбцы во второй таблице создаются как свойства вложенного объекта. В качестве имени вложенного массива используется имя таблицы или псевдоним второй таблицы (например, `D` в следующем примере).  
  
```sql  
SELECT TOP 2 SalesOrderNumber,  
        OrderDate,  
        UnitPrice,  
        OrderQty  
FROM Sales.SalesOrderHeader H  
   INNER JOIN Sales.SalesOrderDetail D  
     ON H.SalesOrderID = D.SalesOrderID  
FOR JSON AUTO   
```  
  
**Результат**  
  
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

### <a name="example-3"></a>Пример 3
 
**Запрос**  
Вместо использования FOR JSON AUTO можно вкладывать вложенный запрос FOR JSON PATH в инструкцию SELECT, как показано в следующем примере. В этом примере выводится тот же результат, что и в предыдущем.  
  
```sql  
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
  
**Результат**  
  
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

## <a name="learn-more-about-the-built-in-json-support-in-sql-server"></a>Дополнительные сведения о встроенной поддержке JSON в SQL Server  
Много определенных решений, варианты использования и рекомендации см. в [записях блога о встроенной поддержке JSON](http://blogs.msdn.com/b/sqlserverstorageengine/archive/tags/json/) (категории SQL Server и Azure SQL Database (База данных SQL Azure), автор — руководитель программ корпорации Майкрософт Йован Попович (Jovan Popovic)).

## <a name="see-also"></a>См. также:  
 [Предложение FOR (Transact-SQL)](../../t-sql/queries/select-for-clause-transact-sql.md)  

