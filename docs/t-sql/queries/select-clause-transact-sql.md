---
title: "Предложение SELECT (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 08/09/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SELECT Clause
- SELECT_Clause_TSQL
- DISTINCT_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- parentheses [SQL Server]
- identity columns [SQL Server], SELECT clause
- SELECT clause
- $IDENTITY keyword
- user-defined types [SQL Server], invoking methods and properties
- SELECT statement [SQL Server], processing orders
- clauses [SQL Server], SELECT
- $ROWGUID keyword
- queries [SQL Server], results
ms.assetid: 2616d800-4853-4cf1-af77-d32d68d8c2ef
caps.latest.revision: 54
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: e8b6972868c221ec0368b689164eff740ae6f1a7
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="select-clause-transact-sql"></a>Выражение SELECT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Указывает столбцы, возвращаемые запросом.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SELECT [ ALL | DISTINCT ]  
[ TOP ( expression ) [ PERCENT ] [ WITH TIES ] ]   
<select_list>   
<select_list> ::=   
    {   
      *   
      | { table_name | view_name | table_alias }.*   
      | {  
          [ { table_name | view_name | table_alias }. ]  
               { column_name | $IDENTITY | $ROWGUID }   
          | udt_column_name [ { . | :: } { { property_name | field_name }   
            | method_name ( argument [ ,...n] ) } ]  
          | expression  
          [ [ AS ] column_alias ]   
         }  
      | column_alias = expression   
    } [ ,...n ]   
```  
  
## <a name="arguments"></a>Аргументы  
 **ALL**  
 Указывает, что в результирующем наборе могут появиться повторяющиеся строки. ALL является параметром по умолчанию.  
  
 DISTINCT  
 Указывает, что в результирующем наборе могут появиться только уникальные строки. Значения NULL считаются равными для ключевого слова DISTINCT.  
  
 Начало (*выражение* ) [%] [WITH TIES]  
 Указывает на то, что только заданное число или процент строк будет возвращен из результирующего набора запроса. *expression* может быть либо числом, либо процентом от числа строк.  
  
 Для обеспечения обратной совместимости использование TOP *выражение* инструкции без скобок в инструкции SELECT поддерживается, но не рекомендуется. Дополнительные сведения см. в разделе [в начало &#40; Transact-SQL &#41; ](../../t-sql/queries/top-transact-sql.md).  
  
\<select_list > столбцы, выбираемые для результирующего набора. Список выбора представляет собой серию выражений, отделяемых запятыми. Максимальное число выражений, которое можно задать в списке выбора — 4 096.  
  
 \*  
 Указывает на то, что все столбцы из всех таблиц и представлений в предложении FROM должны быть возвращены. Столбцы возвращаются таблицей или представлением, как указано в предложении FROM, и в порядке, в котором они находятся в таблице или представлении.  
  
 *имя_таблицы* | *view_name* | *таблицы*_*псевдоним*. *  
 Ограничивает область \* для указанной таблицы или представления.  
  
 *column_name*  
 Имя возвращаемого столбца. Квалифицировать *column_name* во избежание неоднозначных ссылок, могут возникнуть, если в двух таблицах из предложения FROM имеют столбцы с повторяющимися именами. Например, таблицы SalesOrderHeader и SalesOrderDetail в [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] базы данных как есть столбец с именем ModifiedDate. Если в запросе соединяются две таблицы, то данные о дате изменения из таблицы SalesOrderDetail могут быть заданы в списке выбора как SalesOrderDetail.ModifiedDate.  
  
 *expression*  
 Является константой, функцией, любым сочетанием имен столбцов, констант и функций, соединенных оператором (операторами) или вложенным запросом.  
  
 $IDENTITY  
 Возвращает столбец идентификатора. Дополнительные сведения см. в разделе [УДОСТОВЕРЕНИЕ &#40; Свойство &#41; &#40; Transact-SQL &#41; ](../../t-sql/statements/create-table-transact-sql-identity-property.md), [ALTER таблицы &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-table-transact-sql.md), и [создание таблицы &#40; Transact-SQL &#41; ](../../t-sql/statements/create-table-transact-sql.md).  
  
 Если более чем одна таблица из предложения FROM содержит столбец со свойством IDENTITY, $IDENTITY должно быть задано с определенным именем таблицы, например T1.$IDENTITY.  
  
 $ROWGUID  
 Возвращает столбец с идентификаторами GUID строки.  
  
 Если более чем одна таблица из предложения FROM содержит столбец со свойством ROWGUIDCOL, $ROWGUIDCOL должно быть задано с определенным именем таблицы, например T1.$IDENTITY.  
  
 *udt_column_name*  
 Имя возвращаемого, определяемого пользователем типа данных CLR столбца.  
  
> [!NOTE]  
>  Среда [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] возвращает значения определяемого пользователем типа в двоичном представлении. Чтобы вернуть значения определяемого пользователем типа в строке или в формате XML, используйте [ПРИВЕДЕНИЯ](../../t-sql/functions/cast-and-convert-transact-sql.md) или [преобразовать](../../t-sql/functions/cast-and-convert-transact-sql.md).  
  
 { . | :: }  
 Указывает метод, свойство или поле пользовательского типа CLR. Используете. для метода экземпляра (нестатического), свойство или поле. Используйте:: для статического метода, свойства или поля. Для обращения к методу, свойству или полю определяемого пользователем типа среды CLR необходимо разрешение EXECUTE для этого типа.  
  
 *property_name*  
 Представляет открытое свойство *udt_column_name*.  
  
 *имя_поля*  
 Является членом открытых данных *udt_column_name*.  
  
 *имя_метода*  
 — Это открытый метод *udt_column_name* , принимающий один или несколько аргументов. *имя_метода* не может быть методом мутатора.  
  
 В следующем примере выбираются значения столбца `Location`, определенного типом `point`, из таблицы `Cities` путем обращения к методу типа, названного `Distance`:  
  
```  
CREATE TABLE dbo.Cities (  
     Name varchar(20),  
     State varchar(20),  
     Location point );  
GO  
DECLARE @p point (32, 23), @distance float;  
GO  
SELECT Location.Distance (@p)  
FROM Cities;  
```  
  
 *псевдоним column_*  
 Альтернативное имя, которым можно заменить имя столбца в результирующем наборе запроса. Например, для столбца «quantity» может быть указан псевдоним «Quantity», «Quantity to Date» или «Qty».  
  
 Кроме того, псевдонимы используются для указания имен для результатов выражений, например:  
  
 `USE AdventureWorks2012`;  
  
 `GO`  
  
 `SELECT AVG(UnitPrice) AS [Average Price]`  
  
 `FROM Sales.SalesOrderDetail;`  
  
 *column_alias* может использоваться в предложении ORDER BY. Однако он не может быть использован в предложениях WHERE, GROUP BY или HAVING. Если выражение запроса является частью инструкции DECLARE CURSOR, *псевдоним_столбца* не может использоваться в предложении FOR UPDATE.  
  
## <a name="remarks"></a>Замечания  
 Длина возвращаемых данных для **текст** или **ntext** столбцов, включенных в список выбора устанавливается в минимальное значение из следующих: фактический размер **текста** столбец, TEXTSIZE сеанса по умолчанию или жестко запрограммированное ограничение. Чтобы изменить длину возвращаемого текста для сеанса, используйте инструкцию SET. По умолчанию ограничение на длину возвращаемых при помощи инструкции SELECT текстовых данных равно 4 000 байт.  
  
 Компонент [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] вызывает исключение номер 511 и осуществляет откат транзакции до момента выполнения текущей инструкции, если наблюдается одно из следующих явлений.  
  
-   Следствием инструкции SELECT является строка результата или строка промежуточной таблицы, превышающая 8 060 байт.  
  
-   Инструкции DELETE, INSERT или UPDATE производят действия со строкой, превышающей 8 060 байт.  
  
 Ошибка возникает в случае, если не указано имя столбца, созданного при помощи инструкции SELECT INTO или CREATE VIEW.  
  
## <a name="see-also"></a>См. также:  
 [ВЫБЕРИТЕ примеры &#40; Transact-SQL &#41;](../../t-sql/queries/select-examples-transact-sql.md)   
 [Выражения &#40; Transact-SQL &#41;](../../t-sql/language-elements/expressions-transact-sql.md)   
 [SELECT (Transact-SQL)](../../t-sql/queries/select-transact-sql.md)  
  
  

