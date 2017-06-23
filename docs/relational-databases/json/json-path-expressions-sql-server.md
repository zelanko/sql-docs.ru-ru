---
title: "Выражения пути JSON (SQL Server) | Документация Майкрософт"
ms.custom:
- SQL2016_New_Updated
ms.date: 01/23/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-json
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- JSON, path expressions
- path expressions (JSON)
ms.assetid: 25ea679c-84cc-4977-867c-2cbe9d192553
caps.latest.revision: 14
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 439b568fb268cdc6e6a817f36ce38aeaeac11fab
ms.openlocfilehash: 44bfd54aa494dd52174eeed8479e14a99d810af3
ms.contentlocale: ru-ru
ms.lasthandoff: 06/23/2017

---
# <a name="json-path-expressions-sql-server"></a>Выражения пути JSON (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

 Используйте выражения пути JSON для ссылки на свойства объектов JSON.  
  
 Выражение пути нужно указывать при вызове следующих функций.  
  
-   При вызове **OPENJSON** для создания реляционного представления данных JSON. Дополнительные сведения см. в разделе [OPENJSON (Transact-SQL)](../../t-sql/functions/openjson-transact-sql.md).  
  
-   При вызове **JSON_VALUE** с целью извлечения значения из текста JSON. Дополнительные сведения см. в разделе [JSON_VALUE (Transact-SQL)](../../t-sql/functions/json-value-transact-sql.md).  
  
-   При вызове **JSON_QUERY** для извлечения объекта JSON или массива. Дополнительные сведения см. в разделе [JSON_QUERY (Transact-SQL)](../../t-sql/functions/json-query-transact-sql.md).  
  
-   При вызове **JSON_MODIFY** для обновления значения свойства в строке JSON. Дополнительные сведения см. в разделе [JSON_MODIFY (Transact-SQL)](../../t-sql/functions/json-modify-transact-sql.md).  

## <a name="parts-of-a-path-expression"></a>Элементы выражения пути
 Выражение пути состоит из двух компонентов.  
  
1.  Необязательный [режим path](#PATHMODE), со значением **нестрогой** или **strict**.  
  
2.  Сам [путь](#PATH) .  

##  <a name="PATHMODE"></a> Path mode  
 В начале выражения пути можно при необходимости объявить режим пути, указав ключевое слово **lax** или **strict**. По умолчанию **lax**.  
  
-   В **нестрогой** режиме, функция возвращает пустое значение, если выражение пути содержит ошибку. Например, если вы запрашиваете значение **$.name**, а текст JSON не содержит **имя** ключа, функция возвращает значение null, но не вызывает ошибку.  
  
-   В **strict** режиме, функция вызывает ошибку, если выражение пути содержит ошибку.  

В следующем запросе задана явно `lax` режим в выражении пути.

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
  
    -   Оператор "точка" (`.`) указывает на элемент объекта. Например, в `$.people[1].surname`, `surname` является дочерним элементом `people`.
  
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
 Если текст JSON содержит повторяющиеся свойства — например, два ключей с тем же именем на том же уровне - **JSON_VALUE** и **JSON_QUERY** функции возвращают только первое значение, которое соответствует пути. Чтобы проанализировать объект JSON, который содержит повторяющиеся ключи и возврат всех значений, используйте **OPENJSON**, как показано в следующем примере.  
  
```sql  
DECLARE @json NVARCHAR(MAX)
SET @json=N'{"person":{"info":{"name":"John", "name":"Jack"}}}'

SELECT value
FROM OPENJSON(@json,'$.person.info') 
```  

## <a name="learn-more-about-the-built-in-json-support-in-sql-server"></a>Дополнительные сведения о встроенной поддержке JSON в SQL Server  
Большое количество определенных решений варианты использования и рекомендации, см. в разделе [записи в блогах о встроенной поддержке JSON](http://blogs.msdn.com/b/sqlserverstorageengine/archive/tags/json/) в SQL Server и базы данных SQL Azure с руководителем программ Microsoft (Jovan Popovic).
  
## <a name="see-also"></a>См. также:  
 [OPENJSON (Transact-SQL)](../../t-sql/functions/openjson-transact-sql.md)   
 [JSON_VALUE (Transact-SQL)](../../t-sql/functions/json-value-transact-sql.md)   
 [JSON_QUERY (Transact-SQL)](../../t-sql/functions/json-query-transact-sql.md)  
  
  

