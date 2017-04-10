---
title: "Выражения пути JSON (SQL Server) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "01/23/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-json"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "выражения пути JSON"
  - "выражения пути (JSON)"
ms.assetid: 25ea679c-84cc-4977-867c-2cbe9d192553
caps.latest.revision: 14
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 11
---
# Выражения пути JSON (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Используйте выражения пути JSON для создания ссылок на свойства объектов JSON. В выражениях пути JSON используется синтаксис, похожий на синтаксис Javascript.  
  
 Выражение пути нужно указывать при вызове следующих функций.  
  
-   При вызове **OPENJSON** для создания реляционного представления данных JSON. Дополнительные сведения см. в разделе [OPENJSON (Transact-SQL)](../../t-sql/functions/openjson-transact-sql.md).  
  
-   При вызове **JSON_VALUE** с целью извлечения значения из текста JSON. Дополнительные сведения см. в разделе [JSON_VALUE (Transact-SQL)](../../t-sql/functions/json-value-transact-sql.md).  
  
-   При вызове **JSON_QUERY** для извлечения объекта JSON или массива. Дополнительные сведения см. в разделе [JSON_QUERY (Transact-SQL)](../../t-sql/functions/json-query-transact-sql.md).  
  
-   При вызове **JSON_MODIFY** для обновления значения свойства в строке JSON. Дополнительные сведения см. в разделе [JSON_MODIFY (Transact-SQL)](../../t-sql/functions/json-modify-transact-sql.md).  
  
 Выражение пути состоит из двух компонентов.  
  
1.  Необязательный компонент [режим пути](#PATHMODE)со значениями lax или strict.  
  
2.  Сам [путь](#PATH) .  
  
##  <a name="PATHMODE"></a> режим пути  
 В начале выражения пути можно при необходимости объявить режим пути, указав ключевое слово **lax** или **strict**. По умолчанию **lax**.  
  
-   В режиме **lax** функции возвращают пустые значения, если выражение пути содержит ошибку. Например, если вы запрашиваете значение **$.name**, а текст JSON не содержит ключ **name** , функция вернет значение NULL.  
  
-   В режиме **strict** функции возвращают ошибки, если выражение пути содержит ошибку.  
  
##  <a name="PATH"></a> путь  
 Объявив необязательный режим пути, укажите сам путь.  
  
-   Знак доллара ($) представляет элемент контекста.  
  
-   Путь свойства — это набор действий пути. Действия пути могут содержать следующие элементы и операторы.  
  
    -   Имена ключей. Если имя ключа начинается со знака доллара или содержит специальные символы, например пробелы, заключите его в кавычки. Например, `$.name` или `$."first name"`.  
  
    -   Элементы массива. Например, `$.product[3]`. Массивы отсчитываются от нуля.  
  
    -   Оператор "точка" (.) указывает на элемент объекта.  
  
## Примеры  
 В примерах этого раздела используется следующий текст JSON.  
  
```json  
{ "people":  
  [  
    { "name": "John", "surname": "Doe" },  
    { "name": "Jane", "surname": null, "active": true }  
  ]  
}  
```  
  
 В таблице ниже приведены некоторые примеры выражений пути.  
  
|Выражение пути|Значение|  
|---------------------|-----------|  
|$.people[0].name|Джон|  
|$.people[1]|{ "name": "Jane", "surname": null, "active": true }|  
|$.people[1].surname|null|  
|$|{ "people": [ { "name": "John",  "surname": "Doe" },<br />   { "name": "Jane",  "surname": null, "active": true } ] }|  
  
## Как обрабатываются повторяющиеся пути  
 Если текст JSON содержит повторяющиеся свойства (например, два ключа с одним именем на одном уровне), функции JSON_VALUE и JSON_QUERY возвращают первое значение, которое соответствует пути. Чтобы проанализировать объект JSON, который содержит повторяющиеся ключи, используйте OPENJSON, как показано в следующем примере.  
  
```tsql  
DECLARE @json NVARCHAR(MAX) = N'{"person":{"info":{"name":"John", "name":"Jack"}}}'  
  
SELECT value FROM OPENJSON(@json, '$.person.info')  
```  
  
## См. также:  
 [OPENJSON (Transact-SQL)](../../t-sql/functions/openjson-transact-sql.md)   
 [JSON_VALUE (Transact-SQL)](../../t-sql/functions/json-value-transact-sql.md)   
 [JSON_QUERY (Transact-SQL)](../../t-sql/functions/json-query-transact-sql.md)  
  
  