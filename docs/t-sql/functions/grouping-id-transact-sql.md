---
title: GROUPING_ID (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- GROUPING_ID_TSQL
- GROUPING_ID
dev_langs:
- TSQL
helpviewer_keywords:
- GROUP BY clause, GROUPING_ID
- GROUPING_ID function
ms.assetid: c1050658-b19f-42ee-9a05-ecd6a73b896c
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 6cfbecf5689432a0e9053abf043225b9f9ff596b
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85631567"
---
# <a name="grouping_id-transact-sql"></a>GROUPING_ID (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Представляет собой функцию, которая вычисляет уровень группирования. Если задано предложение GROUP BY, функция GROUPING_ID может использоваться только в предложениях SELECT \<select>, HAVING или ORDER BY.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```syntaxsql
  
GROUPING_ID ( <column_expression>[ ,...n ] )  
```  
  
## <a name="arguments"></a>Аргументы  
 \<column_expression>  
 Выражение *column_expression* в предложении [GROUP BY](../../t-sql/queries/select-group-by-transact-sql.md).  
  
## <a name="return-type"></a>Тип возвращаемых данных  
 **int**  
  
## <a name="remarks"></a>Remarks  
 Аргумент \<column_expression> функции GROUPING_ID должен точно соответствовать выражению в списке GROUP BY. Например, если группирование осуществляется с помощью функции DATEPART (yyyy, \<*column name*>), то следует использовать функцию GROUPING_ID (DATEPART (yyyy, \<*column name*>)), а если для группирования служит аргумент \<*column name*>, следует использовать функцию GROUPING_ID (\<*column name*>).  
  
## <a name="comparing-grouping_id--to-grouping-"></a>Сравнение функций GROUPING_ID () и GROUPING ()  
 GROUPING_ID (\<column_expression> [ **,** ...*n* ]) вводит возврат эквивалента GROUPING (\<column_expression>) для каждого столбца в своем списке столбцов в каждой строке вывода как строку единиц и нулей. Функция GROUPING_ID интерпретирует эту строку как двоичное число и выполняет возврат эквивалентного целого числа. Рассмотрим, например, следующую инструкцию: `SELECT a, b, c, SUM(d),``GROUPING_ID(a,b,c)``FROM T GROUP BY <group by list>`. В следующей таблице показаны входные и выходные значения функции GROUPING_ID ().  
  
|Статистически обработанные столбцы|Входные данные GROUPING_ID (a, b, c) = GROUPING(a) + GROUPING(b) + GROUPING(c)|Выходные данные GROUPING_ID ()|  
|------------------------|---------------------------------------------------------------------------------------|------------------------------|  
|`a`|`100`|`4`|  
|`b`|`010`|`2`|  
|`c`|`001`|`1`|  
|`ab`|`110`|`6`|  
|`ac`|`101`|`5`|  
|`bc`|`011`|`3`|  
|`abc`|`111`|`7`|  
  
## <a name="technical-definition-of-grouping_id-"></a>Техническое определение функции GROUPING_ID ()  
 Каждый аргумент функции GROUPING_ID должен быть элементом списка GROUP BY. Функция GROUPING_ID () возвращает битовую карту типа **integer**, в которой N самых младших битов могут быть установлены. Установленный **bit** означает, что соответствующий аргумент не является столбцом группирования для указанной выходной строки. Самый младший **bit** соответствует аргументу N, а самый младший N-1<sup>й</sup>**bit** соответствует аргументу 1.  
  
## <a name="grouping_id--equivalents"></a>Функции, эквивалентные функции GROUPING_ID ()  
 Применительно к одиночному запросу группирования функция GROUPING (\<column_expression>) эквивалентна GROUPING_ID (\<column_expression>), и обе эти функции возвращают 0.  
  
 Например, следующие инструкции эквивалентны.  
  
 Инструкция А:  
  
```  
SELECT GROUPING_ID(A,B)  
FROM T   
GROUP BY CUBE(A,B)   
```  
  
 Инструкция Б:  
  
```  
SELECT 3 FROM T GROUP BY ()  
UNION ALL  
SELECT 1 FROM T GROUP BY A  
UNION ALL  
SELECT 2 FROM T GROUP BY B  
UNION ALL  
SELECT 0 FROM T GROUP BY A,B  
```  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-using-grouping_id-to-identify-grouping-levels"></a>A. Использование функции GROUPING_ID для обозначения уровней группирования  
 В следующем примере показано, как определить итоговое значение количества сотрудников по столбцам `Name` и `Title`, `Name,` а также как вычислить общее количество сотрудников во всей компании в базе данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]. В этом примере функция `GROUPING_ID()` используется для создания значения, обозначающего уровень агрегирования, в каждой строке столбца `Title`.  
  
```  
SELECT D.Name  
    ,CASE   
    WHEN GROUPING_ID(D.Name, E.JobTitle) = 0 THEN E.JobTitle  
    WHEN GROUPING_ID(D.Name, E.JobTitle) = 1 THEN N'Total: ' + D.Name   
    WHEN GROUPING_ID(D.Name, E.JobTitle) = 3 THEN N'Company Total:'  
        ELSE N'Unknown'  
    END AS N'Job Title'  
    ,COUNT(E.BusinessEntityID) AS N'Employee Count'  
FROM HumanResources.Employee E  
    INNER JOIN HumanResources.EmployeeDepartmentHistory DH  
        ON E.BusinessEntityID = DH.BusinessEntityID  
    INNER JOIN HumanResources.Department D  
        ON D.DepartmentID = DH.DepartmentID       
WHERE DH.EndDate IS NULL  
    AND D.DepartmentID IN (12,14)  
GROUP BY ROLLUP(D.Name, E.JobTitle);  
```  
  
### <a name="b-using-grouping_id-to-filter-a-result-set"></a>Б. Использование функции GROUPING_ID для фильтрации результирующего набора  
  
#### <a name="simple-example"></a>Простой пример  
 Чтобы воспользоваться следующим кодом для получения только тех строк, в которых подсчитаны данные о количестве сотрудников с разными должностями, удалите символы комментария из предложения `HAVING GROUPING_ID(D.Name, E.JobTitle); = 0` в базе данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]. Чтобы получить только строки с данными о количестве сотрудников в разных отделах, удалите символы комментария из предложения `HAVING GROUPING_ID(D.Name, E.JobTitle) = 1;`.  
  
```  
SELECT D.Name  
    ,E.JobTitle  
    ,GROUPING_ID(D.Name, E.JobTitle) AS 'Grouping Level'  
    ,COUNT(E.BusinessEntityID) AS N'Employee Count'  
FROM HumanResources.Employee AS E  
    INNER JOIN HumanResources.EmployeeDepartmentHistory AS DH  
        ON E.BusinessEntityID = DH.BusinessEntityID  
    INNER JOIN HumanResources.Department AS D  
        ON D.DepartmentID = DH.DepartmentID       
WHERE DH.EndDate IS NULL  
    AND D.DepartmentID IN (12,14)  
GROUP BY ROLLUP(D.Name, E.JobTitle)  
--HAVING GROUPING_ID(D.Name, E.JobTitle) = 0; --All titles  
--HAVING GROUPING_ID(D.Name, E.JobTitle) = 1; --Group by Name;  
```  
  
 Ниже приводится неотфильтрованный результирующий набор.  
  
|Имя|Title|Grouping Level|Employee Count|Имя|  
|----------|-----------|--------------------|--------------------|----------|  
|Document Control|Control Specialist|0|2|Document Control|  
|Document Control|Document Control Assistant|0|2|Document Control|  
|Document Control|Document Control Manager|0|1|Document Control|  
|Document Control|NULL|1|5|Document Control|  
|Facilities and Maintenance|Facilities Administrative Assistant|0|1|Facilities and Maintenance|  
|Facilities and Maintenance|Facilities Manager|0|1|Facilities and Maintenance|  
|Facilities and Maintenance|Janitor|0|4|Facilities and Maintenance|  
|Facilities and Maintenance|Maintenance Supervisor|0|1|Facilities and Maintenance|  
|Facilities and Maintenance|NULL|1|7|Facilities and Maintenance|  
|NULL|NULL|3|12|NULL|  
  
#### <a name="complex-example"></a>Сложный пример  
 В следующем примере функция `GROUPING_ID()` используется для фильтрации результирующего набора, содержащего несколько уровней группирования, по уровням группирования. Аналогичный код может использоваться для создания представления, имеющего несколько уровней группирования, и хранимой процедуры, которая вызывает это представление и передает параметр, применяемый для фильтрации этого представления по уровню группирования. В этом примере используется база данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)].  
  
```  
DECLARE @Grouping nvarchar(50);  
DECLARE @GroupingLevel smallint;  
SET @Grouping = N'CountryRegionCode Total';  
  
SELECT @GroupingLevel = (  
    CASE @Grouping  
        WHEN N'Grand Total'             THEN 15  
        WHEN N'SalesPerson Total'       THEN 14  
        WHEN N'Store Total'             THEN 13  
        WHEN N'Store SalesPerson Total' THEN 12  
        WHEN N'CountryRegionCode Total' THEN 11  
        WHEN N'Group Total'             THEN 7  
        ELSE N'Unknown'  
    END);  
  
SELECT   
    T.[Group]  
    ,T.CountryRegionCode  
    ,S.Name AS N'Store'  
    ,(SELECT P.FirstName + ' ' + P.LastName   
        FROM Person.Person AS P   
        WHERE P.BusinessEntityID = H.SalesPersonID)  
        AS N'Sales Person'  
    ,SUM(TotalDue)AS N'TotalSold'  
    ,CAST(GROUPING(T.[Group])AS char(1)) +   
        CAST(GROUPING(T.CountryRegionCode)AS char(1)) +   
        CAST(GROUPING(S.Name)AS char(1)) +   
        CAST(GROUPING(H.SalesPersonID)AS char(1))   
        AS N'GROUPING base-2'  
    ,GROUPING_ID((T.[Group])  
        ,(T.CountryRegionCode),(S.Name),(H.SalesPersonID)  
        ) AS N'GROUPING_ID'  
    ,CASE   
        WHEN GROUPING_ID(  
            (T.[Group]),(T.CountryRegionCode)  
            ,(S.Name),(H.SalesPersonID)  
            ) = 15 THEN N'Grand Total'  
        WHEN GROUPING_ID(  
            (T.[Group]),(T.CountryRegionCode)  
            ,(S.Name),(H.SalesPersonID)  
            ) = 14 THEN N'SalesPerson Total'  
        WHEN GROUPING_ID(  
            (T.[Group]),(T.CountryRegionCode)  
            ,(S.Name),(H.SalesPersonID)  
            ) = 13 THEN N'Store Total'  
        WHEN GROUPING_ID(  
            (T.[Group]),(T.CountryRegionCode)  
            ,(S.Name),(H.SalesPersonID)  
            ) = 12 THEN N'Store SalesPerson Total'  
        WHEN GROUPING_ID(  
            (T.[Group]),(T.CountryRegionCode)  
            ,(S.Name),(H.SalesPersonID)  
            ) = 11 THEN N'CountryRegionCode Total'  
        WHEN GROUPING_ID(  
            (T.[Group]),(T.CountryRegionCode)  
            ,(S.Name),(H.SalesPersonID)  
            ) =  7 THEN N'Group Total'  
        ELSE N'Error'  
        END AS N'Level'  
FROM Sales.Customer AS C  
    INNER JOIN Sales.Store AS S  
        ON C.StoreID  = S.BusinessEntityID   
    INNER JOIN Sales.SalesTerritory AS T  
        ON C.TerritoryID  = T.TerritoryID   
    INNER JOIN Sales.SalesOrderHeader AS H  
        ON C.CustomerID = H.CustomerID  
GROUP BY GROUPING SETS ((S.Name,H.SalesPersonID)  
    ,(H.SalesPersonID),(S.Name)  
    ,(T.[Group]),(T.CountryRegionCode),()  
    )  
HAVING GROUPING_ID(  
    (T.[Group]),(T.CountryRegionCode),(S.Name),(H.SalesPersonID)  
    ) = @GroupingLevel  
ORDER BY   
    GROUPING_ID(S.Name,H.SalesPersonID),GROUPING_ID((T.[Group])  
    ,(T.CountryRegionCode)  
    ,(S.Name)  
    ,(H.SalesPersonID))ASC;  
```  
  
### <a name="c-using-grouping_id--with-rollup-and-cube-to-identify-grouping-levels"></a>В. Использование функции GROUPING_ID () с операторами ROLLUP и CUBE для обозначения уровней группирования  
 В следующих примерах приведен код, который показывает, как использовать функцию `GROUPING()` для вычисления столбца `Bit Vector(base-2)`. Функция `GROUPING_ID()` служит для вычисления соответствующего столбца `Integer Equivalent`. Порядок столбцов в функции `GROUPING_ID()` противоположен порядку столбцов, для объединения которых применяется функция `GROUPING()`.  
  
 В этих примерах функция `GROUPING_ID()` используется для создания значения, обозначающего уровень группирования, в каждой строке столбца `Grouping Level`. Уровни группирования не всегда представляют собой последовательный список целых чисел, который начинается с 1 (0, 1, 2,...*n*).  
  
> [!NOTE]  
>  Функции GROUPING и GROUPING_ID могут использоваться в предложении HAVING для фильтрации результирующего набора.  
  
#### <a name="rollup-example"></a>Пример применения оператора ROLLUP  
 В этом примере, в отличие от следующего примера с предложением CUBE, появляются не все уровни группирования. Если порядок столбцов в списке `ROLLUP` изменяется, значения уровня в столбце `Grouping Level` также должны быть изменены. В этом примере используется база данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)].  
  
```  
SELECT DATEPART(yyyy,OrderDate) AS N'Year'  
    ,DATEPART(mm,OrderDate) AS N'Month'  
    ,DATEPART(dd,OrderDate) AS N'Day'  
    ,SUM(TotalDue) AS N'Total Due'  
    ,CAST(GROUPING(DATEPART(dd,OrderDate))AS char(1)) +   
        CAST(GROUPING(DATEPART(mm,OrderDate))AS char(1)) +   
        CAST(GROUPING(DATEPART(yyyy,OrderDate))AS char(1))   
     AS N'Bit Vector(base-2)'  
    ,GROUPING_ID(DATEPART(yyyy,OrderDate)  
        ,DATEPART(mm,OrderDate)  
        ,DATEPART(dd,OrderDate))   
        AS N'Integer Equivalent'  
    ,CASE  
        WHEN GROUPING_ID(DATEPART(yyyy,OrderDate)  
            ,DATEPART(mm,OrderDate),DATEPART(dd,OrderDate)  
            ) = 0 THEN N'Year Month Day'  
        WHEN GROUPING_ID(DATEPART(yyyy,OrderDate)  
            ,DATEPART(mm,OrderDate),DATEPART(dd,OrderDate)  
            ) = 1 THEN N'Year Month'  
        WHEN GROUPING_ID(DATEPART(yyyy,OrderDate)  
            ,DATEPART(mm,OrderDate),DATEPART(dd,OrderDate)  
            ) = 2 THEN N'not used'  
        WHEN GROUPING_ID(DATEPART(yyyy,OrderDate)  
            ,DATEPART(mm,OrderDate),DATEPART(dd,OrderDate)  
            ) = 3 THEN N'Year'  
        WHEN GROUPING_ID(DATEPART(yyyy,OrderDate)  
            ,DATEPART(mm,OrderDate),DATEPART(dd,OrderDate)  
            ) = 4 THEN N'not used'  
        WHEN GROUPING_ID(DATEPART(yyyy,OrderDate)  
            ,DATEPART(mm,OrderDate),DATEPART(dd,OrderDate)  
            ) = 5 THEN N'not used'  
        WHEN GROUPING_ID(DATEPART(yyyy,OrderDate)  
            ,DATEPART(mm,OrderDate),DATEPART(dd,OrderDate)  
            ) = 6 THEN N'not used'  
        WHEN GROUPING_ID(DATEPART(yyyy,OrderDate)  
            ,DATEPART(mm,OrderDate),DATEPART(dd,OrderDate)  
            ) = 7 THEN N'Grand Total'  
    ELSE N'Error'  
    END AS N'Grouping Level'  
FROM Sales.SalesOrderHeader  
WHERE DATEPART(yyyy,OrderDate) IN(N'2007',N'2008')  
    AND DATEPART(mm,OrderDate) IN(1,2)  
    AND DATEPART(dd,OrderDate) IN(1,2)  
GROUP BY ROLLUP(DATEPART(yyyy,OrderDate)  
        ,DATEPART(mm,OrderDate)  
        ,DATEPART(dd,OrderDate))  
ORDER BY GROUPING_ID(DATEPART(mm,OrderDate)  
    ,DATEPART(yyyy,OrderDate)  
    ,DATEPART(dd,OrderDate)  
    )  
    ,DATEPART(yyyy,OrderDate)  
    ,DATEPART(mm,OrderDate)  
    ,DATEPART(dd,OrderDate);  
```  
  
 Здесь приводится частичный результирующий набор.  
  
|Год|Месяц|День|Total Due|Bit Vector (base-2)|Integer Equivalent|Grouping Level|  
|----------|-----------|---------|---------------|----------------------------|------------------------|--------------------|  
|2007 г.|1|1|1497452,6066|000|0|Year Month Day|  
|2007 г.|1|2|21772,3494|000|0|Year Month Day|  
|2007 г.|2|1|2705653,5913|000|0|Year Month Day|  
|2007 г.|2|2|21684,4068|000|0|Year Month Day|  
|2008|1|1|1908122,0967|000|0|Year Month Day|  
|2008|1|2|46458,0691|000|0|Year Month Day|  
|2008|2|1|3108771,9729|000|0|Year Month Day|  
|2008|2|2|54598,5488|000|0|Year Month Day|  
|2007 г.|1|NULL|1519224,956|100|1|Year Month|  
|2007 г.|2|NULL|2727337,9981|100|1|Year Month|  
|2008|1|NULL|1954580,1658|100|1|Year Month|  
|2008|2|NULL|3163370,5217|100|1|Year Month|  
|2007 г.|NULL|NULL|4246562,9541|110|3|Год|  
|2008|NULL|NULL|5117950,6875|110|3|Год|  
|NULL|NULL|NULL|9364513,6416|111|7|Grand Total|  
  
#### <a name="cube-example"></a>Пример применения предложения CUBE  
 В этом примере функция `GROUPING_ID()` используется для создания значения, которое обозначает уровень группирования, в каждой строке столбца `Grouping Level`.  
  
 В отличие от оператора `ROLLUP` в предыдущем примере, оператор `CUBE` выводит все уровни группирования. Если порядок столбцов в списке `CUBE` изменяется, значения уровня в столбце `Grouping Level` также должны быть изменены. В этом примере используется база данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]  
  
```  
SELECT DATEPART(yyyy,OrderDate) AS N'Year'  
    ,DATEPART(mm,OrderDate) AS N'Month'  
    ,DATEPART(dd,OrderDate) AS N'Day'  
    ,SUM(TotalDue) AS N'Total Due'  
    ,CAST(GROUPING(DATEPART(dd,OrderDate))AS char(1)) +   
        CAST(GROUPING(DATEPART(mm,OrderDate))AS char(1)) +   
        CAST(GROUPING(DATEPART(yyyy,OrderDate))AS char(1))   
        AS N'Bit Vector(base-2)'  
    ,GROUPING_ID(DATEPART(yyyy,OrderDate)  
        ,DATEPART(mm,OrderDate)  
        ,DATEPART(dd,OrderDate))   
        AS N'Integer Equivalent'  
    ,CASE  
        WHEN GROUPING_ID(DATEPART(yyyy,OrderDate)  
            ,DATEPART(mm,OrderDate),DATEPART(dd,OrderDate)  
            ) = 0 THEN N'Year Month Day'  
        WHEN GROUPING_ID(DATEPART(yyyy,OrderDate)   
            ,DATEPART(mm,OrderDate),DATEPART(dd,OrderDate)  
            ) = 1 THEN N'Year Month'  
        WHEN GROUPING_ID(DATEPART(yyyy,OrderDate)   
            ,DATEPART(mm,OrderDate),DATEPART(dd,OrderDate)  
            ) = 2 THEN N'Year Day'  
        WHEN GROUPING_ID(DATEPART(yyyy,OrderDate)   
            ,DATEPART(mm,OrderDate),DATEPART(dd,OrderDate)  
            ) = 3 THEN N'Year'  
        WHEN GROUPING_ID(DATEPART(yyyy,OrderDate)   
            ,DATEPART(mm,OrderDate),DATEPART(dd,OrderDate)  
            ) = 4 THEN N'Month Day'  
        WHEN GROUPING_ID(DATEPART(yyyy,OrderDate)   
            ,DATEPART(mm,OrderDate),DATEPART(dd,OrderDate)  
            ) = 5 THEN N'Month'  
        WHEN GROUPING_ID(DATEPART(yyyy,OrderDate)   
            ,DATEPART(mm,OrderDate),DATEPART(dd,OrderDate)  
            ) = 6 THEN N'Day'  
        WHEN GROUPING_ID(DATEPART(yyyy,OrderDate)   
            ,DATEPART(mm,OrderDate),DATEPART(dd,OrderDate)  
            ) = 7 THEN N'Grand Total'  
    ELSE N'Error'  
    END AS N'Grouping Level'  
FROM Sales.SalesOrderHeader  
WHERE DATEPART(yyyy,OrderDate) IN(N'2007',N'2008')  
    AND DATEPART(mm,OrderDate) IN(1,2)  
    AND DATEPART(dd,OrderDate) IN(1,2)  
GROUP BY CUBE(DATEPART(yyyy,OrderDate)  
    ,DATEPART(mm,OrderDate)  
    ,DATEPART(dd,OrderDate))  
ORDER BY GROUPING_ID(DATEPART(yyyy,OrderDate)  
    ,DATEPART(mm,OrderDate)  
    ,DATEPART(dd,OrderDate)  
    )  
    ,DATEPART(yyyy,OrderDate)  
    ,DATEPART(mm,OrderDate)  
    ,DATEPART(dd,OrderDate);  
```  
  
 Здесь приводится частичный результирующий набор.  
  
|Год|Месяц|День|Total Due|Bit Vector (base-2)|Integer Equivalent|Grouping Level|  
|----------|-----------|---------|---------------|----------------------------|------------------------|--------------------|  
|2007 г.|1|1|1497452,6066|000|0|Year Month Day|  
|2007 г.|1|2|21772,3494|000|0|Year Month Day|  
|2007 г.|2|1|2705653,5913|000|0|Year Month Day|  
|2007 г.|2|2|21684,4068|000|0|Year Month Day|  
|2008|1|1|1908122,0967|000|0|Year Month Day|  
|2008|1|2|46458,0691|000|0|Year Month Day|  
|2008|2|1|3108771,9729|000|0|Year Month Day|  
|2008|2|2|54598,5488|000|0|Year Month Day|  
|2007 г.|1|NULL|1519224,956|100|1|Year Month|  
|2007 г.|2|NULL|2727337,9981|100|1|Year Month|  
|2008|1|NULL|1954580,1658|100|1|Year Month|  
|2008|2|NULL|3163370,5217|100|1|Year Month|  
|2007 г.|NULL|1|4203106,1979|010|2|Year Day|  
|2007 г.|NULL|2|43456,7562|010|2|Year Day|  
|2008|NULL|1|5016894,0696|010|2|Year Day|  
|2008|NULL|2|101056,6179|010|2|Year Day|  
|2007 г.|NULL|NULL|4246562,9541|110|3|Год|  
|2008|NULL|NULL|5117950,6875|110|3|Год|  
|NULL|1|1|3405574,7033|001|4|Month Day|  
|NULL|1|2|68230,4185|001|4|Month Day|  
|NULL|2|1|5814425,5642|001|4|Month Day|  
|NULL|2|2|76282,9556|001|4|Month Day|  
|NULL|1|NULL|3473805,1218|101|5|Месяц|  
|NULL|2|NULL|5890708,5198|101|5|Месяц|  
|NULL|NULL|1|9220000,2675|011|6|День|  
|NULL|NULL|2|144513,3741|011|6|День|  
|NULL|NULL|NULL|9364513,6416|111|7|Grand Total|  
  
## <a name="see-also"></a>См. также:  
 [GROUPING (Transact-SQL)](../../t-sql/functions/grouping-transact-sql.md)   
 [GROUP BY (Transact-SQL)](../../t-sql/queries/select-group-by-transact-sql.md)  
  
  
