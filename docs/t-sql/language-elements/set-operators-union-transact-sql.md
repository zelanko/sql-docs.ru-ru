---
title: "UNION (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 08/07/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- UNION
- UNION_TSQL
dev_langs: TSQL
helpviewer_keywords:
- UNION queries
- combining query results
- UNION operator [SQL Server]
ms.assetid: 607c296f-8a6a-49bc-975a-b8d0c0914df7
caps.latest.revision: "34"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: 04f90ae1f5976e29a8281cab3638b63f0525f454
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="set-operators---union-transact-sql"></a>Операторы работы с наборами - UNION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Объединяет результаты двух или более запросов в один результирующий набор, в который входят все строки, принадлежащие всем запросам в объединении. Операция UNION отличается от соединений столбцов из двух таблиц.  
  
 Ниже приведены основные правила объединения результирующих наборов двух запросов с помощью операции UNION:  
  
-   количество и порядок столбцов должны быть одинаковыми во всех запросах;  
  
-   типы данных должны быть совместимыми.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
    { <query_specification> | ( <query_expression> ) }   
  UNION [ ALL ]   
  <query_specification | ( <query_expression> )   
 [ UNION [ ALL ] <query_specification> | ( <query_expression> )   
    [ ...n ] ]   
```  
  
## <a name="arguments"></a>Аргументы  
\<query_specification > | ( \<query_expression >) — это спецификация запроса или выражение запроса, возвращающее данные для объединения с данными из другой спецификации запроса или запроса выражения. Определения столбцов, которые являются частью операции UNION, не должны совпадать, однако должны быть совместимыми посредством неявного преобразования. Если типы данных различаются, тип данных результата определяется на основе правил для [приоритетов типов данных](../../t-sql/data-types/data-type-precedence-transact-sql.md). Если типы одинаковы, но различаются по точности, масштабу или длине, результат определяется на основе тех же самых правил, которые действуют при объединении выражений. Дополнительные сведения см. в разделе [Точность, масштаб и длина (Transact-SQL)](../../t-sql/data-types/precision-scale-and-length-transact-sql.md).  
  
 Столбцы **xml** тип данных должны быть эквивалентными. Все столбцы должны либо иметь тип, определенный в XML-схеме, либо быть нетипизированными. Типизированные столбцы должны относиться к одной и той же коллекции XML-схем.  
  
 UNION  
 Указывает на то, что несколько результирующих наборов следует объединить и возвратить в виде единого результирующего набора.  
  
 ALL  
 Объединяет в результирующий набор все строки. Это относится и к дублирующимся строкам. Если обратное не указано, дубликаты строк удаляются.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-using-a-simple-union"></a>A. Использование простого UNION  
 При выполнении следующего примера в результирующий набор включается содержимое столбцов `ProductModelID` и `Name` таблиц `ProductModel` и `Gloves`.  
  
```  
-- Uses AdventureWorks  
  
IF OBJECT_ID ('dbo.Gloves', 'U') IS NOT NULL  
DROP TABLE dbo.Gloves;  
GO  
-- Create Gloves table.  
SELECT ProductModelID, Name  
INTO dbo.Gloves  
FROM Production.ProductModel  
WHERE ProductModelID IN (3, 4);  
GO  
  
-- Here is the simple union.  
-- Uses AdventureWorks  
  
SELECT ProductModelID, Name  
FROM Production.ProductModel  
WHERE ProductModelID NOT IN (3, 4)  
UNION  
SELECT ProductModelID, Name  
FROM dbo.Gloves  
ORDER BY Name;  
GO  
```  
  
### <a name="b-using-select-into-with-union"></a>Б. Использование SELECT INTO с UNION  
 При выполнении следующего примера предложение `INTO` во второй инструкции `SELECT` указывает, что в таблице с именем `ProductResults` содержится итоговый результирующий набор объединения заданных столбцов таблиц `ProductModel` и `Gloves`. Заметим, что таблица `Gloves` была создана в результате выполнения первой инструкции `SELECT`.  
  
```  
-- Uses AdventureWorks  
  
IF OBJECT_ID ('dbo.ProductResults', 'U') IS NOT NULL  
DROP TABLE dbo.ProductResults;  
GO  
IF OBJECT_ID ('dbo.Gloves', 'U') IS NOT NULL  
DROP TABLE dbo.Gloves;  
GO  
-- Create Gloves table.  
SELECT ProductModelID, Name  
INTO dbo.Gloves  
FROM Production.ProductModel  
WHERE ProductModelID IN (3, 4);  
GO  
  
-- Uses AdventureWorks  
  
SELECT ProductModelID, Name  
INTO dbo.ProductResults  
FROM Production.ProductModel  
WHERE ProductModelID NOT IN (3, 4)  
UNION  
SELECT ProductModelID, Name  
FROM dbo.Gloves;  
GO  
  
SELECT ProductModelID, Name   
FROM dbo.ProductResults;  
  
```  
  
### <a name="c-using-union-of-two-select-statements-with-order-by"></a>В. Использование UNION двух инструкций SELECT с ORDER BY  
 При использовании предложения UNION необходимо соблюдать порядок следования определенных параметров. В следующем примере показаны случаи правильного и неверного использования `UNION` в двух инструкциях `SELECT`, в которых необходимо переименовать столбцы на выходе.  
  
```  
-- Uses AdventureWorks  
  
IF OBJECT_ID ('dbo.Gloves', 'U') IS NOT NULL  
DROP TABLE dbo.Gloves;  
GO  
-- Create Gloves table.  
SELECT ProductModelID, Name  
INTO dbo.Gloves  
FROM Production.ProductModel  
WHERE ProductModelID IN (3, 4);  
GO  
  
/* INCORRECT */  
-- Uses AdventureWorks  
  
SELECT ProductModelID, Name  
FROM Production.ProductModel  
WHERE ProductModelID NOT IN (3, 4)  
ORDER BY Name  
UNION  
SELECT ProductModelID, Name  
FROM dbo.Gloves;  
GO  
  
/* CORRECT */  
-- Uses AdventureWorks  
  
SELECT ProductModelID, Name  
FROM Production.ProductModel  
WHERE ProductModelID NOT IN (3, 4)  
UNION  
SELECT ProductModelID, Name  
FROM dbo.Gloves  
ORDER BY Name;  
GO  
  
```  
  
### <a name="d-using-union-of-three-select-statements-to-show-the-effects-of-all-and-parentheses"></a>Г. Использование UNION трех инструкций SELECT для демонстрации эффекта от использования скобок и ALL  
 В следующих примерах предложение `UNION` используется для комбинирования результатов из трех таблиц, содержащих по 5 одинаковых строк данных. В первом примере используется предложение `UNION ALL`, в результате чего выдаются все 15 строк. Во втором примере предложение `UNION` используется без ключевого слова `ALL`, что позволяет удалить повторяющиеся строки из комбинированного результата выполнения трех инструкций `SELECT` и вывести только 5 строк.  
  
 В третьем примере с первым предложением `ALL` используется ключевое слово `UNION`, а во втором предложении `UNION` вместо ключевого слова `ALL` используются скобки. Сначала выполняется второе предложение `UNION`, которое заключено в скобки. В результате возвращаются 5 строк, так как параметр `ALL` не используется и все повторяющиеся строки удаляются. Полученные 5 строк совмещаются с результатами выполнения первой инструкции `SELECT` с помощью ключевого слова `UNION ALL`. В данном случае повторяющиеся строки двух множеств не удаляются. Окончательный результат состоит из 10 строк.  
  
```  
-- Uses AdventureWorks  
  
IF OBJECT_ID ('dbo.EmployeeOne', 'U') IS NOT NULL  
DROP TABLE dbo.EmployeeOne;  
GO  
IF OBJECT_ID ('dbo.EmployeeTwo', 'U') IS NOT NULL  
DROP TABLE dbo.EmployeeTwo;  
GO  
IF OBJECT_ID ('dbo.EmployeeThree', 'U') IS NOT NULL  
DROP TABLE dbo.EmployeeThree;  
GO  
  
SELECT pp.LastName, pp.FirstName, e.JobTitle   
INTO dbo.EmployeeOne  
FROM Person.Person AS pp JOIN HumanResources.Employee AS e  
ON e.BusinessEntityID = pp.BusinessEntityID  
WHERE LastName = 'Johnson';  
GO  
SELECT pp.LastName, pp.FirstName, e.JobTitle   
INTO dbo.EmployeeTwo  
FROM Person.Person AS pp JOIN HumanResources.Employee AS e  
ON e.BusinessEntityID = pp.BusinessEntityID  
WHERE LastName = 'Johnson';  
GO  
SELECT pp.LastName, pp.FirstName, e.JobTitle   
INTO dbo.EmployeeThree  
FROM Person.Person AS pp JOIN HumanResources.Employee AS e  
ON e.BusinessEntityID = pp.BusinessEntityID  
WHERE LastName = 'Johnson';  
GO  
-- Union ALL  
SELECT LastName, FirstName, JobTitle  
FROM dbo.EmployeeOne  
UNION ALL  
SELECT LastName, FirstName ,JobTitle  
FROM dbo.EmployeeTwo  
UNION ALL  
SELECT LastName, FirstName,JobTitle   
FROM dbo.EmployeeThree;  
GO  
  
SELECT LastName, FirstName,JobTitle  
FROM dbo.EmployeeOne  
UNION   
SELECT LastName, FirstName, JobTitle   
FROM dbo.EmployeeTwo  
UNION   
SELECT LastName, FirstName, JobTitle   
FROM dbo.EmployeeThree;  
GO  
  
SELECT LastName, FirstName,JobTitle   
FROM dbo.EmployeeOne  
UNION ALL  
(  
SELECT LastName, FirstName, JobTitle   
FROM dbo.EmployeeTwo  
UNION  
SELECT LastName, FirstName, JobTitle   
FROM dbo.EmployeeThree  
);  
GO  
  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="e-using-a-simple-union"></a>Д. Использование простого UNION  
 В следующем примере результирующий набор включает в себя содержимое `CustomerKey` столбцы обоих `FactInternetSales` и `DimCustomer` таблицы. Так как не используется ключевое слово ALL, дубликаты исключаются из результатов.  
  
```  
-- Uses AdventureWorks  
  
SELECT CustomerKey   
FROM FactInternetSales    
UNION   
SELECT CustomerKey   
FROM DimCustomer   
ORDER BY CustomerKey;  
```  
  
### <a name="f-using-union-of-two-select-statements-with-order-by"></a>Е. Использование UNION двух инструкций SELECT с ORDER BY  
 Если любой инструкции SELECT в операторе UNION содержит предложение ORDER BY, это предложение должны находиться после всех инструкций SELECT. В следующем примере показано неправильное и правильное использование `UNION` в двух `SELECT` инструкций, в которых столбец упорядочивается с помощью предложения ORDER BY.  
  
```  
-- Uses AdventureWorks  
  
-- INCORRECT  
SELECT CustomerKey   
FROM FactInternetSales    
ORDER BY CustomerKey  
UNION   
SELECT CustomerKey   
FROM DimCustomer  
ORDER BY CustomerKey;  
  
-- CORRECT   
USE AdventureWorksPDW2012;  
  
SELECT CustomerKey   
FROM FactInternetSales    
UNION   
SELECT CustomerKey   
FROM DimCustomer   
ORDER BY CustomerKey;  
```  
  
### <a name="g-using-union-of-two-select-statements-with-where-and-order-by"></a>Ж. Использование UNION двух инструкций SELECT с WHERE и ORDER BY  
 В следующем примере показано неправильное и правильное использование `UNION` в двух `SELECT` инструкций там, где ГДЕ и ORDER BY должны использоваться.  
  
```  
-- Uses AdventureWorks  
  
-- INCORRECT   
SELECT CustomerKey   
FROM FactInternetSales   
WHERE CustomerKey >= 11000  
ORDER BY CustomerKey   
UNION   
SELECT CustomerKey   
FROM DimCustomer   
ORDER BY CustomerKey;  
  
-- CORRECT  
USE AdventureWorksPDW2012;  
  
SELECT CustomerKey   
FROM FactInternetSales   
WHERE CustomerKey >= 11000  
UNION   
SELECT CustomerKey   
FROM DimCustomer   
ORDER BY CustomerKey;  
```  
  
### <a name="h-using-union-of-three-select-statements-to-show-effects-of-all-and-parentheses"></a>З. Использование предложения UNION с тремя инструкциями SELECT для отображения всех влияния скобок и  
 В следующих примерах используется `UNION` для объединения результатов **той же таблице** для демонстрации результаты всех и круглые скобки, при использовании `UNION`.  
  
 В первом примере используется `UNION ALL` для отображения повторяющихся записей и возвращает каждая строка в исходной таблице три раза. Во втором примере `UNION` без `ALL` Чтобы удалить повторяющиеся строки из комбинированного результата выполнения трех `SELECT` инструкций и возвращает только те строки, unduplicated из исходной таблицы.  
  
 В третьем примере `ALL` с первым `UNION` и круглые скобки, включающий второй `UNION` , не использующем `ALL`. Второй `UNION` обрабатывается первой, так как он указан в скобках. Она возвращает только unduplicated строки из таблицы, так как `ALL` параметр не используется и удалять дубликаты. Эти строки объединяются с результатами выполнения первой `SELECT` с помощью `UNION ALL` ключевые слова. Это не удаляет дубликаты между двумя наборами.  
  
```  
-- Uses AdventureWorks  
  
SELECT CustomerKey, FirstName, LastName  
FROM DimCustomer  
UNION ALL   
SELECT CustomerKey, FirstName, LastName  
FROM DimCustomer  
UNION ALL   
SELECT CustomerKey, FirstName, LastName  
FROM DimCustomer;  
  
SELECT CustomerKey, FirstName, LastName  
FROM DimCustomer  
UNION   
SELECT CustomerKey, FirstName, LastName  
FROM DimCustomer  
UNION   
SELECT CustomerKey, FirstName, LastName  
FROM DimCustomer;  
  
SELECT CustomerKey, FirstName, LastName  
FROM DimCustomer  
UNION ALL  
(  
SELECT CustomerKey, FirstName, LastName  
FROM DimCustomer  
UNION   
SELECT CustomerKey, FirstName, LastName  
FROM DimCustomer  
);  
```  
  
## <a name="see-also"></a>См. также:  
 [SELECT (Transact-SQL)](../../t-sql/queries/select-transact-sql.md)   
 [ВЫБЕРИТЕ примеры &#40; Transact-SQL &#41;](../../t-sql/queries/select-examples-transact-sql.md)  
  
  

