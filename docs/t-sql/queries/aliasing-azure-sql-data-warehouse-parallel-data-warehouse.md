---
title: "Совмещение имен (хранилище данных Azure SQL, параллельное хранилище данных) | Документы Microsoft"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7b3a5c74-05cf-4385-8ee6-6176d003cb8a
caps.latest.revision: 11
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: edc81ce4377f490b482d920871ad361c98f961c5
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="aliasing-azure-sql-data-warehouse-parallel-data-warehouse"></a>Совмещение имен (хранилище данных Azure SQL, параллельное хранилище данных)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw_md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  За счет присвоения псевдонима временные подстановки коротких и легко запомнить строки вместо имени таблицы или столбца в [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] или [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] [!INCLUDE[DWsql](../../includes/dwsql-md.md)] запросов. Псевдонимы таблиц часто используются в запросах с СОЕДИНЕНИЯМИ, так как синтаксис JOIN требуются полные имена объектов, при ссылке на столбцы.  
  
 Псевдонимы должны быть соответствующие правила именования объектов отдельные слова. Дополнительные сведения см. в разделе «Правила именования объектов» в [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)]. Псевдонимы не могут содержать пробелы и не может быть заключено в одинарные или двойные кавычки.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
object_source [ AS ] alias  
```  
  
## <a name="arguments"></a>Аргументы  
 *object_source*  
 Имя исходной таблицы или столбца.  
  
 AS  
 Необязательный псевдоним местоимением. При работе с псевдонимами переменной диапазона, ключевое слово AS запрещен.  
  
 *псевдоним*  
 Имя нужного временную ссылку для таблицы или столбца. Можно использовать любое допустимое имя объекта. Дополнительные сведения см. в разделе «Правила именования объектов» в [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)].  
  
## <a name="examples-includesssdwincludessssdw-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] и[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 В следующем примере показано запроса, имеющего несколько соединений. В этом примере демонстрируются Совмещение имен таблиц и столбцов.  
  
-   Псевдонимы столбцов: Оба столбца и выражения, включающие столбцы в списке select используются псевдонимы в этом примере. `SalesTerritoryRegion AS SalesTR`демонстрируется простой псевдоним. `Sum(SalesAmountQuota) AS TotalSales`Демонстрирует  
  
-   Таблица псевдонимов: `dbo.DimSalesTerritory AS st` показывает создание `st` псевдоним для `dbo.DimSalesTerritory` таблицы.  
  
```  
-- Uses AdventureWorks  
  
SELECT LastName, SUM(SalesAmountQuota) AS TotalSales, SalesTerritoryRegion AS SalesTR,  
    RANK() OVER (PARTITION BY SalesTerritoryRegion ORDER BY SUM(SalesAmountQuota) DESC ) AS RankResult  
FROM dbo.DimEmployee AS e  
INNER JOIN dbo.FactSalesQuota AS sq ON e.EmployeeKey = sq.EmployeeKey  
INNER JOIN dbo.DimSalesTerritory AS st ON e.SalesTerritoryKey = st.SalesTerritoryKey  
WHERE SalesPersonFlag = 1 AND SalesTerritoryRegion != N'NA'  
GROUP BY LastName, SalesTerritoryRegion;  
  
```  
  
 Ключевое слово, можно исключить, как показано ниже, но часто включен для удобства чтения.  
  
```  
-- Uses AdventureWorks  
  
SELECT LastName, SUM(SalesAmountQuota) TotalSales, SalesTerritoryRegion SalesTR,  
RANK() OVER (PARTITION BY SalesTerritoryRegion ORDER BY SUM(SalesAmountQuota) DESC ) RankResult  
FROM dbo.DimEmployee e  
INNER JOIN dbo.FactSalesQuota sq ON e.EmployeeKey = sq.EmployeeKey  
INNER JOIN dbo.DimSalesTerritory st ON e.SalesTerritoryKey = st.SalesTerritoryKey  
WHERE SalesPersonFlag = 1 AND SalesTerritoryRegion != N'NA'  
GROUP BY LastName, SalesTerritoryRegion;  
```  
  
## <a name="see-also"></a>См. также:  
 [SELECT (Transact-SQL)](../../t-sql/queries/select-transact-sql.md)   
 [INSERT (Transact-SQL)](../../t-sql/statements/insert-transact-sql.md)   
 [UPDATE (Transact-SQL)](../../t-sql/queries/update-transact-sql.md)  
  
  
