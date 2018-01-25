---
title: "Поиск условие (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 01/15/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|queries
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- search
- Search Condition
- condition
dev_langs: TSQL
helpviewer_keywords:
- OR operator [Transact-SQL]
- CONTAINS predicate (Transact-SQL)
- ESCAPE keyword
- operators [Transact-SQL], search condition
- search conditions [SQL Server]
- WHERE clause, search conditions
- ALL keyword
- FREETEXT predicate (Transact-SQL)
- EXISTS keyword
- search conditions [SQL Server], about search conditions
- NOT operator [Transact-SQL]
- BETWEEN operator
- SOME | ANY keyword
- predicates [full-text search]
- AND, about search conditions
- logical operators [SQL Server], about search conditions
- precedence [SQL Server], logical operators
- logical operators [SQL Server], precedence
- LIKE comparisons
ms.assetid: 09974469-c5d2-4be8-bc5a-78e404660b2c
caps.latest.revision: "43"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: aff1f4010182b601111ed2ba892bb06b6e82b71d
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="search-condition-transact-sql"></a>Условие поиска (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Сочетание одного или нескольких предикатов, в котором используются логические операторы AND, OR и NOT.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
<search_condition> ::=   
    { [ NOT ] <predicate> | ( <search_condition> ) }   
    [ { AND | OR } [ NOT ] { <predicate> | ( <search_condition> ) } ]   
[ ,...n ]   
  
<predicate> ::=   
    { expression { = | < > | ! = | > | > = | ! > | < | < = | ! < } expression   
    | string_expression [ NOT ] LIKE string_expression   
  [ ESCAPE 'escape_character' ]   
    | expression [ NOT ] BETWEEN expression AND expression   
    | expression IS [ NOT ] NULL   
    | CONTAINS   
  ( { column | * } , '<contains_search_condition>' )   
    | FREETEXT ( { column | * } , 'freetext_string' )   
    | expression [ NOT ] IN ( subquery | expression [ ,...n ] )   
    | expression { = | < > | ! = | > | > = | ! > | < | < = | ! < }   
  { ALL | SOME | ANY} ( subquery )   
    | EXISTS ( subquery )     }   
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
< search_condition > ::=   
    { [ NOT ] <predicate> | ( <search_condition> ) }   
    [ { AND | OR } [ NOT ] { <predicate> | ( <search_condition> ) } ]   
[ ,...n ]   
  
<predicate> ::=   
    { expression { = | < > | ! = | > | > = | < | < = } expression   
    | string_expression [ NOT ] LIKE string_expression   
    | expression [ NOT ] BETWEEN expression AND expression   
    | expression IS [ NOT ] NULL   
    | expression [ NOT ] IN (subquery | expression [ ,...n ] )   
    | expression [ NOT ] EXISTS (subquery)     }   
```  
  
## <a name="arguments"></a>Аргументы  
 \<search_condition>  
 Задает условия для строк, возвращаемых в результирующем наборе инструкции SELECT, выражения запроса или вложенного запроса. Задает обновляемые строки для инструкции UPDATE. Задает удаляемые строки для инструкции DELETE. Количество предикатов, которое может содержаться в условии поиска для инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)], не ограничено.  
  
 NOT  
 Инвертирует логическое выражение, задаваемое предикатом. Дополнительные сведения см. в разделе [не &#40; Transact-SQL &#41; ](../../t-sql/language-elements/not-transact-sql.md).  
  
 и  
 Объединяет два условия и выдает значение TRUE, если оба условия имеют значение TRUE. Дополнительные сведения см. в разделе [и &#40; Transact-SQL &#41; ](../../t-sql/language-elements/and-transact-sql.md).  
  
 или  
 Объединяет два условия и выдает значение TRUE, если хотя бы одно условие имеет значение TRUE. Дополнительные сведения см. в разделе [или &#40; Transact-SQL &#41; ](../../t-sql/language-elements/or-transact-sql.md).  
  
 \<Предикат >  
 Выражение, возвращающее значения TRUE, FALSE или UNKNOWN.  
  
 *expression*  
 Может являться именем столбца, константой, функцией, переменной, скалярным вложенным запросом или любым сочетанием имен столбцов, констант и функций, связанных операторами или вложенным запросом. Также может содержать выражение CASE.  
  
> [!NOTE]  
>  Не в Юникоде строковые константы и переменные используют кодовую страницу, соответствующий параметрам сортировки базы данных. Код может запускают страницу преобразования при использовании только символьных данных не в Юникоде, ссылаясь на символьных типов данных не в Юникоде **char**, **varchar**, и **текст**. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Преобразует кодовую страницу, соответствующий параметрам сортировки столбца, на который указывает ссылка, или указано использование предложения COLLATE, если эту кодовую страницу отличается от кодовой страницы, соответствующий параметрам сортировки по умолчанию базы данных не в Юникоде строковые константы и переменные. Любые символы, не входящие в новую кодовую страницу будут преобразованы с похожим символом, если [наилучшего соответствия](http://www.unicode.org/Public/MAPPINGS/VENDORS/MICSFT/WindowsBestFit/) можно найти, в противном случае преобразуется в символ замены по умолчанию «?».  
>  
> При работе с несколько кодовых страниц, символьные константы может иметь префикс с заглавной буквы 'N' и в Юникоде переменные могут использоваться, чтобы избежать преобразования кодовых страниц.  
  
 =  
 Оператор, используемый для проверки равенства двух выражений.  
  
 <>  
 Оператор, используемый для проверки условий неравенства условий двух выражений.  
  
 !=  
 Оператор, используемый для проверки условий неравенства условий двух выражений.  
  
 \>  
 Оператор, используемый для проверки превышения одного выражения над условием другого.  
  
 \>=  
 Оператор, используемый для проверки превышения либо равенства двух выражений.  
  
 !>  
 Оператор, используемый для проверки того, что одно выражение не превышает другое выражение.  
  
 <  
 Оператор, используемый для проверки того, что одно выражение меньше другого.  
  
 <=  
 Оператор, используемый для проверки того, что одно выражение меньше или равно другому.  
  
 !<  
 Оператор, используемый для проверки того, что одно выражение не меньше другого.  
  
 *string_expression*  
 Строка обычных символов и символов-шаблонов.  
  
 [ NOT ] LIKE  
 Указывает, что последующая строка символов для использования с сопоставлением шаблонов. Дополнительные сведения см. в разделе [как &#40; Transact-SQL &#41; ](../../t-sql/language-elements/like-transact-sql.md).  
  
 ESCAPE- **"***escape_ символ***"**  
 Позволяет найти сам символ-шаблон в строке (вместо того чтобы использовать его как шаблон). *escape_character* — это символ, помещаемый перед символом, чтобы указать данное специальное использование.  
  
 [ NOT ] BETWEEN  
 Задает включающий диапазон значений. Используйте оператор AND для разделения начальных и конечных значений. Дополнительные сведения см. в разделе [BETWEEN &#40; Transact-SQL &#41; ](../../t-sql/language-elements/between-transact-sql.md).  
  
 IS [NOT] NULL  
 Задает поиск значений NULL или значений, не являющихся значениями NULL, в зависимости от используемых ключевых слов. При обращении одного из операндов выражения с битовыми или арифметическими операторами в значение NULL указанное выражение также обращается в значение NULL.  
  
 CONTAINS  
 Осуществляет поиск столбцов, содержащих символьные данные, для точного или менее точный (*Нечеткое*) совпадает с отдельными словами и фразами, сходства слов на определенном расстоянии друг с другом и взвешенных совпадений. Этот параметр может быть использован только в инструкции SELECT. Дополнительные сведения см. в разделе [CONTAINS &#40; Transact-SQL &#41; ](../../t-sql/queries/contains-transact-sql.md).  
  
 FREETEXT  
 Предоставляет простую форму естественного языка ввода запросов на осуществление поиска столбцов, содержащих символьные данные, совпадающие с содержанием предиката не точно, а по смыслу. Этот параметр может быть использован только в инструкции SELECT. Дополнительные сведения см. в разделе [FREETEXT &#40; Transact-SQL &#41; ](../../t-sql/queries/freetext-transact-sql.md).  
  
 [ NOT ] IN  
 Задает поиск выражения, основанного на выражении, включенного или исключенного из списка. Выражение поиска может быть константой или именем столбца, а списком может быть набор констант или, что чаще, вложенный запрос. Список значений необходимо заключать в скобки. Дополнительные сведения см. в статье [IN (Transact-SQL)](../../t-sql/language-elements/in-transact-sql.md).  
  
 *subquery*  
 Может рассматриваться как ограниченная инструкция SELECT и похож на \<query_expresssion > в инструкции SELECT. Использование предложения ORDER BY и ключевого слова INTO не допускается. Дополнительные сведения см. в разделе [ВЫБЕРИТЕ &#40; Transact-SQL &#41; ](../../t-sql/queries/select-transact-sql.md).  
  
 ALL  
 Используется с оператором сравнения и вложенным запросом. Возвращает значение TRUE для \<предиката > при всех значений, полученных для вложенного запроса удовлетворяют условию, или FALSE, если не все значения удовлетворяют условию или если вложенный запрос не возвращает строк внешней инструкции. Дополнительные сведения см. в разделе [все &#40; Transact-SQL &#41; ](../../t-sql/language-elements/all-transact-sql.md).  
  
 { SOME | ANY }  
 Используется с оператором сравнения и вложенным запросом. Возвращает значение TRUE для \<предиката > при получении любого значения для вложенного запроса значение удовлетворяет условию, или FALSE, если значения во вложенном запросе не удовлетворяет условию или если вложенный запрос не возвращает строк внешней инструкции. В противном случае результатом выражения является значение UNKNOWN. Дополнительные сведения см. в разделе [НЕКОТОРЫЕ &#124; ВСЕ &#40; Transact-SQL &#41; ](../../t-sql/language-elements/some-any-transact-sql.md).  
  
 EXISTS  
 Используется во вложенном запросе для проверки существования строк, возвращенных вложенным запросом. Дополнительные сведения см. в разделе [EXISTS &#40; Transact-SQL &#41; ](../../t-sql/language-elements/exists-transact-sql.md).  
  
## <a name="remarks"></a>Remarks  
 Приоритеты выполнения логических операторов распределяются следующим образом: NOT (наивысший приоритет), AND, OR (низший приоритет). Для перераспределения указанных приоритетов в условии поиска используются скобки. Порядок выполнения логических операторов может меняться в зависимости от настроек оптимизатора запросов. Дополнительные сведения о как логические операторы работают на логические значения в разделе [и &#40; Transact-SQL &#41; ](../../t-sql/language-elements/and-transact-sql.md), [Или &#40; Transact-SQL &#41; ](../../t-sql/language-elements/or-transact-sql.md), и [не &#40; Transact-SQL &#41; ](../../t-sql/language-elements/not-transact-sql.md).  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-using-where-with-like-and-escape-syntax"></a>A. Использование предложения WHERE вместе с синтаксисом LIKE и ESCAPE  
 Следующий пример выполняет поиск строк, для которых `LargePhotoFileName` столбец содержит символы `green_`и использует `ESCAPE` поскольку _ является подстановочным знаком. Без указания `ESCAPE` параметр, запрос будет выполнять поиск всех описанных значений, содержащих слово `green` следуют любой символ, отличный от символа _.  
  
```  
USE AdventureWorks2012 ;  
GO  
SELECT *   
FROM Production.ProductPhoto  
WHERE LargePhotoFileName LIKE '%greena_%' ESCAPE 'a' ;  
```  
  
### <a name="b-using-where-and-like-syntax-with-unicode-data"></a>Б. Использование предложения WHERE и синтаксиса LIKE с данными в Юникоде  
 В следующем примере используется предложение `WHERE` для отображения всех адресов офисов компаний, находящихся за пределами США (`US`) и в городах, названия которых начинаются с `Pa`.  
  
```  
USE AdventureWorks2012 ;  
GO  
SELECT AddressLine1, AddressLine2, City, PostalCode, CountryRegionCode    
FROM Person.Address AS a  
JOIN Person.StateProvince AS s ON a.StateProvinceID = s.StateProvinceID  
WHERE CountryRegionCode NOT IN ('US')  
AND City LIKE N'Pa%' ;  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-using-where-with-like"></a>В. Использование предложения WHERE совместно с LIKE  
 Следующий пример выполняет поиск строк, для которых `LastName` столбец содержит символы `and`.  
  
```  
-- Uses AdventureWorks  
  
SELECT EmployeeKey, LastName  
FROM DimEmployee  
WHERE LastName LIKE '%and%';  
```  
  
### <a name="d-using-where-and-like-syntax-with-unicode-data"></a>Г. Использование предложения WHERE и синтаксиса LIKE с данными в Юникоде  
 В следующем примере используется `WHERE` предложение для выполнения поиска Юникода на `LastName` столбца.  
  
```  
-- Uses AdventureWorks  
  
SELECT EmployeeKey, LastName  
FROM DimEmployee  
WHERE LastName LIKE N'%and%';  
```  
  
## <a name="see-also"></a>См. также  
 [Агрегатные функции &#40; Transact-SQL &#41;](../../t-sql/functions/aggregate-functions-transact-sql.md)   
 [РЕГИСТР &#40; Transact-SQL &#41;](../../t-sql/language-elements/case-transact-sql.md)   
 [CONTAINSTABLE (Transact-SQL)](../../relational-databases/system-functions/containstable-transact-sql.md)   
 [Курсоры (Transact-SQL)](../../t-sql/language-elements/cursors-transact-sql.md)   
 [DELETE (Transact-SQL)](../../t-sql/statements/delete-transact-sql.md)   
 [Выражения &#40; Transact-SQL &#41;](../../t-sql/language-elements/expressions-transact-sql.md)   
 [FREETEXTTABLE (Transact-SQL)](../../relational-databases/system-functions/freetexttable-transact-sql.md)   
 [FROM (Transact-SQL)](../../t-sql/queries/from-transact-sql.md)   
 [Операторы &#40; Transact-SQL &#41;](../../t-sql/language-elements/operators-transact-sql.md)   
 [UPDATE (Transact-SQL)](../../t-sql/queries/update-transact-sql.md)  
  
  

