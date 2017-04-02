---
title: "Форматирование вложенных выходных данных JSON в режиме PATH (SQL Server) | Microsoft Docs"
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
ms.assetid: 032761b0-6358-42e4-b05c-dbfd663ac881
caps.latest.revision: 19
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 16
---
# Форматирование вложенных выходных данных JSON в режиме PATH (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Чтобы сохранить полный контроль над форматом выходных данных JSON, используйте режим **PATH** с предложением **FOR JSON**.  
  
 Режим **PATH** позволяет создавать объекты-оболочки и вкладывать сложные свойства друг в друга. Результаты форматируются в виде массива объектов JSON.  
  
 Ниже приведены некоторые примеры предложения **FOR JSON** с параметром **PATH**. Форматируйте вложенные результаты с помощью имен столбцов, разделенных точкой, или с помощью вложенных запросов, как показано в следующих примерах. По умолчанию значения NULL не включаются в выходные данные.  
  
## Пример. Имена столбцов, разделенные точкой  
 В приведенном ниже запросе первые пять строк из таблицы AdventureWorks Person форматируются как JSON.  
  
 **Запрос**  
  
```tsql  
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
[  
    {"Id":1,"FirstName":"Ken","LastName":"Sánchez","Info":{"MiddleName":"J"}},  
    {"Id":2,"FirstName":"Terri","LastName":"Duffy","Info":{"MiddleName":"Lee"}},  
    {"Id":3,"FirstName":"Roberto","LastName":"Tamburello"},  
    {"Id":4,"FirstName":"Rob","LastName":"Walters"},  
    {"Id":5,"FirstName":"Gail","LastName":"Erickson","Info":{"Title":"Ms.","MiddleName":"A"}}  
]  
```  
  
 Предложение FOR JSON PATH будет использовать псевдоним или имя столбца для определения имени ключа в выходных данных JSON. Если псевдоним содержит точки, предложение FOR JSON PATH создаст вложенный объект. Обратите внимание на то, что для ячеек со значением NULL выходные данные создаваться не будут.  
  
## Пример: несколько таблиц  
 Если запрос ссылается на несколько таблиц, результаты представляются в виде плоского списка, а затем предложение FOR JSON PATH вкладывает каждый столбец по его псевдониму. Следующий запрос создает один запрос JSON для каждой пары (OrderHeader,OrderDetails), объединяемой в запросе:  
  
 **Запрос**  
  
```tsql  
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
[  
  {  
    "Order":{  
        "Number":"SO43659",  
        "Date":"2011-05-31T00:00:00"  
      },  
    "Product":{  
         "Price":2024.9940,  
         "Quantity":1  
     }  
  },  
  {  
    "Order":{ "Number":"SO43659“ },  
    "Product":{"Price":2024.9940}  
  }  
]  
```  
  
## См. также:  
 [Предложение FOR (Transact-SQL)](../Topic/FOR%20Clause%20\(Transact-SQL\).md)  
  
  