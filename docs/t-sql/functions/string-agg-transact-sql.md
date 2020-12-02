---
description: STRING_AGG (Transact-SQL)
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
author: julieMSFT
ms.author: jrasnick
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: fa5490a488168716649a913045b38dc04591ce27
ms.sourcegitcommit: c5078791a07330a87a92abb19b791e950672e198
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "91379814"
---
# <a name="string_agg-transact-sql"></a>STRING_AGG (Transact-SQL)

<!--[!INCLUDE [sqlserver2017-asdb-asdbmi-asa](../../includes/applies-to-version/sqlserver2017-asdb-asdbmi-asa.md)]-->

[!INCLUDE [sqlserver2017-asdb-asdbmi-asa](../../includes/applies-to-version/sqlserver2017-asdb-asdbmi-asa.md)]

Сцепляет значения строковых выражений, помещая между ними значения-разделители. В конце строки разделитель не добавляется. 
 
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```syntaxsql
STRING_AGG ( expression, separator ) [ <order_clause> ]

<order_clause> ::=   
    WITHIN GROUP ( ORDER BY <order_by_expression_list> [ ASC | DESC ] )   
```

[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Аргументы

*expression*  
[Выражение](../../t-sql/language-elements/expressions-transact-sql.md) любого типа данных. Во время объединения выражения преобразуются в тип `NVARCHAR` или `VARCHAR`. Нестроковые типы преобразуются в тип `NVARCHAR`.

*separator* язательно, количество  
[Выражение](../../t-sql/language-elements/expressions-transact-sql.md) типа `NVARCHAR` или `VARCHAR`, которое используется в качестве разделителя сцепляемых строк. Может быть литералом или переменной. 

<order_clause>   
При необходимости укажите очередность сцепляемых результатов с помощью предложения `WITHIN GROUP`:

```syntaxsql
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

## <a name="remarks"></a>Комментарии

`STRING_AGG` — это агрегатная функция, которая принимает все выражения из строк и сцепляет их в одну строку. Значения выражений неявно преобразуются в строковые типы и затем сцепляются. Неявное преобразование в строки выполняется по существующим правилам преобразования типов данных. Дополнительные сведения о преобразовании типов данных см. в статье [Функции CAST и CONVERT (Transact-SQL)](../../t-sql/functions/cast-and-convert-transact-sql.md). 

Если входное выражение имеет тип `VARCHAR`, разделитель не может иметь тип `NVARCHAR`. 

Значения NULL пропускаются, и соответствующий разделитель не добавляется. Чтобы вернуть заполнитель для значений NULL, используйте функцию `ISNULL`, как показано в примере Б.

Функция `STRING_AGG` доступна на любом уровне совместимости.

## <a name="examples"></a>Примеры

### <a name="a-generate-list-of-names-separated-in-new-lines"></a>A. Формирование списка имен, разделенного по строкам

В приведенном ниже примере формируется список имен в одной результирующей ячейке, разделенный символами возврата каретки.
```sql
USE AdventureWorks2016
GO
SELECT STRING_AGG (CONVERT(NVARCHAR(max),FirstName), CHAR(13)) AS csv 
FROM Person.Person;  
```
[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]

|csv | 
|--- |
|Syed <br />Catherine <br />Kim <br />Kim <br />Kim <br />Hazem <br />... | 

Значения `NULL`, найденные в ячейках `name`, не возвращаются в результатах.   

> [!NOTE]  
> Если в редакторе запросов [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]используется режим **В виде сетки**, символы возврата каретки не применяются. Чтобы результирующий набор отображался правильно, перейдите в режим **В виде текста**.       
> По умолчанию результаты в виде текста усекаются до 256 символов. Чтобы увеличить это ограничение, измените значение параметра **Максимальное число символов, отображаемых в каждом столбце**.

### <a name="b-generate-list-of-names-separated-with-comma-without-null-values"></a>Б. Формирование списка имен, разделенного запятыми, без значений NULL

В приведенном ниже примере значения NULL заменяются на "N/A" и имена, разделенные запятыми, возвращаются в одной результирующей ячейке.  
```sql
USE AdventureWorks2016
GO
SELECT STRING_AGG(CONVERT(NVARCHAR(max), ISNULL(FirstName,'N/A')), ',') AS csv 
FROM Person.Person; 
```

[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]

> [!NOTE]
> Результирующий набор отображается обрезанным.

|csv | 
|--- |
|Syed,Catherine,Kim,Kim,Kim,Hazem,Sam,Humberto,Gustavo,Pilar,Pilar, ...|  

### <a name="c-generate-comma-separated-values"></a>В. Формирование списка значений с разделителями-запятыми

```sql
USE AdventureWorks2016
GO
SELECT STRING_AGG(CONVERT(NVARCHAR(max), CONCAT(FirstName, ' ', LastName, '(', ModifiedDate, ')')), CHAR(13)) AS names 
FROM Person.Person; 
```
[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]

> [!NOTE]
> Результирующий набор отображается обрезанным.

|имена |
|--- |
|Ken Sánchez (Feb 8 2003 12:00AM) <br />Terri Duffy (Feb 24 2002 12:00AM) <br />Roberto Tamburello (Dec 5 2001 12:00AM) <br />Rob Walters (Dec 29 2001 12:00AM) <br />... |

> [!NOTE]  
> Если в редакторе запросов Management Studio используется режим **В виде сетки**, символы возврата каретки не применяются. Чтобы результирующий набор отображался правильно, перейдите в режим **В виде текста**.

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

> [!NOTE]
> Предложение `GROUP BY` является обязательным, если функция `STRING_AGG` не является единственным элементом в списке `SELECT`.

### <a name="e-generate-list-of-emails-per-towns"></a>Д. Формирование списка адресов электронной почты по городам

Следующий запрос находит адреса электронной почты сотрудников и группирует их по городам:

```sql
USE AdventureWorks2016
GO

SELECT TOP 10 City, STRING_AGG(CONVERT(NVARCHAR(max), EmailAddress), ';') AS emails 
FROM Person.BusinessEntityAddress AS BEA  
INNER JOIN Person.Address AS A ON BEA.AddressID = A.AddressID
INNER JOIN Person.EmailAddress AS EA ON BEA.BusinessEntityID = EA.BusinessEntityID 
GROUP BY City;
```

[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]

> [!NOTE]
> Результирующий набор отображается обрезанным.

|City |emails |
|--- |--- |
|Ballard|paige28@adventure-works.com;joshua24@adventure-works.com;javier12@adventure-works.com;...|
|Baltimore|gilbert9@adventure-works.com|
|Barstow|kristen4@adventure-works.com|
|Basingstoke Hants|dale10@adventure-works.com;heidi9@adventure-works.com|
|Baytown|kelvin15@adventure-works.com|
|Beaverton|billy6@adventure-works.com;dalton35@adventure-works.com;lawrence1@adventure-works.com;...|
|Bell Gardens|christy8@adventure-works.com
|Бельвью|min0@adventure-works.com;gigi0@adventure-works.com;terry18@adventure-works.com;...|
|Bellflower|philip0@adventure-works.com;emma34@adventure-works.com;jorge8@adventure-works.com;...|
|Bellingham|christopher23@adventure-works.com;frederick7@adventure-works.com;omar0@adventure-works.com;...|

Адреса, возвращенные в столбце emails, можно использовать для рассылки сообщений группе людей, работающих в определенном городе. 

### <a name="f-generate-a-sorted-list-of-emails-per-towns"></a>Е. Формирование отсортированного списка адресов электронной почты по городам   
Так же как в предыдущем примере, следующий запрос находит адреса электронной почты сотрудников, группирует их по городам и сортирует по алфавиту:   

```sql
USE AdventureWorks2016
GO

SELECT TOP 10 City, STRING_AGG(CONVERT(NVARCHAR(max), EmailAddress), ';') WITHIN GROUP (ORDER BY EmailAddress ASC) AS emails 
FROM Person.BusinessEntityAddress AS BEA  
INNER JOIN Person.Address AS A ON BEA.AddressID = A.AddressID
INNER JOIN Person.EmailAddress AS EA ON BEA.BusinessEntityID = EA.BusinessEntityID 
GROUP BY City;
```

[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]

> [!NOTE]
> Результирующий набор отображается обрезанным.

|City |emails |
|--- |--- |
|Barstow|kristen4@adventure-works.com
|Basingstoke Hants|dale10@adventure-works.com;heidi9@adventure-works.com
|Braintree|mindy20@adventure-works.com
|Bell Gardens|christy8@adventure-works.com
|Byron|louis37@adventure-works.com
|Bordeaux|ranjit0@adventure-works.com
|Carnation|don0@adventure-works.com;douglas0@adventure-works.com;george0@adventure-works.com;...|
|Boulogne-Billancourt|allen12@adventure-works.com;bethany15@adventure-works.com;carl5@adventure-works.com;...|
|Berkshire|barbara41@adventure-works.com;brenda4@adventure-works.com;carrie14@adventure-works.com;...|
|Berks|adriana6@adventure-works.com;alisha13@adventure-works.com;arthur19@adventure-works.com;...|

## <a name="see-also"></a>Дополнительно
 
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

