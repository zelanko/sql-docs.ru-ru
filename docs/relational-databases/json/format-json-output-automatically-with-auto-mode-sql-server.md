---
title: Автоматическое форматирование выходных данных JSON в режиме AUTO
ms.date: 07/17/2017
ms.prod: sql
ms.reviewer: genemi
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- FOR JSON AUTO
ms.assetid: 178a2a4e-e0f6-49b9-9895-396956d3c7d9
author: jovanpop-msft
ms.author: jovanpop
ms.custom: seo-dt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 1472c05c2ac4a9308a0fc941ed706d155203ca03
ms.sourcegitcommit: 15fe0bbba963d011472cfbbc06d954d9dbf2d655
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/14/2019
ms.locfileid: "74095805"
---
# <a name="format-json-output-automatically-with-auto-mode-sql-server"></a>Автоматическое форматирование выходных данных JSON в режиме AUTO (SQL Server)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

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

## <a name="learn-more-about-json-in-sql-server-and-azure-sql-database"></a>Дополнительные сведения о JSON в SQL Server и базе данных SQL Azure  
  
### <a name="microsoft-videos"></a>Видео Майкрософт

Наглядные инструкции по встроенной поддержке JSON в SQL Server и базе данных SQL Azure см. в следующих видео.

-   [SQL Server 2016 and JSON Support](https://channel9.msdn.com/Shows/Data-Exposed/SQL-Server-2016-and-JSON-Support) (SQL Server 2016 и поддержка JSON)

-   [Using JSON in SQL Server 2016 and Azure SQL Database](https://channel9.msdn.com/Shows/Data-Exposed/Using-JSON-in-SQL-Server-2016-and-Azure-SQL-Database) (Использование JSON в SQL Server 2016 и базе данных SQL Azure)

-   [JSON as a bridge between NoSQL and relational worlds](https://channel9.msdn.com/events/DataDriven/SQLServer2016/JSON-as-a-bridge-betwen-NoSQL-and-relational-worlds) (JSON как мост между NoSQL и реляционными решениями)

## <a name="see-also"></a>См. также:  
 [Предложение FOR (Transact-SQL)](../../t-sql/queries/select-for-clause-transact-sql.md)  
