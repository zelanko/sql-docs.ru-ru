---
title: "ГДЕ (Transact-SQL) | Документы Microsoft"
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
- WHERE_TSQL
- WHERE
dev_langs:
- TSQL
helpviewer_keywords:
- retrieving rows
- clauses [SQL Server], WHERE
- WHERE clause, about WHERE clause
- row retrieval [SQL Server], WHERE clause
- WHERE clause
ms.assetid: a8430421-7bce-4fab-a2d2-56c00a3c6fa4
caps.latest.revision: 37
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 5835510f37f52d57d2c23918a30dde10e7496a5d
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="where-transact-sql"></a>Предложение WHERE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Определяет условия поиска строк, возвращаемых запросом.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
[ WHERE <search_condition> ]  
```  
  
## <a name="arguments"></a>Аргументы  
\<*search_condition* > определяет условия, которые должны быть выполнены для возвращаемых строк. Количество предикатов, которое может содержать условие поиска, не ограничено. Дополнительные сведения об условиях поиска и предикатах см. в разделе [условие поиска &#40; Transact-SQL &#41; ](../../t-sql/queries/search-condition-transact-sql.md).  
  
## <a name="examples"></a>Примеры  
 В следующих примерах показывается, как можно использовать в предложении `WHERE` различные распространенные условия поиска.  
  
### <a name="a-finding-a-row-by-using-a-simple-equality"></a>A. Нахождение строки с помощью простого равенства  
  
```  
USE AdventureWorks2012  
GO  
SELECT ProductID, Name  
FROM Production.Product  
WHERE Name = 'Blade' ;  
GO  
```  
  
### <a name="b-finding-rows-that-contain-a-value-as-a-part-of-a-string"></a>Б. Нахождение строк, содержащих значение как часть строки  
  
```  
SELECT ProductID, Name, Color  
FROM Production.Product  
WHERE Name LIKE ('%Frame%');  
GO  
```  
  
### <a name="c-finding-rows-by-using-a-comparison-operator"></a>В. Нахождение строк с использованием оператора сравнения  
  
```  
SELECT ProductID, Name  
FROM Production.Product  
WHERE ProductID <= 12 ;  
GO  
```  
  
### <a name="d-finding-rows-that-meet-any-of-three-conditions"></a>Г. Нахождение строк, удовлетворяющих любому из трех условий  
  
```  
SELECT ProductID, Name  
FROM Production.Product  
WHERE ProductID = 2  
OR ProductID = 4   
OR Name = 'Spokes' ;  
GO  
```  
  
### <a name="e-finding-rows-that-must-meet-several-conditions"></a>Д. Нахождение строк, которые должны удовлетворять нескольким условиям  
  
```  
SELECT ProductID, Name, Color  
FROM Production.Product  
WHERE Name LIKE ('%Frame%')  
AND Name LIKE ('HL%')  
AND Color = 'Red' ;  
GO  
```  
  
### <a name="f-finding-rows-that-are-in-a-list-of-values"></a>Е. Нахождение строк, находящихся в списке значений  
  
```  
SELECT ProductID, Name, Color  
FROM Production.Product  
WHERE Name IN ('Blade', 'Crown Race', 'Spokes');  
GO  
```  
  
### <a name="g-finding-rows-that-have-a-value-between-two-values"></a>Ж. Нахождение строк, содержащих значение, расположенное между двумя значениями  
  
```  
SELECT ProductID, Name, Color  
FROM Production.Product  
WHERE ProductID BETWEEN 725 AND 734;  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 В следующих примерах показывается, как можно использовать в предложении `WHERE` различные распространенные условия поиска.  
  
### <a name="h-finding-a-row-by-using-a-simple-equality"></a>З. Нахождение строки с помощью простого равенства  
  
```  
-- Uses AdventureWorks  
  
SELECT EmployeeKey, LastName  
FROM DimEmployee  
WHERE LastName = 'Smith' ;  
```  
  
### <a name="i-finding-rows-that-contain-a-value-as-part-of-a-string"></a>И. Нахождение строк, содержащих значение как часть строки  
  
```  
-- Uses AdventureWorks  
  
SELECT EmployeeKey, LastName  
FROM DimEmployee  
WHERE LastName LIKE ('%Smi%');  
```  
  
### <a name="j-finding-rows-by-using-a-comparison-operator"></a>К. Нахождение строк с использованием оператора сравнения  
  
```  
-- Uses AdventureWorks  
  
SELECT EmployeeKey, LastName  
FROM DimEmployee  
WHERE EmployeeKey  <= 500;  
```  
  
### <a name="k-finding-rows-that-meet-any-of-three-conditions"></a>Л. Нахождение строк, удовлетворяющих любому из трех условий  
  
```  
-- Uses AdventureWorks  
  
SELECT EmployeeKey, LastName  
FROM DimEmployee  
WHERE EmployeeKey = 1 OR EmployeeKey = 8 OR EmployeeKey = 12;  
```  
  
### <a name="l-finding-rows-that-must-meet-several-conditions"></a>М. Нахождение строк, которые должны удовлетворять нескольким условиям  
  
```  
-- Uses AdventureWorks  
  
SELECT EmployeeKey, LastName  
FROM DimEmployee  
WHERE EmployeeKey <= 500 AND LastName LIKE '%Smi%' AND FirstName LIKE '%A%';  
```  
  
### <a name="m-finding-rows-that-are-in-a-list-of-values"></a>Н. Нахождение строк, находящихся в списке значений  
  
```  
-- Uses AdventureWorks  
  
SELECT EmployeeKey, LastName  
FROM DimEmployee  
WHERE LastName IN ('Smith', 'Godfrey', 'Johnson');  
```  
  
### <a name="n-finding-rows-that-have-a-value-between-two-values"></a>О. Нахождение строк, содержащих значение, расположенное между двумя значениями  
  
```  
-- Uses AdventureWorks  
  
SELECT EmployeeKey, LastName  
FROM DimEmployee  
WHERE EmployeeKey Between 100 AND 200;  
```  
  
## <a name="see-also"></a>См. также:  
 [DELETE (Transact-SQL)](../../t-sql/statements/delete-transact-sql.md)   
 [Предикаты &#40; Transact-SQL &#41;](~/t-sql/queries/predicates.md)   
 [Условие поиска &#40; Transact-SQL &#41;](../../t-sql/queries/search-condition-transact-sql.md)   
 [SELECT (Transact-SQL)](../../t-sql/queries/select-transact-sql.md)   
 [UPDATE (Transact-SQL)](../../t-sql/queries/update-transact-sql.md)   
 [MERGE (Transact-SQL)](../../t-sql/statements/merge-transact-sql.md)  
  
  



