---
title: "STRING_AGG (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 04/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- STRING_AGG
- STRING_AGG_TSQL
helpviewer_keywords:
- STRING_AGG function
ms.assetid: 8860ef3f-142f-4cca-aa64-87a123e91206
caps.latest.revision: 13
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: bf74698e9e61f456726b1e6a62126a8d78a09777
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="stringagg-transact-sql"></a>STRING_AGG (Transact-SQL)
[!INCLUDE[tsql-appliesto-ssvNxt-asdb-xxxx-xxx](../../includes/tsql-appliesto-ssvnxt-asdb-xxxx-xxx.md)]

Объединяет значения строковых выражений и помещает значения разделителя между ними. Разделитель не добавляется в конце строки.
 
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
STRING_AGG ( expression, separator ) [ <order_clause> ]

<order_clause> ::=   
    WITHIN GROUP ( ORDER BY <order_by_expression_list> [ ASC | DESC ] )   
```

## <a name="arguments"></a>Аргументы 

*разделитель*  
— [Выражение](../../t-sql/language-elements/expressions-transact-sql.md) из `NVARCHAR` или `VARCHAR` тип, используемый в качестве разделителя для объединения строк. Это может быть литералом или переменной. 

*expression*  
— [Выражение](../../t-sql/language-elements/expressions-transact-sql.md) любого типа. Выражения преобразуются в `NVARCHAR` или `VARCHAR` типов во время объединения. Типы строк не преобразуются в `NVARCHAR` типа.


< order_clause >   
При необходимости укажите порядок объединенных результатов, с помощью `WITHIN GROUP` предложения:
```
WITHIN GROUP ( ORDER BY <order_by_expression_list> [ ASC | DESC ] )
```   
< order_by_expression_list >   
 
  Список неконстантное [выражений](../../t-sql/language-elements/expressions-transact-sql.md) может использоваться для сортировки результатов. Только один `order_by_expression` допускается для каждого запроса. По умолчанию задан порядок сортировки по возрастанию.   
  

## <a name="return-types"></a>Типы возвращаемых значений 

Тип возвращаемого значения зависит от первый аргумент (expression). Если входной аргумент имеет тип string (`NVARCHAR`, `VARCHAR`), тип результат будет такой же, как тип входных данных. В следующей таблице перечислены автоматические преобразования:  

|Тип входного выражения. |Результат | 
|-------|-------|
|NVARCHAR(MAX) |NVARCHAR(MAX) |
|VARCHAR(MAX) |VARCHAR(MAX) |
|NVARCHAR (1... 4000) |NVARCHAR(4000) |
|VARCHAR (1... 8000) |VARCHAR(8000) |
|int, bigint, smallint, tinyint, числовых, float, real, бит, decimal, smallmoney, money, datetime, datetime2, |NVARCHAR(4000) |


## <a name="remarks"></a>Замечания  
 
`STRING_AGG`Статистическая функция принимает все выражения из строк и объединяет их в одну строку. Выражение значения являются неявно преобразуются в строковые типы и затем объединяются. Неявное преобразование в строки выполняется по существующим правилам преобразования типов данных. Дополнительные сведения о преобразованиях типов данных см. в разделе [CAST и CONVERT (Transact-SQL)](../../t-sql/functions/cast-and-convert-transact-sql.md). 

Если входное выражение имеет тип `VARCHAR`, разделитель не может быть типом `NVARCHAR`. 

Значения NULL учитываются и соответствующий разделитель не добавляется. Чтобы вернуть заполнителя для значений null, используйте `ISNULL` работать так, как показано в примере б.

`STRING_AGG`доступна на любом уровне совместимости.


## <a name="examples"></a>Примеры 

### <a name="a-generate-list-of-names-separated-in-new-lines"></a>A. Создать список имен, разделенных в новых строк 
В следующем примере создается список имен в ячейке одного результата, разделенные символы возврата каретки.
```tsql
SELECT STRING_AGG (FirstName, CHAR(13)) AS csv 
FROM Person.Person; 
```
[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]

|csv | 
|--- |
|Syed <br />Catherine <br />Kim <br />Kim <br />Kim <br />Hazem <br />... | 

`NULL`Обнаружены значения в `name` ячеек не возвращаются в результатах.   
> [!NOTE]  
>  Если с помощью редактора запросов Management Studio **результаты в таблицу** параметр не может реализовать символ возврата каретки. Переключитесь в **в виде текста** для просмотра результатов в набор должным образом.   


### <a name="b-generate-list-of-names-separated-with-comma-without-null-values"></a>Б. Создать список имен, разделенных точкой с запятой без значений NULL   
В следующем примере заменяет значения null «Н/д» и возвращает имена, разделенные запятыми в одной ячейке.  
```tsql
SELECT STRING_AGG ( ISNULL(FirstName,'N/A'), ',') AS csv 
FROM Person.Person; 
```

[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]
 

|CSV | 
|--- |
|Джон, н/д, Майк, Питер, н/д, н/д, Alice, Bob |  


### <a name="c-generate-comma-separated-values"></a>В. Создать значения с разделителями запятыми 

```tsql   
SELECT 
STRING_AGG(CONCAT(FirstName, ' ', LastName, ' (', ModifiedDate, ')'), CHAR(13)) 
  AS names 
FROM Person.Person; 
```
[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]

|имена | 
|--- |
|Алексей Санчес (8 2003 фев 12:00 AM) <br />Terri Даффи (24 2002 фев 12:00 AM) <br />Roberto Tamburello (дек 5 2001 12:00 AM) <br />Rob Walters (дек 29 2001 12:00 AM) <br />... |

> [!NOTE]  
>  Если с помощью редактора запросов Management Studio **результаты в таблицу** параметр не может реализовать символ возврата каретки. Переключитесь в **в виде текста** для просмотра результатов в набор должным образом.   
 

### <a name="d-return-news-articles-with-related-tags"></a>Г. Возвращать с тегами связанные статьи 

Статьи и их тегов разделяются в различные таблицы. Разработчику необходимо возвращать одну строку для каждой статьи с все связанные с ними теги. С помощью следующего запроса: 
```tsql
SELECT a.articleId, title, STRING_AGG (tag, ',') as tags 
FROM dbo.Article AS a       
LEFT JOIN dbo.ArticleTag AS t 
    ON a.ArticleId = t.ArticleId 
GROUP BY a.articleId, title;
```

[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]

|ИД статьи |title |tags |
|--- |--- |--- |
|172 |Опрашивает указывают результатов закрыть выборов |политика, опросы, Город совета | 
|176 |Новый канал, ожидаемого для уменьшения перегрузки |NULL |
|177 |Собаки продолжают работать с более популярным, чем cats |опрашивает животных| 

### <a name="e-generate-list-of-emails-per-towns"></a>Д. Создать список адресов электронной почты в городах

Следующий запрос находит адреса электронной почты сотрудников и группирует их по городах: 
```tsql
SELECT town, STRING_AGG (email, ';') AS emails 
FROM dbo.Employee 
GROUP BY town; 
```

[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]

|Город |сообщения электронной почты |
|--- |--- |
|Seattle |syed0@adventure-works.com;catherine0@adventure-works.com;kim2@adventure-works.com |
|LA |sam1@adventure-works.com;hazem0@adventure-works.com |

Сообщения электронной почты, возвращается в сообщениях электронной почты, столбец может использоваться непосредственно для отправки сообщений электронной почты в некоторых городах определенной рабочей группы. 

### <a name="f-generate-a-sorted-list-of-emails-per-towns"></a>Е. Сформировать отсортированный список адресов электронной почты в городах   
   
Аналогично предыдущему примеру, следующий запрос находит адреса электронной почты сотрудников, группирует их по городу и сортировка сообщения электронной почты:   
```tsql
SELECT town, 
    STRING_AGG (email, ';') WITHIN GROUP (ORDER BY email ASC) AS emails 
FROM dbo.Employee 
GROUP BY town; 
```
   
[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]

|Город |сообщения электронной почты |
|--- |--- |
|Seattle |catherine0@adventure-works.com;kim2@adventure-works.com;syed0@adventure-works.com |
|LA |hazem0@adventure-works.com;sam1@adventure-works.com |


## <a name="see-also"></a>См. также:  

[Строковые функции (Transact-SQL)](../../t-sql/functions/string-functions-transact-sql.md)  


