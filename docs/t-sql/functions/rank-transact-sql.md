---
title: "Ранг (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 10/25/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- RANK
- RANK_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- row ranking [SQL Server]
- tied rows [SQL Server]
- ranking rows
- RANK function [Transact-SQL]
ms.assetid: 2d96f6d2-5db7-4b3c-a63e-213c58e4af55
caps.latest.revision: 62
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 304ceaedefe1755c56b27a8f6e64a922a1986bc0
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="rank-transact-sql"></a>RANK (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает ранг каждой строки в секции результирующего набора. Ранг строки вычисляется как единица плюс количество рангов, находящихся до этой строки.  

  ROW_NUMBER и ранг похожи. ROW_NUMBER номеров всех строк последовательно (например 1, 2, 3, 4, 5). Ранг предоставляет то же значение для связей (например 1, 2, 2, 4, 5).   
  
> [!NOTE]
> Ранг является временное значение рассчитывается при запуске запроса. Для хранения чисел в таблице, в разделе [свойство IDENTITY](../../t-sql/statements/create-table-transact-sql-identity-property.md) и [ПОСЛЕДОВАТЕЛЬНОСТИ](../../t-sql/statements/create-sequence-transact-sql.md). 
   
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
RANK ( ) OVER ( [ partition_by_clause ] order_by_clause )  
```  
  
## <a name="arguments"></a>Аргументы  
 НАД **(** [ *partition_by_clause* ] *order_by_clause***)**  
 *partition_by_clause* Делит результирующий набор, полученный с помощью предложения FROM, на секции, к которым применяется функция. Если этот параметр не указан, функция обрабатывает все строки результирующего набора запроса как отдельные группы. *order_by_clause* определяет порядок данных перед применением функции. *Order_by_clause* является обязательным. \<Строки или предложение диапазона > из более ЧЕМ для функция RANK не может быть указано предложение. Дополнительные сведения см. в разделе [предложение OVER &#40; Transact-SQL &#41; ](../../t-sql/queries/select-over-clause-transact-sql.md).  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 **bigint**  
  
## <a name="remarks"></a>Замечания  
 Если две и более строки претендуют на один ранг, то все они получат одинаковый ранг. Например, если двум лучшим продавцам соответствует одинаковое значение SalesYTD, им обоим присваивается ранг 1. Менеджер по продажам со следующим по величине значением SalesYTD получит ранг номер три, так как перед ним находятся две строки с более высоким рангом. Поэтому функция RANK не всегда возвращает последовательные целые числа.  
  
 Порядок сортировки, используемый для всего запроса, определяет порядок, в котором строки будут появляться в результирующем наборе.  
  
 Функция RANK не детерминирована. Дополнительные сведения см. в разделе [Deterministic and Nondeterministic Functions](../../relational-databases/user-defined-functions/deterministic-and-nondeterministic-functions.md).  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-ranking-rows-within-a-partition"></a>A. Ранжирование строк внутри секции  
 Следующий пример ранжирует продукты по количеству в указанных местоположениях в описи. Результирующий набор секционируется по `LocationID` и логически сортируется по `Quantity`. Обратите внимание, что количество продуктов 494 и 495 совпадает. Так как они занимают одно и то же место, рейтинг обоих продуктов равен единице.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT i.ProductID, p.Name, i.LocationID, i.Quantity  
    ,RANK() OVER   
    (PARTITION BY i.LocationID ORDER BY i.Quantity DESC) AS Rank  
FROM Production.ProductInventory AS i   
INNER JOIN Production.Product AS p   
    ON i.ProductID = p.ProductID  
WHERE i.LocationID BETWEEN 3 AND 4  
ORDER BY i.LocationID;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
  
ProductID   Name                   LocationID   Quantity Rank  
----------- ---------------------- ------------ -------- ----  
494         Paint - Silver         3            49       1  
495         Paint - Blue           3            49       1  
493         Paint - Red            3            41       3  
496         Paint - Yellow         3            30       4  
492         Paint - Black          3            17       5  
495         Paint - Blue           4            35       1  
496         Paint - Yellow         4            25       2  
493         Paint - Red            4            24       3  
492         Paint - Black          4            14       4  
494         Paint - Silver         4            12       5  
 (10 row(s) affected)  
```  
  
### <a name="b-ranking-all-rows-in-a-result-set"></a>Б. Ранжирование всех строк в результирующем наборе  
 Следующий пример возвращает список первых десяти сотрудников, отранжированных по их окладу. Поскольку предложение PARTITION BY не указывалось, функция RANK применялась ко всем строкам результирующего набора.  
  
```  
USE AdventureWorks2012  
SELECT TOP(10) BusinessEntityID, Rate,   
       RANK() OVER (ORDER BY Rate DESC) AS RankBySalary  
FROM HumanResources.EmployeePayHistory AS eph1  
WHERE RateChangeDate = (SELECT MAX(RateChangeDate)   
                        FROM HumanResources.EmployeePayHistory AS eph2  
                        WHERE eph1.BusinessEntityID = eph2.BusinessEntityID)  
ORDER BY BusinessEntityID;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
BusinessEntityID Rate                  RankBySalary  
---------------- --------------------- --------------------  
1                125.50                1  
2                63.4615               4  
3                43.2692               8  
4                29.8462               19  
5                32.6923               16  
6                32.6923               16  
7                50.4808               6  
8                40.8654               10  
9                40.8654               10  
10               42.4808               9  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-ranking-rows-within-a-partition"></a>C: ранжирование строк внутри секции  
 Следующий пример ранжирует коммерческих представителей в каждой территории продаж в соответствии с общего объема продаж. Набор строк секционируется по столбцу `SalesTerritoryGroup` и сортируется по столбцу `SalesAmountQuota`.  
  
```  
-- Uses AdventureWorks  
  
SELECT LastName, SUM(SalesAmountQuota) AS TotalSales, SalesTerritoryRegion,  
    RANK() OVER (PARTITION BY SalesTerritoryRegion ORDER BY SUM(SalesAmountQuota) DESC ) AS RankResult  
FROM dbo.DimEmployee AS e  
INNER JOIN dbo.FactSalesQuota AS sq ON e.EmployeeKey = sq.EmployeeKey  
INNER JOIN dbo.DimSalesTerritory AS st ON e.SalesTerritoryKey = st.SalesTerritoryKey  
WHERE SalesPersonFlag = 1 AND SalesTerritoryRegion != N'NA'  
GROUP BY LastName, SalesTerritoryRegion;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```
LastName          TotalSales     SalesTerritoryGroup  RankResult
----------------  -------------  -------------------  --------
Tsoflias          1687000.0000   Australia            1
Saraiva           7098000.0000   Canada               1
Vargas            4365000.0000   Canada               2
Carson            12198000.0000  Central              1
Varkey Chudukatil 5557000.0000   France               1
Valdez            2287000.0000   Germany              1
Blythe            11162000.0000  Northeast            1
Campbell          4025000.0000   Northwest            1
Ansman-Wolfe      3551000.0000   Northwest            2
Mensa-Annan       2753000.0000   Northwest            3
Reiter            8541000.0000   Southeast            1
Mitchell          11786000.0000  Southwest            1
Ito               7804000.0000   Southwest            2
Pak               10514000.0000  United Kingdom       1
```  
  
## <a name="see-also"></a>См. также:  
 [DENSE_RANK &#40; Transact-SQL &#41;](../../t-sql/functions/dense-rank-transact-sql.md)   
 [ROW_NUMBER &#40; Transact-SQL &#41;](../../t-sql/functions/row-number-transact-sql.md)   
 [NTILE &#40; Transact-SQL &#41;](../../t-sql/functions/ntile-transact-sql.md)   
 [Ранжирующие функции &#40; Transact-SQL &#41;](../../t-sql/functions/ranking-functions-transact-sql.md)   
 [Встроенные функции (Transact-SQL)](~/t-sql/functions/functions.md)  
  
  




