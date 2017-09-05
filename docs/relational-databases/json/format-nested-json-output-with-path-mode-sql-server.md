---
title: "Форматирование вложенных выходных данных JSON в режиме PATH (SQL Server) | Документация Майкрософт"
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
ms.assetid: 032761b0-6358-42e4-b05c-dbfd663ac881
caps.latest.revision: 19
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.translationtype: HT
ms.sourcegitcommit: 9045ebe77cf2f60fecad22672f3f055d8c5fdff2
ms.openlocfilehash: 12dfc255364a410de1ad5c75f3abf38155d6d70f
ms.contentlocale: ru-ru
ms.lasthandoff: 07/31/2017

---
# <a name="format-nested-json-output-with-path-mode-sql-server"></a>Форматирование вложенных выходных данных JSON в режиме PATH (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

Чтобы сохранить полный контроль над выходными данными предложения **FOR JSON**, укажите параметр **PATH**.  
  
Режим**PATH** позволяет создавать объекты-оболочки и вкладывать сложные свойства друг в друга. Результаты форматируются в виде массива объектов JSON.  
  
Кроме того, можно использовать параметр **AUTO** для автоматического форматирования выходных данных на основе структуры инструкции **SELECT**.
 -   Дополнительные сведения о параметре **AUTO** см. в статье [Автоматическое форматирование выходных данных JSON в режиме AUTO](../../relational-databases/json/format-json-output-automatically-with-auto-mode-sql-server.md).
 -   Общие сведения об этих параметрах см. в статье [Форматирование результатов запроса как JSON с помощью предложения FOR JSON (SQL Server)](../../relational-databases/json/format-query-results-as-json-with-for-json-sql-server.md).
 
Ниже приведены некоторые примеры предложения **FOR JSON** с параметром **PATH** . Форматируйте вложенные результаты с помощью имен столбцов, разделенных точкой, или с помощью вложенных запросов, как показано в следующих примерах. По умолчанию значения NULL не включаются в выходные данные **FOR JSON**.  

## <a name="example---dot-separated-column-names"></a>Пример. Имена столбцов, разделенные точкой  
В приведенном ниже запросе первые пять строк из таблицы AdventureWorks `Person` форматируются как JSON.  

Предложение **FOR JSON PATH** использует псевдоним или имя столбца для определения имени ключа в выходных данных JSON. Если псевдоним содержит точки, параметр PATH создаст вложенные объекты.  

 **Запрос**  
  
```sql  
SELECT TOP 5   
       BusinessEntityID As Id,  
       FirstName, LastName,  
       Title As 'Info.Title',  
       MiddleName As 'Info.MiddleName'  
   FROM Person.Person  
   FOR JSON PATH   
```  
  
 **Результат**  
  
```json  
[{
    "Id": 1,
    "FirstName": "Ken",
    "LastName": "Sanchez",
    "Info": {
        "MiddleName": "J"
    }
}, {
    "Id": 2,
    "FirstName": "Terri",
    "LastName": "Duffy",
    "Info": {
        "MiddleName": "Lee"
    }
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
    "Info": {
        "Title": "Ms.",
        "MiddleName": "A"
    }
}]
```  
   
## <a name="example---multiple-tables"></a>Пример: несколько таблиц  
Если запрос ссылается на несколько таблиц, предложение **FOR JSON PATH** будет вкладывать каждый столбец по его псевдониму. Следующий запрос создает один запрос JSON для каждой пары (OrderHeader, OrderDetails), объединяемой в запросе. 
  
 **Запрос**  
  
```sql  
SELECT TOP 2 SalesOrderNumber AS 'Order.Number',  
        OrderDate AS 'Order.Date',  
        UnitPrice AS 'Product.Price',  
        OrderQty AS 'Product.Quantity'  
FROM Sales.SalesOrderHeader H  
   INNER JOIN Sales.SalesOrderDetail D  
     ON H.SalesOrderID = D.SalesOrderID  
FOR JSON PATH   
```  
  
 **Результат**  
  
```json  
[{
    "Order": {
        "Number": "SO43659",
        "Date": "2011-05-31T00:00:00"
    },
    "Product": {
        "Price": 2024.9940,
        "Quantity": 1
    }
}, {
    "Order": {
        "Number": "SO43659"
    },
    "Product": {
        "Price": 2024.9940
    }
}]
```  

## <a name="learn-more-about-the-built-in-json-support-in-sql-server"></a>Дополнительные сведения о встроенной поддержке JSON в SQL Server  
Много определенных решений, варианты использования и рекомендации см. в [записях блога о встроенной поддержке JSON](http://blogs.msdn.com/b/sqlserverstorageengine/archive/tags/json/) (категории SQL Server и Azure SQL Database (База данных SQL Azure), автор — руководитель программ корпорации Майкрософт Йован Попович (Jovan Popovic)).

## <a name="see-also"></a>См. также:  
 [Предложение FOR (Transact-SQL)](../../t-sql/queries/select-for-clause-transact-sql.md)  

