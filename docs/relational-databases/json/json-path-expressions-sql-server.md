---
title: "Выражения пути JSON (SQL Server) | Документация Майкрософт"
ms.custom: SQL2016_New_Updated
ms.date: 01/23/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: dbe-json
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- JSON, path expressions
- path expressions (JSON)
ms.assetid: 25ea679c-84cc-4977-867c-2cbe9d192553
caps.latest.revision: "14"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 24bd97b912507021544b7c4227e409b1d400ea66
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="json-path-expressions-sql-server"></a>Выражения пути JSON (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

 Используйте выражения пути JSON для создания ссылок на свойства объектов JSON.  
  
 Выражение пути нужно указывать при вызове следующих функций.  
  
-   При вызове **OPENJSON** для создания реляционного представления данных JSON. Дополнительные сведения см. в разделе [OPENJSON (Transact-SQL)](../../t-sql/functions/openjson-transact-sql.md).  
  
-   При вызове **JSON_VALUE** с целью извлечения значения из текста JSON. Дополнительные сведения см. в разделе [JSON_VALUE (Transact-SQL)](../../t-sql/functions/json-value-transact-sql.md).  
  
-   При вызове **JSON_QUERY** для извлечения объекта JSON или массива. Дополнительные сведения см. в разделе [JSON_QUERY (Transact-SQL)](../../t-sql/functions/json-query-transact-sql.md).  
  
-   При вызове **JSON_MODIFY** для обновления значения свойства в строке JSON. Дополнительные сведения см. в разделе [JSON_MODIFY (Transact-SQL)](../../t-sql/functions/json-modify-transact-sql.md).  

## <a name="parts-of-a-path-expression"></a>Элементы выражения пути
 Выражение пути состоит из двух компонентов.  
  
1.  Необязательный компонент [path mode](#PATHMODE) со значением **lax** или **strict**.  
  
2.  Сам [путь](#PATH) .  

##  <a name="PATHMODE"></a> Path mode  
 В начале выражения пути можно при необходимости объявить режим пути, указав ключевое слово **lax** или **strict**. По умолчанию **lax**.  
  
-   В режиме **lax** функция возвращает пустые значения, если выражение пути содержит ошибку. Например, если вы запрашиваете значение **$.name**, а текст JSON не содержит ключ **name**, функция вернет значение NULL, но ошибку это не вызовет.  
  
-   В режиме **strict** функция возвращает ошибку, если выражение пути содержит ошибку.  

В следующем запросе в выражении пути явно задан режим `lax`.

```sql  
DECLARE @json NVARCHAR(MAX)
SET @json=N'{ ... }'

SELECT * FROM OPENJSON(@json, N'lax $.info')
```  
  
##  <a name="PATH"></a> Path  
 Объявив необязательный режим пути, укажите сам путь.  
  
-   Знак доллара (`$`) представляет элемент контекста.  
  
-   Путь свойства — это набор действий пути. Действия пути могут содержать следующие элементы и операторы.  
  
    -   Имена ключей. Например, `$.name` или `$."first name"`. Если имя ключа начинается со знака доллара или содержит специальные символы, например пробелы, заключите его в кавычки.   
  
    -   Элементы массива. Например, `$.product[3]`. Массивы отсчитываются от нуля.  
  
    -   Оператор "точка" (`.`) указывает на элемент объекта. Например, в `$.people[1].surname` `surname` является дочерним элементом `people`.
  
## <a name="examples"></a>Примеры  
 В примерах этого раздела используется следующий текст JSON.  
  
```json  
{
    "people": [{
        "name": "John",
        "surname": "Doe"
    }, {
        "name": "Jane",
        "surname": null,
        "active": true
    }]
}
```  
  
 В таблице ниже приведены некоторые примеры выражений пути.  
  
|Выражение пути|Значение|  
|---------------------|-----------|  
|$.people[0].name|Джон|  
|$.people[1]|{ "name": "Jane", "surname": null, "active": true }|  
|$.people[1].surname|null|  
|$|{ "people": [ { "name": "John",  "surname": "Doe" },<br />   { "name": "Jane",  "surname": null, "active": true } ] }|  
  
## <a name="how-built-in-functions-handle-duplicate-paths"></a>Как встроенные функции обрабатывают повторяющиеся пути  
 Если текст JSON содержит повторяющиеся свойства (например, два ключа с одним и тем же именем на одном уровне), функции **JSON_VALUE** и **JSON_QUERY** возвращают первое значение, которое соответствует пути. Чтобы проанализировать объект JSON, который содержит повторяющиеся ключи, и получить все значения, используйте функцию **OPENJSON**, как показано в следующем примере.  
  
```sql  
DECLARE @json NVARCHAR(MAX)
SET @json=N'{"person":{"info":{"name":"John", "name":"Jack"}}}'

SELECT value
FROM OPENJSON(@json,'$.person.info') 
```  

## <a name="learn-more-about-the-built-in-json-support-in-sql-server"></a>Дополнительные сведения о встроенной поддержке JSON в SQL Server  
Большое количество решений, варианты использования и рекомендации см. в [записях Йована Поповича (Jovan Popovic), руководителя программы Майкрософт, в блогах о встроенной поддержке JSON](http://blogs.msdn.com/b/sqlserverstorageengine/archive/tags/json/) в SQL Server и базах данных SQL Azure.
  
## <a name="see-also"></a>См. также:  
 [OPENJSON (Transact-SQL)](../../t-sql/functions/openjson-transact-sql.md)   
 [JSON_VALUE (Transact-SQL)](../../t-sql/functions/json-value-transact-sql.md)   
 [JSON_QUERY (Transact-SQL)](../../t-sql/functions/json-query-transact-sql.md)  
  
  
