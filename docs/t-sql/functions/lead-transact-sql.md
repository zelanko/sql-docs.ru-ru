---
title: "LEAD (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 10/20/2015
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- LEAD_TSQL
- LEAD
dev_langs:
- TSQL
helpviewer_keywords:
- LEAD function
- analytic functions, LEAD
ms.assetid: 21f66bbf-d1ea-4f75-a3c4-20dc7fc1c69e
caps.latest.revision: 22
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: a5ec17dc2c38f040d6877cb69ac484ad56225a37
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="lead-transact-sql"></a>Предложение LEAD (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-all_md](../../includes/tsql-appliesto-ss2012-all-md.md)]

  Обращается к данным из последующей строки того же результирующего набора данных без использования самосоединения в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Функция LEAD обеспечивает доступ к строке на заданном физическом смещении после текущей строки. Используйте данную аналитическую функцию в инструкции SELECT для сравнения значений текущей строки со значениями из последующей.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "значок ссылки на раздел") [синтаксические обозначения Transact-SQL &#40; Transact-SQL &#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
LEAD ( scalar_expression [ ,offset ] , [ default ] )   
    OVER ( [ partition_by_clause ] order_by_clause )  
```  
  
## <a name="arguments"></a>Аргументы  
 *scalar_expression*  
 Возвращаемое значение основано на указанном смещении. Это выражение любого типа, возвращающее единичное (скалярное) значение. *scalar_expression* не может быть аналитической функцией.  
  
 *Смещение*  
 Количество строк перед текущей строкой, из которых необходимо получить значение. Если значение аргумента не указано, то по умолчанию принимается 1. *Смещение* может быть столбцом, вложенным запросом или другим выражением, результатом которого является положительным целым числом или может быть неявно преобразован в **bigint**. *Смещение* не может быть отрицательным значением или аналитической функцией.  
  
 *по умолчанию*  
 Значение, возвращаемое при *scalar_expression* в *смещение* имеет значение NULL. Если значение по умолчанию не задано, то возвращается NULL. *по умолчанию* может быть столбцом, вложенным запросом или другим выражением, но не может быть аналитической функцией. *по умолчанию* должно быть совместимо по типу с *scalar_expression*.  
  
 НАД **(** [ *partition_by_clause* ] *order_by_clause***)**  
 *partition_by_clause* Делит результирующий набор, полученный с помощью предложения FROM, на секции, к которым применяется функция. Если этот параметр не указан, функция обрабатывает все строки результирующего набора запроса как отдельные группы. *order_by_clause* определяет порядок данных перед применением функции. Когда *partition_by_clause* задан, он определяет порядок данных в каждой секции. *Order_by_clause* является обязательным. Дополнительные сведения см. в разделе [предложение OVER &#40; Transact-SQL &#41; ](../../t-sql/queries/select-over-clause-transact-sql.md).  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 Тип данных указанного *scalar_expression*. Если возвращается значение NULL *scalar_expression* допускает значение NULL или *по умолчанию* имеет значение NULL.  
  
 Функция LEAD не детерминирована. Дополнительные сведения см. в разделе [Deterministic and Nondeterministic Functions](../../relational-databases/user-defined-functions/deterministic-and-nondeterministic-functions.md).  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-compare-values-between-years"></a>A. Сравнение значений по годам  
 В запросе используется функция LEAD для возврата разности в квотах продаж для указанного работника за последующие годы. Обратите внимание, что для последней строки возвращается значение по умолчанию, т. е. нуль (0), так как для нее последующие значения отсутствуют.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT BusinessEntityID, YEAR(QuotaDate) AS SalesYear, SalesQuota AS CurrentQuota,   
    LEAD(SalesQuota, 1,0) OVER (ORDER BY YEAR(QuotaDate)) AS NextQuota  
FROM Sales.SalesPersonQuotaHistory  
WHERE BusinessEntityID = 275 and YEAR(QuotaDate) IN ('2005','2006');  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
  
BusinessEntityID SalesYear   CurrentQuota          NextQuota  
---------------- ----------- --------------------- ---------------------  
275              2005        367000.00             556000.00  
275              2005        556000.00             502000.00  
275              2006        502000.00             550000.00  
275              2006        550000.00             1429000.00  
275              2006        1429000.00            1324000.00  
275              2006        1324000.00            0.00  
```  
  
### <a name="b-compare-values-within-partitions"></a>Б. Сравнение значений внутри секций  
 В следующем примере функция LEAD используется для сравнения объемов продаж за текущий год между сотрудниками. Предложение PARTITION BY указывается для секционирования строк результирующего набора по территориям продаж. Функция LEAD применяется к каждой секции отдельно, и вычисление начинается заново для каждой секции. Предложение ORDER BY, указанное в предложении OVER, сортирует строки в каждой из секций перед применением функции. Предложение ORDER BY в инструкции SELECT упорядочивает строки во всем результирующем наборе. Обратите внимание, что для последней строки каждой секции возвращается значение по умолчанию, т. е. нуль (0), так как последующее значение для последней строки отсутствует.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT TerritoryName, BusinessEntityID, SalesYTD,   
       LEAD (SalesYTD, 1, 0) OVER (PARTITION BY TerritoryName ORDER BY SalesYTD DESC) AS NextRepSales  
FROM Sales.vSalesPerson  
WHERE TerritoryName IN (N'Northwest', N'Canada')   
ORDER BY TerritoryName;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
  
TerritoryName            BusinessEntityID SalesYTD              NextRepSales  
-----------------------  ---------------- --------------------- ---------------------  
Canada                   282              2604540.7172          1453719.4653  
Canada                   278              1453719.4653          0.00  
Northwest                284              1576562.1966          1573012.9383  
Northwest                283              1573012.9383          1352577.1325  
Northwest                280              1352577.1325          0.00  
  
```  
  
### <a name="c-specifying-arbitrary-expressions"></a>В. Указание произвольных выражений  
 В следующем примере демонстрируется указание ряда произвольных выражений в синтаксисе функции LEAD.  
  
```  
CREATE TABLE T (a int, b int, c int);   
GO  
INSERT INTO T VALUES (1, 1, -3), (2, 2, 4), (3, 1, NULL), (4, 3, 1), (5, 2, NULL), (6, 1, 5);   
  
SELECT b, c,   
    LEAD(2*c, b*(SELECT MIN(b) FROM T), -c/2.0) OVER (ORDER BY a) AS i  
FROM T;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
b           c           i  
----------- ----------- -----------  
1           -3          8  
2           4           2  
1           NULL        2  
3           1           0  
2           NULL        NULL  
1           5           -2  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="d-compare-values-between-quarters"></a>D: сравнение значений кварталов  
 В следующем примере функция LEAD. Запрос получает разницы между значениями квоты продаж для указанного работника за последующие календарного квартала. Обратите внимание, что так как не имеет смысла интереса после последней строки, используется значение по умолчанию, ноль (0).  
  
```  
-- Uses AdventureWorks  
  
SELECT CalendarYear AS Year, CalendarQuarter AS Quarter, SalesAmountQuota AS SalesQuota,  
       LEAD(SalesAmountQuota,1,0) OVER (ORDER BY CalendarYear, CalendarQuarter) AS NextQuota,  
   SalesAmountQuota - LEAD(Sale sAmountQuota,1,0) OVER (ORDER BY CalendarYear, CalendarQuarter) AS Diff  
FROM dbo.FactSalesQuota  
WHERE EmployeeKey = 272 AND CalendarYear IN (2001,2002)  
ORDER BY CalendarYear, CalendarQuarter;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `Year Quarter  SalesQuota  NextQuota  Diff`  
  
 `---- -------  ----------  ---------  -------------`  
  
 `2001 3        28000.0000   7000.0000   21000.0000`  
  
 `2001 4         7000.0000  91000.0000  -84000.0000`  
  
 `2001 1        91000.0000 140000.0000  -49000.0000`  
  
 `2002 2       140000.0000   7000.0000    7000.0000`  
  
 `2002 3         7000.0000 154000.0000   84000.0000`  
  
 `2002 4       154000.0000      0.0000  154000.0000`  
  
## <a name="see-also"></a>См. также:  
 [LAG &#40; Transact-SQL &#41;](../../t-sql/functions/lag-transact-sql.md)  
  
  



