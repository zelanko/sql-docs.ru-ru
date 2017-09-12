---
title: "ROW_NUMBER (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 09/11/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ROW_NUMBER
- ROW_NUMBER_TSQL
- ROW_NUMBER()_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- ROW_NUMBER function
- row numbers [SQL Server]
- sequential row numbers [SQL Server]
ms.assetid: 82fa9016-77db-4b42-b4c8-df6095b81906
caps.latest.revision: 50
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 820acddf7de1282501caf2fcaa43dbc757b98b7a
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="rownumber-transact-sql"></a>ROW_NUMBER (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Номера выходного результирующего набора. В частности возвращает порядковый номер строки в секции результирующего набора, начиная с 1 для первой строки в каждой секции. 
  
`ROW_NUMBER`и `RANK` похожи. `ROW_NUMBER`все номера строк последовательно (например 1, 2, 3, 4, 5). `RANK`предоставляет значение все же наличие связей (например 1, 2, 2, 4, 5).   
  
> [!NOTE]
> `ROW_NUMBER`временное значение рассчитывается при запуске запроса. Для хранения чисел в таблице, в разделе [свойство IDENTITY](../../t-sql/statements/create-table-transact-sql-identity-property.md) и [ПОСЛЕДОВАТЕЛЬНОСТИ](../../t-sql/statements/create-sequence-transact-sql.md). 
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
 
  
## <a name="syntax"></a>Синтаксис  
  
```  
ROW_NUMBER ( )   
    OVER ( [ PARTITION BY value_expression , ... [ n ] ] order_by_clause )  
```  
  
## <a name="arguments"></a>Аргументы  
 PARTITION BY *value_expression*  
 Делит результирующий набор, полученный по [FROM](../../t-sql/queries/from-transact-sql.md) на секции, к которым применяется функция ROW_NUMBER. *value_expression* указывает столбец, по которому секционируется результирующий набор. Если `PARTITION BY` не указан, функция обрабатывает все строки результирующего набора запроса как одну группу. Дополнительные сведения см. в разделе [предложение OVER &#40; Transact-SQL &#41; ](../../t-sql/queries/select-over-clause-transact-sql.md).  
  
 *order_by_clause*  
 `ORDER BY` Предложение определяет последовательность, в которой строкам назначаются уникальному `ROW_NUMBER` в пределах указанной секции. Оно должно указываться обязательно. Дополнительные сведения см. в разделе [предложение OVER &#40; Transact-SQL &#41; ](../../t-sql/queries/select-over-clause-transact-sql.md).  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 **bigint**  
  
## <a name="general-remarks"></a>Общие замечания  
 Нет никакой гарантии, что строки возвращаются с помощью запроса `ROW_NUMBER()` будут упорядочены так же при каждом выполнении, если выполняются следующие условия.  
  
1.  Все значения в секционированном столбце являются уникальными.  
  
2.  Значения `ORDER BY` столбцы являются уникальными.  
  
3.  Сочетания значений столбца секционирования и `ORDER BY` столбцов являются уникальными.  
  
 `ROW_NUMBER()`является недетерминированным. Дополнительные сведения см. в разделе [Deterministic and Nondeterministic Functions](../../relational-databases/user-defined-functions/deterministic-and-nondeterministic-functions.md).  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-simple-examples"></a>A. Простые примеры 

Следующий запрос возвращает четыре системных таблиц в алфавитном порядке.

```
SELECT 
  name, recovery_model_desc
FROM sys.databases 
WHERE database_id < 5
ORDER BY name ASC;
```

 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
   
|имя    |recovery_model_desc |  
|-----------  |------------ |  
|master |SIMPLE |
|model |ПОЛНОЕ |
|msdb |SIMPLE |
|tempdb |SIMPLE |

Чтобы добавить столбец с номерами строк перед каждой строки, добавьте столбец с `ROW_NUMBER` функции, при этом с именем `Row#`. Необходимо переместить `ORDER BY` предложение до `OVER` предложения.

```
SELECT 
  ROW_NUMBER() OVER(ORDER BY name ASC) AS Row#,
  name, recovery_model_desc
FROM sys.databases 
WHERE database_id < 5;
```

 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
   
|Номер строки |имя    |recovery_model_desc |  
|------- |-----------  |------------ |  
|1 |master |SIMPLE |
|2 |model |ПОЛНОЕ |
|3 |msdb |SIMPLE |
|4 |tempdb |SIMPLE |

Добавление `PARTITION BY` предложение на `recovery_model_desc` столбец будет нумерацию при `recovery_model_desc` изменении значения. 
 
```
SELECT 
  ROW_NUMBER() OVER(PARTITION BY recovery_model_desc ORDER BY name ASC) 
    AS Row#,
  name, recovery_model_desc
FROM sys.databases WHERE database_id < 5;
```  

 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
   
|Номер строки |имя    |recovery_model_desc |  
|------- |-----------  |------------ |  
|1 |model |ПОЛНОЕ |
|1 |master |SIMPLE |
|2 |msdb |SIMPLE |
|3 |tempdb |SIMPLE |


### <a name="b-returning-the-row-number-for-salespeople"></a>Б. Возврат номера строки для salespeople  
 В следующем примере показан расчет номера строки для salespeople в [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)], выполняемый на основе ранжирования продаж за текущий год.  
  
```  
USE AdventureWorks2012;   
GO  
SELECT ROW_NUMBER() OVER(ORDER BY SalesYTD DESC) AS Row,   
    FirstName, LastName, ROUND(SalesYTD,2,1) AS "Sales YTD"   
FROM Sales.vSalesPerson  
WHERE TerritoryName IS NOT NULL AND SalesYTD <> 0;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
  
Row FirstName    LastName               SalesYTD  
--- -----------  ---------------------- -----------------  
1   Linda        Mitchell               4251368.54  
2   Jae          Pak                    4116871.22  
3   Michael      Blythe                 3763178.17  
4   Jillian      Carson                 3189418.36  
5   Ranjit       Varkey Chudukatil      3121616.32  
6   José         Saraiva                2604540.71  
7   Shu          Ito                    2458535.61  
8   Tsvi         Reiter                 2315185.61  
9   Rachel       Valdez                 1827066.71  
10  Tete         Mensa-Annan            1576562.19  
11  David        Campbell               1573012.93  
12  Garrett      Vargas                 1453719.46  
13  Lynn         Tsoflias               1421810.92  
14  Pamela       Ansman-Wolfe           1352577.13  
```  
  
### <a name="c-returning-a-subset-of-rows"></a>В. Возврат подмножества строк  
 В следующем примере показан расчет номеров всех строк в таблице `SalesOrderHeader` в порядке `OrderDate` с последующим возвращением строк с номерами от `50` до `60` включительно.  
  
```  
USE AdventureWorks2012;  
GO  
WITH OrderedOrders AS  
(  
    SELECT SalesOrderID, OrderDate,  
    ROW_NUMBER() OVER (ORDER BY OrderDate) AS RowNumber  
    FROM Sales.SalesOrderHeader   
)   
SELECT SalesOrderID, OrderDate, RowNumber    
FROM OrderedOrders   
WHERE RowNumber BETWEEN 50 AND 60;  
```  
  
### <a name="d-using-rownumber-with-partition"></a>Г. Использование ROW_NUMBER() с PARTITION  
 В следующем примере аргумент `PARTITION BY` используется для секционирования результирующего набора запроса по столбцу `TerritoryName`. Предложение `ORDER BY`, указанное в предложении `OVER`, упорядочивает строки каждой секции по столбцу `SalesYTD`. Предложение `ORDER BY` в инструкции `SELECT` упорядочивает полный результирующий набор запроса по `TerritoryName`.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT FirstName, LastName, TerritoryName, ROUND(SalesYTD,2,1) AS SalesYTD,  
ROW_NUMBER() OVER(PARTITION BY TerritoryName ORDER BY SalesYTD DESC) 
  AS Row  
FROM Sales.vSalesPerson  
WHERE TerritoryName IS NOT NULL AND SalesYTD <> 0  
ORDER BY TerritoryName;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
  
FirstName  LastName             TerritoryName        SalesYTD      Row  
---------  -------------------- ------------------   ------------  ---  
Lynn       Tsoflias             Australia            1421810.92    1  
José       Saraiva              Canada               2604540.71    1  
Garrett    Vargas               Canada               1453719.46    2  
Jillian    Carson               Central              3189418.36    1  
Ranjit     Varkey Chudukatil    France               3121616.32    1  
Rachel     Valdez               Germany              1827066.71    1  
Michael    Blythe               Northeast            3763178.17    1  
Tete       Mensa-Annan          Northwest            1576562.19    1  
David      Campbell             Northwest            1573012.93    2  
Pamela     Ansman-Wolfe         Northwest            1352577.13    3  
Tsvi       Reiter               Southeast            2315185.61    1  
Linda      Mitchell             Southwest            4251368.54    1  
Shu        Ito                  Southwest            2458535.61    2  
Jae        Pak                  United Kingdom       4116871.22    1  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="e-returning-the-row-number-for-salespeople"></a>Д. Возврат номера строки для salespeople  
 В следующем примере возвращается `ROW_NUMBER` для торговых представителей, в зависимости от их установленной квоты продаж.  
  
```  
-- Uses AdventureWorks  
  
SELECT ROW_NUMBER() OVER(ORDER BY SUM(SalesAmountQuota) DESC) 
    AS RowNumber,  
    FirstName, LastName,   
    CONVERT(varchar(13), SUM(SalesAmountQuota),1) AS SalesQuota   
FROM dbo.DimEmployee AS e  
INNER JOIN dbo.FactSalesQuota AS sq  
    ON e.EmployeeKey = sq.EmployeeKey  
WHERE e.SalesPersonFlag = 1  
GROUP BY LastName, FirstName;  
```  
  
 Здесь приводится частичный результирующий набор.  
  
 `RowNumber  FirstName  LastName            SalesQuota`  
  
 `---------  ---------  ------------------  -------------`  
  
 `1          Jillian    Carson              12,198,000.00`  
  
 `2          Linda      Mitchell            11,786,000.00`  
  
 `3          Michael    Blythe              11,162,000.00`  
  
 `4          Jae        Pak                 10,514,000.00`  
  
### <a name="f-using-rownumber-with-partition"></a>Е. Использование ROW_NUMBER() с PARTITION  
 Следующий пример демонстрирует использование функции `ROW_NUMBER` с аргументом `PARTITION BY`. В результате `ROW_NUMBER` функции для нумерации строк в каждой секции.  
  
```  
-- Uses AdventureWorks  
  
SELECT ROW_NUMBER() OVER(PARTITION BY SalesTerritoryKey 
        ORDER BY SUM(SalesAmountQuota) DESC) AS RowNumber,  
    LastName, SalesTerritoryKey AS Territory,  
    CONVERT(varchar(13), SUM(SalesAmountQuota),1) AS SalesQuota   
FROM dbo.DimEmployee AS e  
INNER JOIN dbo.FactSalesQuota AS sq  
    ON e.EmployeeKey = sq.EmployeeKey  
WHERE e.SalesPersonFlag = 1  
GROUP BY LastName, FirstName, SalesTerritoryKey;  
```  
  
 Здесь приводится частичный результирующий набор.  
  
 `RowNumber  LastName            Territory  SalesQuota`  
  
 `---------  ------------------  ---------  -------------`  
  
 `1          Campbell            1           4,025,000.00`  
  
 `2          Ansman-Wolfe        1           3,551,000.00`  
  
 `3          Mensa-Annan         1           2,275,000.00`  
  
 `1          Blythe              2          11,162,000.00`  
  
 `1          Carson              3          12,198,000.00`  
  
 `1          Mitchell            4          11,786,000.00`  
  
 `2          Ito                 4           7,804,000.00`  
  
## <a name="see-also"></a>См. также:  
 [Ранг &#40; Transact-SQL &#41;](../../t-sql/functions/rank-transact-sql.md)   
 [DENSE_RANK &#40; Transact-SQL &#41;](../../t-sql/functions/dense-rank-transact-sql.md)   
 [NTILE &#40; Transact-SQL &#41;](../../t-sql/functions/ntile-transact-sql.md)  
  
  



