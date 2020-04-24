---
title: WHERE (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 08/09/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
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
author: VanMSFT
ms.author: vanto
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 77c80984ec2224e59a01184220c93cbc2eda8721
ms.sourcegitcommit: 8ffc23126609b1cbe2f6820f9a823c5850205372
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2020
ms.locfileid: "81632866"
---
# <a name="where-transact-sql"></a>Предложение WHERE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Определяет условия поиска строк, возвращаемых запросом.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```syntaxsql
[ WHERE <search_condition> ]  
```  
  
## <a name="arguments"></a>Аргументы  
\< *search_condition* > Определяет условия, которые должны быть выполнены для всех возвращаемых строк. Количество предикатов, которое может содержать условие поиска, не ограничено. Дополнительные сведения об условиях поиска и предикатах см. в статье [Условие поиска (Transact-SQL)](../../t-sql/queries/search-condition-transact-sql.md).  
  
## <a name="examples"></a>Примеры  
 В следующих примерах показывается, как можно использовать в предложении `WHERE` различные распространенные условия поиска.  
  
### <a name="a-finding-a-row-by-using-a-simple-equality"></a>A. Нахождение строки с помощью простого равенства  
  
```  
-- Uses AdventureWorksDW  
  
SELECT EmployeeKey, LastName  
FROM DimEmployee  
WHERE LastName = 'Smith' ;  
```  
  
### <a name="b-finding-rows-that-contain-a-value-as-part-of-a-string"></a>Б. Нахождение строк, содержащих значение как часть строки  
  
```  
-- Uses AdventureWorksDW  
  
SELECT EmployeeKey, LastName  
FROM DimEmployee  
WHERE LastName LIKE ('%Smi%');  
```  
  
### <a name="c-finding-rows-by-using-a-comparison-operator"></a>В. Нахождение строк с использованием оператора сравнения  
  
```  
-- Uses AdventureWorksDW  
  
SELECT EmployeeKey, LastName  
FROM DimEmployee  
WHERE EmployeeKey  <= 500;  
```  
  
### <a name="d-finding-rows-that-meet-any-of-three-conditions"></a>Г. Нахождение строк, удовлетворяющих любому из трех условий  
  
```  
-- Uses AdventureWorksDW  
  
SELECT EmployeeKey, LastName  
FROM DimEmployee  
WHERE EmployeeKey = 1 OR EmployeeKey = 8 OR EmployeeKey = 12;  
```  
  
### <a name="e-finding-rows-that-must-meet-several-conditions"></a>Д. Нахождение строк, которые должны удовлетворять нескольким условиям  
  
```  
-- Uses AdventureWorksDW  
  
SELECT EmployeeKey, LastName  
FROM DimEmployee  
WHERE EmployeeKey <= 500 AND LastName LIKE '%Smi%' AND FirstName LIKE '%A%';  
```  
  
### <a name="f-finding-rows-that-are-in-a-list-of-values"></a>Е. Нахождение строк, находящихся в списке значений  
  
```  
-- Uses AdventureWorksDW  
  
SELECT EmployeeKey, LastName  
FROM DimEmployee  
WHERE LastName IN ('Smith', 'Godfrey', 'Johnson');  
```  
  
### <a name="g-finding-rows-that-have-a-value-between-two-values"></a>Ж. Нахождение строк, содержащих значение, расположенное между двумя значениями  
  
```  
-- Uses AdventureWorksDW  
  
SELECT EmployeeKey, LastName  
FROM DimEmployee  
WHERE EmployeeKey Between 100 AND 200;  
```  
  
## <a name="see-also"></a>См. также:  
 [DELETE (Transact-SQL)](../../t-sql/statements/delete-transact-sql.md)   
 [Предикаты (Transact-SQL)](~/t-sql/queries/predicates.md)   
 [Условие поиска (Transact-SQL)](../../t-sql/queries/search-condition-transact-sql.md)   
 [SELECT (Transact-SQL)](../../t-sql/queries/select-transact-sql.md)   
 [UPDATE (Transact-SQL)](../../t-sql/queries/update-transact-sql.md)   
 [MERGE (Transact-SQL)](../../t-sql/statements/merge-transact-sql.md)  
  
  


