---
title: Вложенные запросы
description: Вложенные запросы в Azure Synapse Analytics и Parallel Data Warehouse
ms.custom: seo-lt-2019
titleSuffix: Azure Synapse Analytics
ms.date: 03/03/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: t-sql
ms.topic: conceptual
ms.assetid: 0e8ebd60-1936-48c9-b2b9-e099c8269fcf
author: shkale-msft
ms.author: shkale
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest'
ms.openlocfilehash: a739b44c673a20a157dd2ea03824ae9a8b70a30b
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2020
ms.locfileid: "97439049"
---
# <a name="subqueries-azure-synapse-analytics-parallel-data-warehouse"></a>Вложенные запросы (Azure Synapse Analytics, Parallel Data Warehouse)
[!INCLUDE[applies-to-version/asa-pdw](../../includes/applies-to-version/asa-pdw.md)]

  В этой статье приведены примеры использования вложенных запросов в [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] или [!INCLUDE[ssPDW](../../includes/sspdw-md.md)].  
  
 Сведения об инструкции SELECT см. в статье [SELECT (Transact-SQL)](../../t-sql/queries/select-transact-sql.md).  
  
## <a name="contents"></a>Содержимое  
  
-   [Основы](#Basics)  
  
-   [Примеры. Azure Synapse Analytics и Parallel Data Warehouse](#Examples)  
  
##  <a name="basics"></a><a name="Basics"></a> Основы  
 Вложенный запрос  
 Вложенным запросом называется запрос, помещаемый в инструкцию SELECT, INSERT, UPDATE или DELETE или в другой вложенный запрос. Он также называется внутренним запросом или внутренней выборкой.  
  
 Внешний запрос  
 Инструкция, содержащая вложенный запрос. Также называется внешней выборкой.  
  
 Связанный вложенный запрос  
 Вложенный запрос, который обращается к таблице во внешнем запросе.  
  
##  <a name="examples-sssdw-and-sspdw"></a><a name="Examples"></a> Примеры: [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] и [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 В этом разделе приводятся примеры вложенных запросов, поддерживаемых в [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] или [!INCLUDE[ssPDW](../../includes/sspdw-md.md)].  
  
### <a name="a-top-and-order-by-in-a-subquery"></a>A. TOP и ORDER BY во вложенном запросе  
  
```sql
SELECT * FROM tblA  
WHERE col1 IN  
    (SELECT TOP 100 col1 FROM tblB ORDER BY col1);
```  
  
### <a name="b-having-clause-with-a-correlated-subquery"></a>Б. Предложение HAVING со связанным вложенным запросом  
  
```sql
SELECT dm.EmployeeKey, dm.FirstName, dm.LastName   
FROM DimEmployee AS dm   
GROUP BY dm.EmployeeKey, dm.FirstName, dm.LastName  
HAVING 5000 <=   
(SELECT sum(OrderQuantity)  
FROM FactResellerSales AS frs  
WHERE dm.EmployeeKey = frs.EmployeeKey)  
ORDER BY EmployeeKey;
```  
  
### <a name="c-correlated-subqueries-with-analytics"></a>В. Связанные вложенные запросы с аналитикой  
  
```sql
SELECT * FROM ReplA AS A   
WHERE A.ID IN   
    (SELECT sum(B.ID2) OVER() FROM ReplB AS B WHERE A.ID2 = B.ID);  
```  
  
### <a name="d-correlated-union-statements-in-a-subquery"></a>Г. Связанные инструкции объединения во вложенном запросе  
  
```sql
SELECT * FROM RA   
WHERE EXISTS   
    (SELECT 1 FROM RB WHERE RB.b1 = RA.a1   
     UNION ALL SELECT 1 FROM RC);  
```  
  
### <a name="e-join-predicates-in-a-subquery"></a>Д. Предикаты соединения во вложенном запросе  
  
```sql
SELECT * FROM RA INNER JOIN RB   
    ON RA.a1 = (SELECT COUNT(*) FROM RC);  
```  
  
### <a name="f-correlated-join-predicates-in-a-subquery"></a>Е. Связанные предикаты соединения во вложенном запросе  
  
```sql
SELECT * FROM RA   
    WHERE RA.a2 IN   
    (SELECT 1 FROM RB INNER JOIN RC ON RA.a1=RB.b1+RC.c1);  
```  
  
### <a name="g-correlated-subselects-as-data-sources"></a>Ж. Связанные вложенные выборки в качестве источников данных  
  
```sql
SELECT * FROM RA   
    WHERE 3 = (SELECT COUNT(*)   
        FROM (SELECT b1 FROM RB WHERE RB.b1 = RA.a1) X);  
```  
  
### <a name="h-correlated-subqueries-in-the-data-values--used-with-aggregates"></a>З. Связанные вложенные запросы в значениях данных, используемые с агрегатами  
  
```sql
SELECT Rb.b1, (SELECT RA.a1 FROM RA WHERE RB.b1 = RA.a1) FROM RB GROUP BY RB.b1;  
```  
  
### <a name="i-using-in-with-a-correlated-subquery"></a>И. Использование IN со связанным вложенным запросом  
 В следующем примере в коррелированном или повторяющемся вложенном запросе используется кодовое слово `IN`. Это запрос, зависящий от результатов выполнения другого запроса. Внутренний запрос повторно выполняется для каждой строки, которая может быть выбрана с помощью внешнего запроса. Этот запрос получает один экземпляр `EmployeeKey`, а также имя и фамилию каждого сотрудника, для которого значение `OrderQuantity` в таблице `FactResellerSales` составляет `5`, а соответствующие идентификационные номера в таблицах `DimEmployee` и `FactResellerSales` совпадают.  
  
```sql
SELECT DISTINCT dm.EmployeeKey, dm.FirstName, dm.LastName   
FROM DimEmployee AS dm   
WHERE 5 IN   
    (SELECT OrderQuantity  
    FROM FactResellerSales AS frs  
    WHERE dm.EmployeeKey = frs.EmployeeKey)  
ORDER BY EmployeeKey;  
```  
  
### <a name="j-using-exists-versus-in-with-a-subquery"></a>К. Использование EXISTS или IN с вложенным запросом  
 В приведенном ниже примере представлены семантически эквивалентные запросы для демонстрации различий в использовании ключевых слов `EXISTS` и `IN`. Вложенный запрос в каждом из примеров получает один экземпляр каждого названия продукта, подкатегория которого — `Road Bikes`. Значения `ProductSubcategoryKey` совпадают в таблицах `DimProduct` и `DimProductSubcategory`.  
  
```sql
SELECT DISTINCT EnglishProductName  
FROM DimProduct AS dp   
WHERE EXISTS  
    (SELECT *  
     FROM DimProductSubcategory AS dps   
     WHERE dp.ProductSubcategoryKey = dps.ProductSubcategoryKey  
           AND dps.EnglishProductSubcategoryName = 'Road Bikes')  
ORDER BY EnglishProductName;  
```  
  
 либо  
  
```sql
SELECT DISTINCT EnglishProductName  
FROM DimProduct AS dp   
WHERE dp.ProductSubcategoryKey IN  
    (SELECT ProductSubcategoryKey  
     FROM DimProductSubcategory   
     WHERE EnglishProductSubcategoryName = 'Road Bikes')  
ORDER BY EnglishProductName;  
```  
  
### <a name="k-using-multiple-correlated-subqueries"></a>Л. Использование нескольких связанных вложенных запросов  
 В данном примере с помощью двух коррелированных запросов осуществляется поиск сотрудников, продавших определенную продукцию.  
  
```sql
SELECT DISTINCT LastName, FirstName, e.EmployeeKey  
FROM DimEmployee e JOIN FactResellerSales s ON e.EmployeeKey = s.EmployeeKey  
WHERE ProductKey IN  
(SELECT ProductKey FROM DimProduct WHERE ProductSubcategoryKey IN  
(SELECT ProductSubcategoryKey FROM DimProductSubcategory   
 WHERE EnglishProductSubcategoryName LIKE '%Bikes'))  
ORDER BY LastName;  
```  
  
  
