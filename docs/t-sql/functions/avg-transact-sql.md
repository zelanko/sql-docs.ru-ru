---
title: "AVG (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 07/24/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- AVG_TSQL
- AVG
dev_langs:
- TSQL
helpviewer_keywords:
- AVG function [Transact-SQL]
- GROUP BY clause, AVG function
- DISTINCT keyword
- values [SQL Server], average
- average values
ms.assetid: 4534b705-d946-441b-9b5d-5fbe561c9131
caps.latest.revision: 52
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 80c1228faeaaa4012afc0fd27992a2f5cf389f6e
ms.openlocfilehash: 1e7598f8ee20f88346dfcbba1757f1173b34fe5c
ms.contentlocale: ru-ru
ms.lasthandoff: 10/12/2017

---
# <a name="avg-transact-sql"></a>AVG (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Возвращает среднее арифметическое группы значений. Значения NULL пропускаются.
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```sql
AVG ( [ ALL | DISTINCT ] expression )  
   OVER ( [ partition_by_clause ] order_by_clause )    
```  
  
## <a name="arguments"></a>Аргументы  
ALL  
Применяет агрегатную функцию ко всем значениям. ALL является параметром по умолчанию.
  
DISTINCT  
Указывает на то, что функция AVG будет выполнена только для одного экземпляра каждого уникального значения, независимо от того, сколько раз встречается это значение.
  
*expression*  
— [Выражение](../../t-sql/language-elements/expressions-transact-sql.md) точных числовых или приблизительных числовых типа данных, за исключением **бит** тип данных. Агрегатные функции и вложенные запросы не допускаются.
  
НАД **(** [ *partition_by_clause* ] *order_by_clause***)**  
*partition_by_clause* Делит результирующий набор, полученный с помощью предложения FROM, на секции, к которым применяется функция. Если этот параметр не указан, функция обрабатывает все строки результирующего набора запроса как отдельные группы. *order_by_clause* , определяет логический порядок, в котором выполняется операция. *order_by_clause* является обязательным. Дополнительные сведения см. в разделе [предложение OVER &#40; Transact-SQL &#41; ](../../t-sql/queries/select-over-clause-transact-sql.md).
  
## <a name="return-types"></a>Возвращаемые типы
Возвращаемый тип определяется типом вычисленного результата *выражение*.
  
|Результат выражения|Возвращаемый тип|  
|---|---|
|**tinyint**|**int**|  
|**smallint**|**int**|  
|**ssNoversion**|**int**|  
|**bigint**|**bigint**|  
|**десятичное число** категории (p, s)|**Decimal (38, s)** деленная **decimal (10, 0)**|  
|**Money** и **smallmoney** категории|**money**|  
|**число с плавающей запятой** и **реальные** категории|**float**|  
  
## <a name="remarks"></a>Замечания  
Если тип данных *выражение* данных-псевдонимом является тип, возвращаемый тип также является псевдонимом типа данных. Тем не менее, если тип базовых данных псевдоним типа данных будет повышаться, например из **tinyint** для **int**, возвращается повышенного уровня данных, а не типа данных псевдонима.
  
Функция AVG () вычисляет среднее арифметическое набора значений, выполняя деление суммы этих значений на число значений, не равных NULL. Если сумма превышает максимальное значение для типа данных возвращаемого значения, будет возвращена ошибка.
  
AVG — это детерминированная функция, если она используется без предложений OVER и ORDER BY. Она не детерминирована при использовании с предложениями OVER и ORDER BY. Дополнительные сведения см. в разделе [Deterministic and Nondeterministic Functions](../../relational-databases/user-defined-functions/deterministic-and-nondeterministic-functions.md).
  
## <a name="examples"></a>Примеры  
  
### <a name="a-using-the-sum-and-avg-functions-for-calculations"></a>A. Использование функций SUM и AVG для вычислений  
В следующем примере вычисляются среднее количество часов отпуска и сумма часов больничных, которые использовали вице-президенты компании [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)]. Каждая из этих агрегатных функций создает одно сводное значение для всех извлеченных строк. В этом примере используется база данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)].
  
```sql
SELECT AVG(VacationHours)AS 'Average vacation hours',   
    SUM(SickLeaveHours) AS 'Total sick leave hours'  
FROM HumanResources.Employee  
WHERE JobTitle LIKE 'Vice President%';  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```
Average vacation hours       Total sick leave hours
 ----------------------       ----------------------
25                           97
  
(1 row(s) affected)
```
  
### <a name="b-using-the-sum-and-avg-functions-with-a-group-by-clause"></a>Б. Использование функций SUM и AVG в предложении GROUP BY  
При использовании с предложением `GROUP BY` каждая агрегатная функция создает одно значение для каждой группы вместо всей таблицы. В следующем примере создается итоговое значение для каждой территории продаж в базе данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]. Итог содержит средний бонус, полученный продавцами по каждой территории, и сумму продаж за текущий год для каждой территории.
  
```sql
SELECT TerritoryID, AVG(Bonus)as 'Average bonus', SUM(SalesYTD) as 'YTD sales'  
FROM Sales.SalesPerson  
GROUP BY TerritoryID;  
GO  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
TerritoryID Average Bonus         YTD Sales  
----------- --------------------- ---------------------  
NULL        0.00                  1252127.9471  
1           4133.3333             4502152.2674  
2           4100.00               3763178.1787  
3           2500.00               3189418.3662  
4           2775.00               6709904.1666  
5           6700.00               2315185.611  
6           2750.00               4058260.1825  
7           985.00                3121616.3202  
8           75.00                 1827066.7118  
9           5650.00               1421810.9242  
10          5150.00               4116871.2277  
  
(11 row(s) affected)  
```  
  
### <a name="c-using-avg-with-distinct"></a>В. Использование функции AVG с ключевым словом DISTINCT  
Следующая инструкция возвращает среднюю справочную цену на продукцию из базы данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]. При указании DISTINCT в расчете учитываются только уникальные значения.
  
```sql
SELECT AVG(DISTINCT ListPrice)  
FROM Production.Product;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```
------------------------------
437.4042
  
(1 row(s) affected)
```
  
### <a name="d-using-avg-without-distinct"></a>Г. Использование функции AVG без ключевого слова DISTINCT  
Без ключевого слова DISTINCT функция `AVG` находит среднюю справочную цену всех продуктов в таблице `Product` в базе данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)], учитывая и все повторяющиеся значения.
  
```sql
SELECT AVG(ListPrice)  
FROM Production.Product;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```
------------------------------
438.6662
  
(1 row(s) affected)
```
  
### <a name="e-using-the-over-clause"></a>Д. Использование предложения OVER  
Следующий пример показывает использование функции AVG с предложением OVER для получения скользящего среднего годовых продаж на каждой территории в таблице `Sales.SalesPerson` в базе данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]. Данные секционируются по `TerritoryID` и логически сортируются по `SalesYTD`. Это означает, что функция AVG вычисляется для каждой территории на основании объема продаж за год. Обратите внимание, что в `TerritoryID` 1 для продаж за 2005 год используются две строки, в которых представлены два менеджера по продажам с показателями за этот год. После расчета среднего значения продаж для двух данных строк в вычисление включается третья строка, представляющая продажи за 2006 год.
  
```sql
SELECT BusinessEntityID, TerritoryID   
   ,DATEPART(yy,ModifiedDate) AS SalesYear  
   ,CONVERT(varchar(20),SalesYTD,1) AS  SalesYTD  
   ,CONVERT(varchar(20),AVG(SalesYTD) OVER (PARTITION BY TerritoryID   
                                            ORDER BY DATEPART(yy,ModifiedDate)   
                                           ),1) AS MovingAvg  
   ,CONVERT(varchar(20),SUM(SalesYTD) OVER (PARTITION BY TerritoryID   
                                            ORDER BY DATEPART(yy,ModifiedDate)   
                                            ),1) AS CumulativeTotal  
FROM Sales.SalesPerson  
WHERE TerritoryID IS NULL OR TerritoryID < 5  
ORDER BY TerritoryID,SalesYear;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
BusinessEntityID TerritoryID SalesYear   SalesYTD             MovingAvg            CumulativeTotal  
---------------- ----------- ----------- -------------------- -------------------- --------------------  
274              NULL        2005        559,697.56           559,697.56           559,697.56  
287              NULL        2006        519,905.93           539,801.75           1,079,603.50  
285              NULL        2007        172,524.45           417,375.98           1,252,127.95  
283              1           2005        1,573,012.94         1,462,795.04         2,925,590.07  
280              1           2005        1,352,577.13         1,462,795.04         2,925,590.07  
284              1           2006        1,576,562.20         1,500,717.42         4,502,152.27  
275              2           2005        3,763,178.18         3,763,178.18         3,763,178.18  
277              3           2005        3,189,418.37         3,189,418.37         3,189,418.37  
276              4           2005        4,251,368.55         3,354,952.08         6,709,904.17  
281              4           2005        2,458,535.62         3,354,952.08         6,709,904.17  
  
(10 row(s) affected)  
  
```  
  
В этом примере предложение OVER не включает в себя предложение PARTITION BY. Это означает, что функция будет применяться для всех строк, возвращаемых запросом. Предложение ORDER BY, указанное в предложении OVER, определяет логический порядок применения функции AVG. Запрос возвращает скользящее среднее значение продаж за год для всех территорий, указанных в предложении WHERE. Предложение ORDER BY, указанное в инструкции SELECT, определяет порядок отображения строк запроса.
  
```sql
SELECT BusinessEntityID, TerritoryID   
   ,DATEPART(yy,ModifiedDate) AS SalesYear  
   ,CONVERT(varchar(20),SalesYTD,1) AS  SalesYTD  
   ,CONVERT(varchar(20),AVG(SalesYTD) OVER (ORDER BY DATEPART(yy,ModifiedDate)   
                                            ),1) AS MovingAvg  
   ,CONVERT(varchar(20),SUM(SalesYTD) OVER (ORDER BY DATEPART(yy,ModifiedDate)   
                                            ),1) AS CumulativeTotal  
FROM Sales.SalesPerson  
WHERE TerritoryID IS NULL OR TerritoryID < 5  
ORDER BY SalesYear;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
BusinessEntityID TerritoryID SalesYear   SalesYTD             MovingAvg            CumulativeTotal  
---------------- ----------- ----------- -------------------- -------------------- --------------------  
274              NULL        2005        559,697.56           2,449,684.05         17,147,788.35  
275              2           2005        3,763,178.18         2,449,684.05         17,147,788.35  
276              4           2005        4,251,368.55         2,449,684.05         17,147,788.35  
277              3           2005        3,189,418.37         2,449,684.05         17,147,788.35  
280              1           2005        1,352,577.13         2,449,684.05         17,147,788.35  
281              4           2005        2,458,535.62         2,449,684.05         17,147,788.35  
283              1           2005        1,573,012.94         2,449,684.05         17,147,788.35  
284              1           2006        1,576,562.20         2,138,250.72         19,244,256.47  
287              NULL        2006        519,905.93           2,138,250.72         19,244,256.47  
285              NULL        2007        172,524.45           1,941,678.09         19,416,780.93  
(10 row(s) affected)  
```  
  
## <a name="see-also"></a>См. также:
[Агрегатные функции &#40; Transact-SQL &#41;](../../t-sql/functions/aggregate-functions-transact-sql.md)  
[ЧЕРЕЗ предложение &#40; Transact-SQL &#41;](../../t-sql/queries/select-over-clause-transact-sql.md)
  
  

