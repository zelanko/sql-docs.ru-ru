---
title: STRING_AGG (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 04/19/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: conceptual
f1_keywords:
- STRING_AGG
- STRING_AGG_TSQL
helpviewer_keywords:
- STRING_AGG function
ms.assetid: 8860ef3f-142f-4cca-aa64-87a123e91206
author: MikeRayMSFT
ms.author: mikeray
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 3af59410ed151e54a5cc7ea7a546f8979a318693
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67906874"
---
# <a name="stringagg-transact-sql"></a>STRING_AGG (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2017-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2017-asdb-asdw-xxx-md.md)]

Сцепляет значения строковых выражений, помещая между ними значения-разделители. В конце строки разделитель не добавляется.
 
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
STRING_AGG ( expression, separator ) [ <order_clause> ]

<order_clause> ::=   
    WITHIN GROUP ( ORDER BY <order_by_expression_list> [ ASC | DESC ] )   
```

## <a name="arguments"></a>Аргументы

*expression*  
[Выражение](../../t-sql/language-elements/expressions-transact-sql.md) любого типа данных. Во время объединения выражения преобразуются в тип `NVARCHAR` или `VARCHAR`. Нестроковые типы преобразуются в тип `NVARCHAR`.

*separator*  
[Выражение](../../t-sql/language-elements/expressions-transact-sql.md) типа `NVARCHAR` или `VARCHAR`, которое используется в качестве разделителя сцепляемых строк. Может быть литералом или переменной. 

<order_clause>   
При необходимости укажите очередность сцепляемых результатов с помощью предложения `WITHIN GROUP`:

```
WITHIN GROUP ( ORDER BY <order_by_expression_list> [ ASC | DESC ] )
```   
<order_by_expression_list>   
 
  Список неконстантных [выражений](../../t-sql/language-elements/expressions-transact-sql.md), который можно использовать для сортировки результатов. В запросе допускается только один аргумент `order_by_expression`. По умолчанию задан порядок сортировки по возрастанию.   
  
## <a name="return-types"></a>Типы возвращаемых данных

Тип возвращаемого значения зависит от первого аргумента (expression). Если входной аргумент имеет строковый тип (`NVARCHAR`, `VARCHAR`), результат будет иметь тот же тип. В приведенной ниже таблице перечислены автоматические преобразования.  

|Тип входного выражения |Результат | 
|-------|-------|
|NVARCHAR(MAX) |NVARCHAR(MAX) |
|VARCHAR(MAX) |VARCHAR(MAX) |
|NVARCHAR(1...4000) |NVARCHAR(4000) |
|VARCHAR(1...8000) |VARCHAR(8000) |
|int, bigint, smallint, tinyint, numeric, float, real, bit, decimal, smallmoney, money, datetime, datetime2, |NVARCHAR(4000) |

## <a name="remarks"></a>Remarks

`STRING_AGG` — это агрегатная функция, которая принимает все выражения из строк и сцепляет их в одну строку. Значения выражений неявно преобразуются в строковые типы и затем сцепляются. Неявное преобразование в строки выполняется по существующим правилам преобразования типов данных. Дополнительные сведения о преобразовании типов данных см. в статье [Функции CAST и CONVERT (Transact-SQL)](../../t-sql/functions/cast-and-convert-transact-sql.md). 

Если входное выражение имеет тип `VARCHAR`, разделитель не может иметь тип `NVARCHAR`. 

Значения NULL пропускаются, и соответствующий разделитель не добавляется. Чтобы вернуть заполнитель для значений NULL, используйте функцию `ISNULL`, как показано в примере Б.

Функция `STRING_AGG` доступна на любом уровне совместимости.

## <a name="examples"></a>Примеры

### <a name="a-generate-list-of-names-separated-in-new-lines"></a>A. Формирование списка имен, разделенного по строкам

В приведенном ниже примере формируется список имен в одной результирующей ячейке, разделенный символами возврата каретки.
```sql
SELECT STRING_AGG (FirstName, CHAR(13)) AS csv 
FROM Person.Person; 
```
[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]

|csv | 
|--- |
|Syed <br />Catherine <br />Kim <br />Kim <br />Kim <br />Hazem <br />... | 

Значения `NULL`, найденные в ячейках `name`, не возвращаются в результатах.   
> [!NOTE]  
>  Если в редакторе запросов Management Studio используется режим **В виде сетки**, символы возврата каретки не применяются. Чтобы результирующий набор отображался правильно, перейдите в режим **В виде текста**.   

### <a name="b-generate-list-of-names-separated-with-comma-without-null-values"></a>Б. Формирование списка имен, разделенного запятыми, без значений NULL

В приведенном ниже примере значения NULL заменяются на "N/A" и имена, разделенные запятыми, возвращаются в одной результирующей ячейке.  
```sql
SELECT STRING_AGG ( ISNULL(FirstName,'N/A'), ',') AS csv 
FROM Person.Person; 
```

[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]

|Csv | 
|--- |
|John,N/A,Mike,Peter,N/A,N/A,Alice,Bob |  

### <a name="c-generate-comma-separated-values"></a>В. Формирование списка значений с разделителями-запятыми

```sql
SELECT 
STRING_AGG(CONCAT(FirstName, ' ', LastName, ' (', ModifiedDate, ')'), CHAR(13)) 
  AS names 
FROM Person.Person; 
```
[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]

|имена |
|--- |
|Ken Sánchez (Feb 8 2003 12:00AM) <br />Terri Duffy (Feb 24 2002 12:00AM) <br />Roberto Tamburello (Dec 5 2001 12:00AM) <br />Rob Walters (Dec 29 2001 12:00AM) <br />... |

> [!NOTE]  
>  Если в редакторе запросов Management Studio используется режим **В виде сетки**, символы возврата каретки не применяются. Чтобы результирующий набор отображался правильно, перейдите в режим **В виде текста**.   

### <a name="d-return-news-articles-with-related-tags"></a>Г. Получение новых статей со связанными тегами 
Статьи и их теги разнесены по разным таблицам. Разработчику необходимо получить одну строку для каждой статьи со всеми связанными тегами. Используется следующий запрос:

```sql
SELECT a.articleId, title, STRING_AGG (tag, ',') as tags 
FROM dbo.Article AS a       
LEFT JOIN dbo.ArticleTag AS t 
    ON a.ArticleId = t.ArticleId 
GROUP BY a.articleId, title;
```

[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]

|articleId |title |tags |
|--- |--- |--- |
|172 |Опросы предвещают напряженную борьбу на выборах |политика,опросы,муниципалитет | 
|176 |Новая автострада разгрузит транспортные потоки |NULL |
|177 |Собаки по-прежнему популярнее кошек |опросы,животные| 

### <a name="e-generate-list-of-emails-per-towns"></a>Д. Формирование списка адресов электронной почты по городам

Следующий запрос находит адреса электронной почты сотрудников и группирует их по городам:

```sql
SELECT town, STRING_AGG (email, ';') AS emails 
FROM dbo.Employee 
GROUP BY town; 
```

[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]

|town |emails |
|--- |--- |
|Seattle |syed0@adventure-works.com;catherine0@adventure-works.com;kim2@adventure-works.com |
|LA |sam1@adventure-works.com;hazem0@adventure-works.com |

Адреса, возвращенные в столбце emails, можно использовать для рассылки сообщений группе людей, работающих в определенном городе. 

### <a name="f-generate-a-sorted-list-of-emails-per-towns"></a>Е. Формирование отсортированного списка адресов электронной почты по городам   
Так же как в предыдущем примере, следующий запрос находит адреса электронной почты сотрудников, группирует их по городам и сортирует по алфавиту:   
```sql
SELECT town, 
    STRING_AGG (email, ';') WITHIN GROUP (ORDER BY email ASC) AS emails 
FROM dbo.Employee 
GROUP BY town; 
```
   
[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]

|town |emails |
|--- |--- |
|Seattle |catherine0@adventure-works.com;kim2@adventure-works.com;syed0@adventure-works.com |
|LA |hazem0@adventure-works.com;sam1@adventure-works.com |

## <a name="see-also"></a>См. также раздел
 
 [CONCAT (Transact-SQL)](../../t-sql/functions/concat-transact-sql.md)  
 [CONCAT_WS (Transact-SQL)](../../t-sql/functions/concat-ws-transact-sql.md)  
 [FORMATMESSAGE (Transact-SQL)](../../t-sql/functions/formatmessage-transact-sql.md)  
 [QUOTENAME (Transact-SQL)](../../t-sql/functions/quotename-transact-sql.md)  
 [REPLACE (Transact-SQL)](../../t-sql/functions/replace-transact-sql.md)  
 [REVERSE (Transact-SQL)](../../t-sql/functions/reverse-transact-sql.md)  
 [STRING_ESCAPE (Transact-SQL)](../../t-sql/functions/string-escape-transact-sql.md)  
 [STUFF (Transact-SQL)](../../t-sql/functions/stuff-transact-sql.md)  
 [TRANSLATE (Transact-SQL)](../../t-sql/functions/translate-transact-sql.md)  
 [Агрегатные функции (Transact-SQL)](../../t-sql/functions/aggregate-functions-transact-sql.md)  
 [Строковые функции (Transact-SQL)](../../t-sql/functions/string-functions-transact-sql.md)  

