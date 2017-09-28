---
title: "(Деление) (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- /
- /_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- / (divide)
- division [SQL Server]
- divide operator (/)
ms.assetid: 1d69893b-e5c3-441d-8dd8-0e5eb872ecfc
caps.latest.revision: 45
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: e3e8a94a92ca592ce6a2deb5d13915606f04f984
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="divide-transact-sql"></a>(Деление) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Выполняет деление одного числа на другое (арифметический оператор деления).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
dividend / divisor  
```  
  
## <a name="arguments"></a>Аргументы  
 *dividend*  
 Делимое числовое выражение. *делимое* может быть любым допустимым [выражение](../../t-sql/language-elements/expressions-transact-sql.md) одного из типов данных числового типа данных, за исключением **datetime** и **smalldatetime** типы данных.  
  
 *divisor*  
 Числовое выражение, на которое делится делимое. *делитель* может быть любое допустимое выражение любого из типов данных категории числовых типов данных, за исключением **datetime** и **smalldatetime** типов данных.  
  
## <a name="result-types"></a>Типы результата  
 Возвращает результат типа данных аргумента с более высоким приоритетом. Дополнительные сведения см. в разделе [Приоритет типов данных (Transact-SQL)](../../t-sql/data-types/data-type-precedence-transact-sql.md).  
  
 Если целое число *делимое* делится на целое число *делитель*, результатом является целочисленная дробная часть усечена.  
  
## <a name="remarks"></a>Замечания  
 Фактическое значение, возвращаемое оператором /, представляет собой частное от деления первого выражения на второе.  
  
## <a name="examples"></a>Примеры  
 В следующем примере арифметический оператор деления используется для вычисления целевого объема продаж за месяц для персонала по продажам из [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)].  
  
```  
-- Uses AdventureWorks  
  
SELECT s.BusinessEntityID AS SalesPersonID, FirstName, LastName, SalesQuota, SalesQuota/12 AS 'Sales Target Per Month'  
FROM Sales.SalesPerson AS s   
JOIN HumanResources.Employee AS e   
    ON s.BusinessEntityID = e.BusinessEntityID  
JOIN Person.Person AS p   
    ON e.BusinessEntityID = p.BusinessEntityID;  
```  
  
 Здесь приводится частичный результирующий набор.  
  
```  
  
SalesPersonID FirstName    LastName          SalesQuota  Sales Target Per Month  
------------- ------------ ----------------- ----------- ------------------  
274           Stephen      Jiang             NULL        NULL  
275           Michael      Blythe            300000.00   25000.00  
276           Linda        Mitchell          250000.00   20833.3333  
277           Jillian      Carson            250000.00   20833.3333  
  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 В следующем примере арифметический оператор деления используется для вычисления доли простой о количестве часов отпуска для часов отсутствия по болезни каждого сотрудника.  
  
```  
-- Uses AdventureWorks  
  
SELECT FirstName, LastName, VacationHours/SickLeaveHours AS PersonalTimeRatio  
FROM DimEmployee;  
  
```  
  
## <a name="see-also"></a>См. также:  
 [Типы данных (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md)   
 [Встроенные функции (Transact-SQL)](~/t-sql/functions/functions.md)   
 [Операторы &#40; Transact-SQL &#41;](../../t-sql/language-elements/operators-transact-sql.md)   
 [SELECT (Transact-SQL)](../../t-sql/queries/select-transact-sql.md)   
 [ГДЕ &#40; Transact-SQL &#41;](../../t-sql/queries/where-transact-sql.md)   
 [&#40; разделить равно &#41; &#40; Transact-SQL &#41;](../../t-sql/language-elements/divide-equals-transact-sql.md)   
 [Составные операторы &#40; Transact-SQL &#41;](../../t-sql/language-elements/compound-operators-transact-sql.md)  
  
  



