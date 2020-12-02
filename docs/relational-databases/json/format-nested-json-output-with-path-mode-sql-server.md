---
description: Форматирование вложенных выходных данных JSON в режиме PATH (SQL Server)
title: Форматирование вложенных выходных данных JSON в режиме PATH
ms.date: 06/03/2020
ms.prod: sql
ms.technology: ''
ms.topic: conceptual
ms.assetid: 032761b0-6358-42e4-b05c-dbfd663ac881
author: jovanpop-msft
ms.author: jovanpop
ms.reviewer: jroth
ms.custom: seo-dt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 8c091618be5e414faa15e200fc8b30230f793eaf
ms.sourcegitcommit: c5078791a07330a87a92abb19b791e950672e198
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96130242"
---
# <a name="format-nested-json-output-with-path-mode-sql-server"></a>Форматирование вложенных выходных данных JSON в режиме PATH (SQL Server)
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]

Чтобы сохранить полный контроль над выходными данными предложения **FOR JSON**, укажите параметр **PATH**.  
  
Режим **PATH** позволяет создавать объекты-оболочки и вкладывать сложные свойства друг в друга. Результаты форматируются в виде массива объектов JSON.  
  
Кроме того, можно использовать параметр **AUTO** для автоматического форматирования выходных данных на основе структуры инструкции **SELECT**.
 -   Дополнительные сведения о параметре **AUTO** см. в статье [Автоматическое форматирование выходных данных JSON в режиме AUTO](../../relational-databases/json/format-json-output-automatically-with-auto-mode-sql-server.md).
 -   Общие сведения об этих параметрах см. в статье [Форматирование результатов запроса как JSON с помощью предложения FOR JSON (SQL Server)](../../relational-databases/json/format-query-results-as-json-with-for-json-sql-server.md).
 
Ниже приведены некоторые примеры предложения **FOR JSON** с параметром **PATH** . Форматируйте вложенные результаты с помощью имен столбцов, разделенных точкой, или с помощью вложенных запросов, как показано в следующих примерах. По умолчанию значения NULL не включаются в выходные данные **FOR JSON**.  [Azure Data Studio](../../azure-data-studio/download-azure-data-studio.md) является рекомендуемым редактором запросов JSON, так как он позволяет выполнять автоматическое форматирование результатов JSON (как показано в этой статье) вместо отображения плоской строки.

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
SELECT TOP 2 H.SalesOrderNumber AS 'Order.Number',  
        H.OrderDate AS 'Order.Date',  
        D.UnitPrice AS 'Product.Price',  
        D.OrderQty AS 'Product.Quantity'  
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

## <a name="learn-more-about-json-in-sql-server-and-azure-sql-database"></a>Дополнительные сведения о JSON в SQL Server и базе данных SQL Azure  
  
### <a name="microsoft-videos"></a>Видео Майкрософт

Наглядные инструкции по встроенной поддержке JSON в SQL Server и базе данных SQL Azure см. в следующих видео.

-   [SQL Server 2016 and JSON Support](https://channel9.msdn.com/Shows/Data-Exposed/SQL-Server-2016-and-JSON-Support) (SQL Server 2016 и поддержка JSON)

-   [Using JSON in SQL Server 2016 and Azure SQL Database](https://channel9.msdn.com/Shows/Data-Exposed/Using-JSON-in-SQL-Server-2016-and-Azure-SQL-Database) (Использование JSON в SQL Server 2016 и базе данных SQL Azure)

-   [JSON as a bridge between NoSQL and relational worlds](https://channel9.msdn.com/events/DataDriven/SQLServer2016/JSON-as-a-bridge-betwen-NoSQL-and-relational-worlds) (JSON как мост между NoSQL и реляционными решениями)

## <a name="see-also"></a>См. также:  
 [Предложение FOR (Transact-SQL)](../../t-sql/queries/select-for-clause-transact-sql.md)  
