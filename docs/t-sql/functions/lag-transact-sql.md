---
title: "LAG (Transact-SQL) | Документы Microsoft"
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
- LAG_TSQL
- LAG
dev_langs:
- TSQL
helpviewer_keywords:
- LAG function
- analytic functions, LAG
ms.assetid: a9a90bdb-3f80-4c97-baca-b7407bcdc7f0
caps.latest.revision: 23
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 77598feb87f6766f6c24c454dace2c138315e69b
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="lag-transact-sql"></a>Предложение LAG (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-all_md](../../includes/tsql-appliesto-ss2012-all-md.md)]

  Обращается к данным из предыдущей строки того же результирующего набора без использования самосоединения в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Функция LAG обеспечивает доступ к строке с заданным физическим смещением перед началом текущей строки. Используйте данную аналитическую функцию в инструкции SELECT для сравнения значений текущей строки со значениями из предыдущей.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "значок ссылки на раздел") [синтаксические обозначения Transact-SQL &#40; Transact-SQL &#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
LAG (scalar_expression [,offset] [,default])  
    OVER ( [ partition_by_clause ] order_by_clause )  
```  
  
## <a name="arguments"></a>Аргументы  
 *scalar_expression*  
 Возвращаемое значение основано на указанном смещении. Это выражение любого типа, возвращающее единичное (скалярное) значение. *scalar_expression* не может быть аналитической функцией.  
  
 *Смещение*  
 Количество строк до строки перед текущей строкой, из которой необходимо получить значение. Если значение аргумента не указано, то по умолчанию принимается 1. *Смещение* может быть столбцом, вложенным запросом или другим выражением, результатом которого является положительным целым числом или может быть неявно преобразован в **bigint**. *Смещение* не может быть отрицательным значением или аналитической функцией.  
  
 *по умолчанию*  
 Значение, возвращаемое при *scalar_expression* в *смещение* имеет значение NULL. Если значение по умолчанию не задано, то возвращается NULL. *по умолчанию* может быть столбцом, вложенным запросом или другим выражением, но не может быть аналитической функцией. *по умолчанию* должно быть совместимо по типу с *scalar_expression*.  
  
 НАД **(** [ *partition_by_clause* ] *order_by_clause***)**  
 *partition_by_clause* Делит результирующий набор, полученный с помощью предложения FROM, на секции, к которым применяется функция. Если этот параметр не указан, функция обрабатывает все строки результирующего набора запроса как отдельные группы. *order_by_clause* определяет порядок данных перед применением функции. Если *partition_by_clause* задан, он определяет порядок данных в секции. *Order_by_clause* является обязательным. Дополнительные сведения см. в разделе [предложение OVER &#40; Transact-SQL &#41; ](../../t-sql/queries/select-over-clause-transact-sql.md).  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 Тип данных указанного *scalar_expression*. Если возвращается значение NULL *scalar_expression* допускает значение NULL или *по умолчанию* имеет значение NULL.  
  
## <a name="general-remarks"></a>Общие замечания  
 Функция LAG не детерминирована. Дополнительные сведения см. в разделе [Deterministic and Nondeterministic Functions](../../relational-databases/user-defined-functions/deterministic-and-nondeterministic-functions.md).  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-compare-values-between-years"></a>A. Сравнение значений по годам  
 В следующем примере показано использование функции LAG для возврата разности в квотах продаж для указанного работника за предыдущие годы. Обратите внимание, что для первой строки возвращается значение, установленное по умолчанию, т. е. нуль (0), так как значение за предыдущие периоды для нее недоступно.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT BusinessEntityID, YEAR(QuotaDate) AS SalesYear, SalesQuota AS CurrentQuota,   
       LAG(SalesQuota, 1,0) OVER (ORDER BY YEAR(QuotaDate)) AS PreviousQuota  
FROM Sales.SalesPersonQuotaHistory  
WHERE BusinessEntityID = 275 and YEAR(QuotaDate) IN ('2005','2006');  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
  
BusinessEntityID SalesYear   CurrentQuota          PreviousQuota  
---------------- ----------- --------------------- ---------------------  
275              2005        367000.00             0.00  
275              2005        556000.00             367000.00  
275              2006        502000.00             556000.00  
275              2006        550000.00             502000.00  
275              2006        1429000.00            550000.00  
275              2006        1324000.00            1429000.00  
  
```  
  
### <a name="b-compare-values-within-partitions"></a>Б. Сравнение значений внутри секций  
 В следующем примере используется функция LAG для сравнения количества продаж за текущий год между сотрудниками. Предложение PARTITION BY указывается для разделения строк результирующего набора по территориям продаж. Функция LAG применяется к каждой секции отдельно, а вычисление начинается заново для каждой секции. Предложение ORDER BY в предложении OVER упорядочивает строки в каждой секции. Предложение ORDER BY в инструкции SELECT сортирует сроки во всем результирующем наборе. Обратите внимание, что для первой строки возвращается значение, установленное по умолчанию, т. е. нуль (0), так как значение за предыдущий период для первой строки каждой секции недоступно.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT TerritoryName, BusinessEntityID, SalesYTD,   
       LAG (SalesYTD, 1, 0) OVER (PARTITION BY TerritoryName ORDER BY SalesYTD DESC) AS PrevRepSales  
FROM Sales.vSalesPerson  
WHERE TerritoryName IN (N'Northwest', N'Canada')   
ORDER BY TerritoryName;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
  
TerritoryName            BusinessEntityID SalesYTD              PrevRepSales  
-----------------------  ---------------- --------------------- ---------------------  
Canada                   282              2604540.7172          0.00  
Canada                   278              1453719.4653          2604540.7172  
Northwest                284              1576562.1966          0.00  
Northwest                283              1573012.9383          1576562.1966  
Northwest                280              1352577.1325          1573012.9383  
  
```  
  
### <a name="c-specifying-arbitrary-expressions"></a>В. Указание произвольных выражений  
 В следующем примере демонстрируется указание ряда произвольных выражений в синтаксисе функции LAG.  
  
```  
CREATE TABLE T (a int, b int, c int);   
GO  
INSERT INTO T VALUES (1, 1, -3), (2, 2, 4), (3, 1, NULL), (4, 3, 1), (5, 2, NULL), (6, 1, 5);   
  
SELECT b, c,   
    LAG(2*c, b*(SELECT MIN(b) FROM T), -c/2.0) OVER (ORDER BY a) AS i  
FROM T;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
b           c           i  
----------- ----------- -----------  
1           -3          1  
2           4           -2  
1           NULL        8  
3           1           -6  
2           NULL        NULL  
1           5           NULL  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="d-compare-values-between-quarters"></a>D: сравнение значений кварталов  
 В следующем примере функция LAG. В запросе используется функция LAG для возврата разности в квотах продаж для указанного работника за предыдущие календарных кварталов. Обратите внимание, что для первой строки возвращается значение, установленное по умолчанию, т. е. нуль (0), так как значение за предыдущие периоды для нее недоступно.  
  
```  
-- Uses AdventureWorks  
  
SELECT CalendarYear, CalendarQuarter, SalesAmountQuota AS SalesQuota,  
       LAG(SalesAmountQuota,1,0) OVER (ORDER BY CalendarYear, CalendarQuarter) AS PrevQuota,  
       SalesAmountQuota - LAG(SalesAmountQuota,1,0) OVER (ORDER BY CalendarYear, CalendarQuarter) AS Diff  
FROM dbo.FactSalesQuota  
WHERE EmployeeKey = 272 AND CalendarYear IN (2001, 2002)  
ORDER BY CalendarYear, CalendarQuarter;   
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
Year Quarter  SalesQuota  PrevQuota  Diff  
---- -------  ----------  ---------  -------------  
2001 3        28000.0000      0.0000   28000.0000  
2001 4         7000.0000  28000.0000  -21000.0000  
2001 1        91000.0000   7000.0000   84000.0000  
2002 2       140000.0000  91000.0000   49000.0000  
2002 3         7000.0000 140000.0000  -70000.0000  
2002 4       154000.0000   7000.0000   84000.0000
```  
  
## <a name="see-also"></a>См. также:  
 [РУКОВОДИТЕЛЬ &#40; Transact-SQL &#41;](../../t-sql/functions/lead-transact-sql.md)  
  
  



