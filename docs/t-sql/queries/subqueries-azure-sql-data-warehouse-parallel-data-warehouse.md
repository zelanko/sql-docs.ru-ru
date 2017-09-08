---
title: "Вложенные запросы (хранилище данных Azure SQL, параллельное хранилище данных) | Документы Microsoft"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0e8ebd60-1936-48c9-b2b9-e099c8269fcf
caps.latest.revision: 7
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 351d559bde6300d9f746d68a802ae0a61202f8b8
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="subqueries-azure-sql-data-warehouse-parallel-data-warehouse"></a>Вложенные запросы (хранилище данных Azure SQL, параллельное хранилище данных)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw_md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  В этом разделе приведены примеры использования вложенные запросы в [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] или [!INCLUDE[ssPDW](../../includes/sspdw-md.md)].  
  
 Инструкция SELECT, в разделе [ВЫБЕРИТЕ &#40; Transact-SQL &#41;](../../t-sql/queries/select-transact-sql.md)  
  
## <a name="contents"></a>Содержание  
  
-   [Основы](#Basics)  
  
-   [Примеры: Хранилище данных SQL и параллельные хранилища данных](#Examples)  
  
##  <a name="Basics"></a>Основы  
 Вложенный запрос  
 Вложенным запросом называется запрос, помещаемый в инструкцию SELECT, INSERT, UPDATE или DELETE или в другой вложенный запрос. Это также называется внутренним запросом или внутренней операцией выбора.  
  
 Внешний запрос  
 Инструкция, которая содержит вложенный запрос. Это также называется внешней операции выбора.  
  
 Коррелированные вложенные запросы  
 Вложенный запрос, который ссылается на таблицу во внешнем запросе.  
  
##  <a name="Examples"></a>Примеры: [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] и[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 В этом разделе приведены примеры вложенных запросов, поддерживаемые в [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] или [!INCLUDE[ssPDW](../../includes/sspdw-md.md)].  
  
### <a name="a-top-and-order-by-in-a-subquery"></a>A. TOP и ORDER BY во вложенном запросе  
  
```  
SELECT * FROM tblA  
WHERE col1 IN  
    (SELECT TOP 100 col1 FROM tblB ORDER BY col1);  
  
```  
  
### <a name="b-having-clause-with-a-correlated-subquery"></a>Б. HAVING предложения с коррелированные вложенные запросы  
  
```  
SELECT dm.EmployeeKey, dm.FirstName, dm.LastName   
FROM DimEmployee AS dm   
GROUP BY dm.EmployeeKey, dm.FirstName, dm.LastName  
HAVING 5000 <=   
(SELECT sum(OrderQuantity)  
FROM FactResellerSales AS frs  
WHERE dm.EmployeeKey = frs.EmployeeKey)  
ORDER BY EmployeeKey;  
  
```  
  
### <a name="c-correlated-subqueries-with-analytics"></a>В. Коррелированные вложенные запросы с помощью аналитики  
  
```  
SELECT * FROM ReplA AS A   
WHERE A.ID IN   
    (SELECT sum(B.ID2) OVER() FROM ReplB AS B WHERE A.ID2 = B.ID);  
```  
  
### <a name="d-correlated-union-statements-in-a-subquery"></a>Г. Коррелированные инструкции union во вложенном запросе  
  
```  
SELECT * FROM RA   
WHERE EXISTS   
    (SELECT 1 FROM RB WHERE RB.b1 = RA.a1   
     UNION ALL SELECT 1 FROM RC);  
```  
  
### <a name="e-join-predicates-in-a-subquery"></a>Д. Предикаты соединения во вложенных запросах  
  
```  
SELECT * FROM RA INNER JOIN RB   
    ON RA.a1 = (SELECT COUNT(*) FROM RC);  
```  
  
### <a name="f-correlated-join-predicates-in-a-subquery"></a>Е. Коррелированные предикаты во вложенном запросе  
  
```  
SELECT * FROM RA   
    WHERE RA.a2 IN   
    (SELECT 1 FROM RB INNER JOIN RC ON RA.a1=RB.b1+RC.c1);  
```  
  
### <a name="g-correlated-subselects-as-data-sources"></a>Ж. Коррелированные подзапросы выборки в качестве источников данных  
  
```  
SELECT * FROM RA   
    WHERE 3 = (SELECT COUNT(*)   
        FROM (SELECT b1 FROM RB WHERE RB.b1 = RA.a1) X);  
```  
  
### <a name="h-correlated-subqueries-in-the-data-values--used-with-aggregates"></a>З. Коррелированные вложенные запросы в значения данных, используемые с статистическими функциями  
  
```  
SELECT Rb.b1, (SELECT RA.a1 FROM RA WHERE RB.b1 = RA.a1) FROM RB GROUP BY RB.b1;  
```  
  
### <a name="i-using-in-with-a-correlated-subquery"></a>И. С помощью вход с помощью коррелированные вложенные запросы  
 В следующем примере в коррелированном или повторяющемся вложенном запросе используется кодовое слово `IN`. Это запрос, зависящий от результатов выполнения другого запроса. Внутренний запрос выполняется неоднократно, один раз для каждой строки, которые могут быть выбраны внешним запросом. Этот запрос извлекает один экземпляр `EmployeeKey` , а также имя и фамилия каждого сотрудника, для которого `OrderQuantity` в `FactResellerSales` таблица является `5` и для которого совпадают идентификационные номера сотрудника в `DimEmployee` и `FactResellerSales` таблиц.  
  
```  
SELECT DISTINCT dm.EmployeeKey, dm.FirstName, dm.LastName   
FROM DimEmployee AS dm   
WHERE 5 IN   
    (SELECT OrderQuantity  
    FROM FactResellerSales AS frs  
    WHERE dm.EmployeeKey = frs.EmployeeKey)  
ORDER BY EmployeeKey;  
```  
  
### <a name="j-using-exists-versus-in-with-a-subquery"></a>К. Использование ключевого слова EXISTS и in с вложенным запросом  
 В следующем примере показано запросы, которые семантически эквивалентны проиллюстрировать различие между использованием `EXISTS` ключевое слово и `IN` ключевое слово. Оба являются примерами вложенный запрос, извлекающие по одному экземпляру продукции каждого наименования, для которой является «Подкатегория продукта» `Road Bikes`. `ProductSubcategoryKey`соответствует между `DimProduct` и `DimProductSubcategory` таблицы.  
  
```  
SELECT DISTINCT EnglishProductName  
FROM DimProduct AS dp   
WHERE EXISTS  
    (SELECT *  
     FROM DimProductSubcategory AS dps   
     WHERE dp.ProductSubcategoryKey = dps.ProductSubcategoryKey  
           AND dps.EnglishProductSubcategoryName = 'Road Bikes')  
ORDER BY EnglishProductName;  
```  
  
 Или  
  
```  
SELECT DISTINCT EnglishProductName  
FROM DimProduct AS dp   
WHERE dp.ProductSubcategoryKey IN  
    (SELECT ProductSubcategoryKey  
     FROM DimProductSubcategory   
     WHERE EnglishProductSubcategoryName = 'Road Bikes')  
ORDER BY EnglishProductName;  
```  
  
### <a name="k-using-multiple-correlated-subqueries"></a>Л. С помощью нескольких коррелированные вложенные запросы  
 В данном примере с помощью двух коррелированных запросов осуществляется поиск сотрудников, продавших определенную продукцию.  
  
```  
SELECT DISTINCT LastName, FirstName, e.EmployeeKey  
FROM DimEmployee e JOIN FactResellerSales s ON e.EmployeeKey = s.EmployeeKey  
WHERE ProductKey IN  
(SELECT ProductKey FROM DimProduct WHERE ProductSubcategoryKey IN  
(SELECT ProductSubcategoryKey FROM DimProductSubcategory   
 WHERE EnglishProductSubcategoryName LIKE '%Bikes'))  
ORDER BY LastName  
;  
  
```  
  
  
