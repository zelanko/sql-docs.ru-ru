---
title: "Удаление квадратных скобок из выходных данных JSON с помощью параметра WITHOUT_ARRAY_WRAPPER (SQL Server) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/23/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-json"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "WITHOUT_ARRAY_WRAPPER"
ms.assetid: aa86c2d1-458e-465f-abfa-75470137d054
caps.latest.revision: 11
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
---
# Удаление квадратных скобок из выходных данных JSON с помощью параметра WITHOUT_ARRAY_WRAPPER (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Чтобы удалить квадратные скобки, в которые выходные данные JSON предложения **FOR JSON** заключаются по умолчанию, укажите параметр **WITHOUT_ARRAY_WRAPPER**. Этот параметр позволяет создать единый объект JSON в качестве выходных данных.  
  
 Если не указать этот параметр, выходные данные JSON будут заключены в квадратные скобки.  
  
## Примеры  
 В следующем примере показаны выходные данные предложения **FOR JSON** с параметром **WITHOUT_ARRAY_WRAPPER** и без него.  
  
 **Запрос**  
  
```tsql  
SELECT 2015 as year, 12 as month, 15 as day  
FOR JSON PATH, WITHOUT_ARRAY_WRAPPER  
```  
  
 **Result** с параметром **WITHOUT_ARRAY_WRAPPER**  
  
```json  
{ "year":2015, "month":12, "day":15 }  
```  
  
 **Result** без параметра **WITHOUT_ARRAY_WRAPPER**  
  
```json  
[ { "year":2015, "month":12, "day":15 } ]  
```  
  
 Вот другой пример предложения **FOR JSON** с параметром **WITHOUT_ARRAY_WRAPPER**.  
  
 **Запрос**  
  
```tsql  
SELECT TOP 1 SalesOrderNumber, OrderDate, Status  
FROM Sales.SalesOrderHeader  
ORDER BY ModifiedDate  
FOR JSON PATH, WITHOUT_ARRAY_WRAPPER  
```  
  
 **Result** с параметром **WITHOUT_ARRAY_WRAPPER**  
  
```json  
{  
    "SalesOrderNumber":"SO43660",  
    "OrderDate":"2011-05-31T00:00:00",  
    "Status":5  
}  
```  
  
 **Result** без параметра **WITHOUT_ARRAY_WRAPPER**  
  
```json  
[  
    {  
        "SalesOrderNumber":"SO43660",  
        "OrderDate":"2011-05-31T00:00:00",  
        "Status":5  
    }  
]  
```  
  
## См. также:  
 [Предложение FOR (Transact-SQL)](../Topic/FOR%20Clause%20\(Transact-SQL\).md)  
  
  