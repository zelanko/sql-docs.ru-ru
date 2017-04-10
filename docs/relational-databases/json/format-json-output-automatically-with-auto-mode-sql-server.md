---
title: "Автоматическое форматирование выходных данных JSON в режиме AUTO (SQL Server) | Microsoft Docs"
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
  - "FOR JSON AUTO"
ms.assetid: 178a2a4e-e0f6-49b9-9895-396956d3c7d9
caps.latest.revision: 17
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 15
---
# Автоматическое форматирование выходных данных JSON в режиме AUTO (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Для автоматического форматирования выходных данных JSON на основе структуры инструкции **SELECT** укажите параметр **AUTO** с предложением **FOR JSON**.  
  
 Благодаря параметру **AUTO** формат выходных данных JSON определяется автоматически на основе порядка столбцов в списке SELECT и соответствующих исходных таблиц. Этот формат изменить нельзя.  
  
 В запросе, где используется параметр **FOR JSON AUTO**, должно быть предложение **FROM**.  
  
 Ниже приведены некоторые примеры предложения **FOR JSON** с параметром **AUTO**.  
  
## Примеры  
 **Запрос 1**  
  
 Если в запросе используется только одна таблица, результаты предложения FOR JSON AUTO будут аналогичны результатам предложения FOR JSON PATH. В этом случае FOR JSON AUTO не создает никакие вложенные объекты. Единственное отличие состоит в том, что псевдонимы, разделенные точками, генерируются как ключи с точками (т. е. FOR JSON AUTO не использует для форматирования псевдонимы столбцов).  
  
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
[  
      {"Id":1,"FirstName":"Ken","LastName":"Sánchez","Info.MiddleName":"J"},  
      {"Id":2,"FirstName":"Terri","LastName":"Duffy","Info.MiddleName":"Lee"},  
      {"Id":3,"FirstName":"Roberto","LastName":"Tamburello"},  
      {"Id":4,"FirstName":"Rob","LastName":"Walters"},  
      {"Id":5,"FirstName":"Gail","LastName":"Erickson","Info.Title":"Ms.","Info.MiddleName":"A"}  
]  
```  
  
 **Запрос 2**  
  
 При соединении таблиц столбцы в первой таблице создаются как свойства корневого объекта. Столбцы во второй таблице создаются как свойства вложенного объекта. В качестве имени вложенного массива используется имя таблицы или псевдоним второй таблицы.  
  
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
[  
  {  
       "SalesOrderNumber":"SO43659",  
        "OrderDate":"2011-05-31T00:00:00",  
        "D":[  
            {"UnitPrice":24.99, "OrderQty":1  }  
         ]  
  },  
  {  
       "SalesOrderNumber":"SO43659" ,  
       "D":[  
          { "UnitPrice":34.40  },  
          { "UnitPrice":134.24, "OrderQty":5 }  
        ]  
  }  
]  
  
```  
  
## Примеры — создание вложенных выходных данных JSON  
 Вместо того чтобы использовать предложение FOR JSON AUTO, можно записать в разделе SELECT основной части запроса вложенные запросы FOR JSON и добавить предложение FOR JSON PATH, как показано в следующих примерах.  
  
 **Запрос 1**  
  
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
  
 **Результат 1**  
  
```json  
[  
  {  
       "SalesOrderNumber":"SO43659",  
        "OrderDate":"2011-05-31T00:00:00",  
        "D":[  
            { "UnitPrice":24.99,  "OrderQty":1 }  
         ]  
  },  
  {  
       "SalesOrderNumber":"SO4390" ,  
       "D":[  
            { "UnitPrice":24.99 }  
        ]  
  }  
]  
  
```  
  
## См. также:  
 [Предложение FOR (Transact-SQL)](../Topic/FOR%20Clause%20\(Transact-SQL\).md)  
  
  