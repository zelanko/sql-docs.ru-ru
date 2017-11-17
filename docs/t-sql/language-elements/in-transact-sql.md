---
title: "IN (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 08/29/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- IN_TSQL
- IN
dev_langs:
- TSQL
helpviewer_keywords:
- values [SQL Server], matching
- NOT IN keyword
- 8623 (Database Engine error)
- matching values in subquery or list [SQL Server]
- IN keyword
- 8632 (Database Engine error)
ms.assetid: 4419de73-96b1-4dfe-8500-f4507915db04
caps.latest.revision: 37
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 70b186107966791e29ccb76ea9c310724b76e3b6
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="in-transact-sql"></a>IN (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Определяет, совпадает ли указанное значение с одним из значений, содержащихся во вложенном запросе или списке.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
test_expression [ NOT ] IN   
    ( subquery | expression [ ,...n ]  
    )   
```  
  
## <a name="arguments"></a>Аргументы  
 *test_expression*  
 Любое допустимое [выражение](../../t-sql/language-elements/expressions-transact-sql.md).  
  
 *вложенный запрос*  
 Вложенный запрос, содержащий результирующий набор, состоящий из одного столбца. Этот столбец должен иметь тот же тип данных, *test_expression*.  
  
 *выражение*[ **,**... *n* ]  
 Список выражений для поиска совпадения. Все выражения должны иметь того же типа, что *test_expression*.  
  
## <a name="result-types"></a>Типы результата  
 **Логическое значение**  
  
## <a name="result-value"></a>Значение результата  
 Если значение *test_expression* равен любое значение, возвращаемое *вложенный запрос* или одному *выражение* из списка разделенных запятыми, результирующее значение равно TRUE. в противном случае результирующее значение равно FALSE.  
  
 Предложение NOT IN инвертирует *вложенный запрос* значение или *выражение*.  
  
> [!CAUTION]  
>  Пустые значения, возвращаемые методом *вложенный запрос* или *выражение* , по сравнению с *test_expression* с помощью предложения IN или NOT IN, возвращается UNKNOWN. Использование значений NULL с предложениями IN или NOT IN может привести к непредвиденным результатам.  
  
## <a name="remarks"></a>Замечания  
 Намеренное Включение очень большого количества значений (много тысяч значений, разделенных запятыми) в круглых скобках в предложение IN может использовать ресурсы и возвратить ошибки 8623 или 8632. Чтобы обойти эту проблему, храните элементы списка IN в таблице и использовать вложенный запрос SELECT внутри предложения.  
  
 Ошибки 8623:  
  
 `The query processor ran out of internal resources and could not produce a query plan. This is a rare event and only expected for extremely complex queries or queries that reference a very large number of tables or partitions. Please simplify the query. If you believe you have received this message in error, contact Customer Support Services for more information.`  
  
 Ошибка 8632.  
  
 `Internal error: An expression services limit has been reached. Please look for potentially complex expressions in your query, and try to simplify them.`  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-comparing-or-and-in"></a>A. Сравнение OR и IN  
 В следующем примере осуществляется выборка списка имен сотрудников на должностях инженеров-разработчиков, разработчиков средств и сотрудников отдела сбыта.  
  
```  
-- Uses AdventureWorks  
  
SELECT p.FirstName, p.LastName, e.JobTitle  
FROM Person.Person AS p  
JOIN HumanResources.Employee AS e  
    ON p.BusinessEntityID = e.BusinessEntityID  
WHERE e.JobTitle = 'Design Engineer'   
   OR e.JobTitle = 'Tool Designer'   
   OR e.JobTitle = 'Marketing Assistant';  
GO  
```  
  
 Этот же результат можно получить при помощи оператора IN.  
  
```  
-- Uses AdventureWorks  
  
SELECT p.FirstName, p.LastName, e.JobTitle  
FROM Person.Person AS p  
JOIN HumanResources.Employee AS e  
    ON p.BusinessEntityID = e.BusinessEntityID  
WHERE e.JobTitle IN ('Design Engineer', 'Tool Designer', 'Marketing Assistant');  
GO  
```  
  
 Ниже представлен результирующий набор, возвращаемый каждым из запросов.  
  
```  
FirstName   LastName      Title  
---------   ---------   ---------------------  
Sharon      Salavaria   Design Engineer                                     
Gail        Erickson    Design Engineer                                     
Jossef      Goldberg    Design Engineer                                     
Janice      Galvin      Tool Designer                                       
Thierry     D'Hers      Tool Designer                                       
Wanida      Benshoof    Marketing Assistant                                 
Kevin       Brown       Marketing Assistant                                 
Mary        Dempsey     Marketing Assistant                                 
  
(8 row(s) affected)  
```  
  
### <a name="b-using-in-with-a-subquery"></a>Б. Применение IN с вложенным запросом  
 В следующем примере осуществляется поиск идентификаторов менеджеров по продажам в таблице `SalesPerson`, имеющих объем продаж более 250 000 долларов в год, а затем выборка из таблицы `Employee` имен и фамилий всех сотрудников, идентификаторы `EmployeeID` которых совпадают с результатами вложенного запроса `SELECT`.  
  
```  
-- Uses AdventureWorks  
  
SELECT p.FirstName, p.LastName  
FROM Person.Person AS p  
    JOIN Sales.SalesPerson AS sp  
    ON p.BusinessEntityID = sp.BusinessEntityID  
WHERE p.BusinessEntityID IN  
   (SELECT BusinessEntityID  
   FROM Sales.SalesPerson  
   WHERE SalesQuota > 250000);  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
FirstName   LastName                                             
---------   --------   
Tsvi         Reiter                                              
Michael      Blythe                                              
Tete         Mensa-Annan                                         
  
(3 row(s) affected)  
```  
  
### <a name="c-using-not-in-with-a-subquery"></a>В. Применение NOT IN с вложенным запросом  
 В следующем примере производится поиск торговцев, квота которых не выше 250 000 долларов США. С помощью `NOT IN` можно найти торговцев, которые не соответствуют списку значений.  
  
```  
-- Uses AdventureWorks  
  
SELECT p.FirstName, p.LastName  
FROM Person.Person AS p  
    JOIN Sales.SalesPerson AS sp  
    ON p.BusinessEntityID = sp.BusinessEntityID  
WHERE p.BusinessEntityID NOT IN  
   (SELECT BusinessEntityID  
   FROM Sales.SalesPerson  
   WHERE SalesQuota > 250000);  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="d-using-in-and-not-in"></a>Г. Использование в и не поддерживается в  
 Следующий пример находит все операции в `FactInternetSales` таблицы, которые соответствуют `SalesReasonKey` значения в `DimSalesReason` таблицы.  
  
```  
-- Uses AdventureWorks  
  
SELECT * FROM FactInternetSalesReason   
WHERE SalesReasonKey   
IN (SELECT SalesReasonKey FROM DimSalesReason);   
```  
  
 Следующий пример находит все операции в `FactInternetSalesReason` таблицы, которые не совпадают `SalesReasonKey` значения в `DimSalesReason` таблицы.  
  
```  
-- Uses AdventureWorks  
  
SELECT * FROM FactInternetSalesReason   
WHERE SalesReasonKey   
NOT IN (SELECT SalesReasonKey FROM DimSalesReason);  
```  
  
### <a name="e-using-in-with-an-expression-list"></a>Д. С помощью вход с помощью списка выражений  
 В следующем примере осуществляется поиск идентификаторов менеджеров по продажам в `DimEmployee` таблица для сотрудников, имеющих первым именем, являющийся либо `Mike` или `Michael`.  
  
```  
-- Uses AdventureWorks  
  
SELECT FirstName, LastName  
FROM DimEmployee  
WHERE FirstName IN ('Mike', 'Michael');  
```  
  
## <a name="see-also"></a>См. также:  
 [РЕГИСТР &#40; Transact-SQL &#41;](../../t-sql/language-elements/case-transact-sql.md)   
 [Выражения &#40; Transact-SQL &#41;](../../t-sql/language-elements/expressions-transact-sql.md)   
 [Встроенные функции (Transact-SQL)](~/t-sql/functions/functions.md)   
 [Операторы &#40; Transact-SQL &#41;](../../t-sql/language-elements/operators-transact-sql.md)   
 [SELECT (Transact-SQL)](../../t-sql/queries/select-transact-sql.md)   
 [ГДЕ &#40; Transact-SQL &#41;](../../t-sql/queries/where-transact-sql.md)   
 [ВСЕ &#40; Transact-SQL &#41;](../../t-sql/language-elements/all-transact-sql.md)   
 [НЕКОТОРЫЕ &#124; ВСЕ &#40; Transact-SQL &#41;](../../t-sql/language-elements/some-any-transact-sql.md)  
  
  




